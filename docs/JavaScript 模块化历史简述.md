# JavaScript 模块化

模块化在JavaScript中是一个现代化的概念。这篇文章我将快速回顾并总结模块化在JavaScript中是如何演进的。

## Script Tags 与 闭包

最初，JavaScript是嵌入在HTML 的&lt;script&gt;标签中。即便将代码封装在不同的script文件中， 所有文件依旧共享`global scope`。

任何在这些js文件或script标签内定义的变量将被挂载到global `window` 对象，其它不相关的代码可能会因此产生冲突。

随着web应用体积与复杂性的快速增长， 作用域的概念与全局作用域的危害被人们所熟知。 随即，立刻执行函数(Immediately-invoking function expressions)被广泛使用。因为JavaScript中的函数会创建自己的作用域，这就意味着 `var` 变量的挂载会被限定在IIFE中。即便变量声明会提升（hoisted）到作用域的顶部。

Several flavors of IIFE can be found in the next example snippet. The code in each IIFE is isolated and can only escape onto the global context via explicit statements such as window.fromIIFE = true.

```js
(function() {
  console.log('IIFE using parenthesis')
})()

~function() {
  console.log('IIFE using a bitwise operator')
}()

void function() {
  console.log('IIFE using the void operator')
}()
```