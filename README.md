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
