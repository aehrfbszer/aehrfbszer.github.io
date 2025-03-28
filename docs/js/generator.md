之前在看到 golang 丑陋的 iterator 语法后，突然明白 js 的 generator/yield 函数到底是什么了

```
function* generateSequence() {
  yield 1;
  yield 2;
  return 3;
}

let generator = generateSequence();

let one = generator.next();

alert(JSON.stringify(one)); // {value: 1, done: false}
```

### generator函数，就是返回生成器函数的函数。
- 如上代码所示，先定义了一个 generator 函数 generateSequence。
- 然后执行它，将返回值赋值给generator。
- 现在generator内部是一个状态机，状态机的调用可以用for of去迭代，或者调用next去手动迭代。其内部的状态机，就是根据yield关键字作为分割线，每个yield会分割出一部分代码块，这样generator内部就是分成了多个小的函数，每次调用next方法，内部的小函数依次执行。
- 调用next时，可以传参数进去，参数的位置，就在上一部分分割代码块的位置。看下图就能懂了。


![图](../../pic/zh.javascript.info_generators%20(2).png)


网上的教程简直不是人话，我没想明白，怎么没有人解释清楚这么简单的东西。是不在乎吗，不过这个yield函数也确实没看见有人用