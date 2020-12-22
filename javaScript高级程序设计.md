### 延迟执行脚本

HTML4.01 为 `<script>`元素定义一个叫defer的属性，这个属性表示脚本在执行的时候不会改变页面的结构，也就是脚本会被延迟到整个页面都解析完毕后再运行。相当于告诉浏览器立即下载脚本吗，但是会延迟执行。

当在XHTML中，指定defer属性应该写成defer="defer"。

### 异步执行脚本
HTML5为`<script>`元素定义async属性，和defer类似，都会告诉浏览器立即开始下载，和defer不同的是，标记的脚本不保证能按照他们出现的次序执行：

```js
<!Document html>
<html>
  <head>
    <title>Example HTML Page</title>
    <script async src="example1.js"></script>
    <script async src="example2.js"></script>
  </head>
  <body>
    < !--- 内容 --->
  </body>
</html>
```

上述代码，第一个脚本可能优先第二个脚本执行，重点在于他们之间没有依赖关系。给脚本添加async属性的目的就是告诉浏览器不必等脚本下载和执行完成后加载页面，同样也不必等到异步脚本下载和执行后再加载其他脚本，所以，异步脚本不应该在加载期间修改DOM。

对于XHTML文档，指定async属性应该写成async="async"

### 动态加载脚本
除了`<script>`标签，还有其他方式可以加载脚本，因为javaScript可以使用DOM API，所以向DOM中动态添加script元素同样可以加载执行的脚本。只要创建一个script元素并将其添加到DOM：

```js
let script = document.createElement('script');
script.src = 'gibberish.js';
document.head.appendChild(script);
```

像上述这种情况属于异步方式加载，相当于添加了async属性，因为不是所有的浏览器都支持async属性，如果要统一动态脚本加载行为，将其设置为同步加载

```js
let script = document.createElement('script');
script.src = 'gibberish.js';
script.async = false;
document.head.appendChild(script);
```

上述这种方式会影响脚本在资源队列中的优先级，解决方法就是在文档头部声明他们：

```js
<link rel="preload" href="gibberish.js">
```

###  XHTML中的变化
#### 1、什么是XHTML
可扩展超文本标记语言是将HTML作为XML的应用重新包装的结果，与HTML不同，在XHTML中使用javaScript必须制定type属性切值为text/javaScript，
