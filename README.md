# knowledge-review
一、解决组件化，模块化的问题：

二、日常工作的内容：

1、共用函数的提取

  js形式：
    弹框
    下拉框
    
  css公共样式：
    表格，按钮，输入框，标题栏，键值对
    
  模块化：业务模块化
         代码模块化
         
2、单元测试、自动化部署、自动化打包

三、当前使用较多的：

    generator函数与promise对象
    
    除了for...of循环以外，扩展运算符（...）、解构赋值和Array.from方法内部调用的，都是遍历器接口。这意味着，它们都可以将 Generator 函数返回的 Iterator 对象，作为参数。
    
    例子：
    function* numbers () {
        yield 1
        yield 2
        return 3
        yield 4
    }

      // 扩展运算符
      [...numbers()] // [1, 2]

      // Array.from 方法
      Array.from(numbers()) // [1, 2]

      // 解构赋值
      let [x, y] = numbers();
      x // 1
      y // 2

      // for...of 循环
      for (let n of numbers()) {
        console.log(n)
      }
      // 1
      // 2
    
    
      generator  yield*遍历完全二叉树
      
      // 下面是二叉树的构造函数，
      // 三个参数分别是左树、当前节点和右树
      function Tree(left, label, right) {
        this.left = left;
        this.label = label;
        this.right = right;
      }

      // 下面是中序（inorder）遍历函数。
      // 由于返回的是一个遍历器，所以要用generator函数。
      // 函数体内采用递归算法，所以左树和右树要用yield*遍历
      function* inorder(t) {
        if (t) {
          yield* inorder(t.left);
          yield t.label;
          yield* inorder(t.right);
        }
      }

      // 下面生成二叉树
      function make(array) {
        // 判断是否为叶节点
        if (array.length == 1) return new Tree(null, array[0], null);
        return new Tree(make(array[0]), array[1], make(array[2]));
      }
      let tree = make([[['a'], 'b', ['c']], 'd', [['e'], 'f', ['g']]]);

      // 遍历二叉树
      var result = [];
      for (let node of inorder(tree)) {
        result.push(node);
      }

      result
      // ['a', 'b', 'c', 'd', 'e', 'f', 'g']

四、常见算法

    1、斐波那契数列
    function* fibonacci() {
        let [prev, curr] = [0, 1];
        for (;;) {
            yield curr;
            [prev, curr] = [curr, prev + curr];
        }
    }

    for (let n of fibonacci()) {
        if (n > 1000) break;
        console.log(n);
    }
