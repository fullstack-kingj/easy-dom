Node 对象提供了 textContent 属性实现获取或设置 HTML 页面中指定元素的文本内容。

## 获取文本内容

textContent 属性表示 HTML 页面指定节点及其后代节点的文本内容。其语法格式如下:

```javascript
var text = element.textContent;
```

在上述语法结构中，返回值 text 表示 element 节点及其后代节点的文本内容。

需要说明的是，在上述语法结构中，调用 textContent 属性的 element 表示元素节点。元素节点本身也是一个元素。

> **值得注意的是:** 如果指定节点是 Document 文档节点的话，textContent 返回 null。

我们可以通过如下代码示例，测试如何通过 textContent 属性获取指定节点的文本内容:

```javascript
var pElement = document.getElementById('p');console.log(pElement.textContent);
```

> **值得注意的是:** 如果指定节点的后代节点也包含文本内容的话，那该节点调用 textContent 属性时，则会返回该节点及其所有后代节点的文本内容。
> 
> 如下 HTML 页面结构:
> 
> ```html
> <p id="content">这是一个<span>段落</span>内容。</p>
> ```
> 
> 如果我们通过上述 `<p>` 元素调用 textContent 属性的话，得到的结果并不是如下结果:
> 
> ```
> 这是一个内容。
> ```
> 
> 而是如下结果:
> 
> ```
> 这是一个段落内容。
> ```

## 设置文本内容通过 textContent 属性不仅可以获取 HTML 页面中指定节点及其后代节点的文本内容，还可以设置指定节点的文本内容。其语法结构如下:

```javascript
element.textContent = "this is some sample text";
```

> **值得注意的是:** 在节点上设置 textContent 属性的话，会删除它的所有子节点，并替换为一个具有给定值的文本节点。

我们可以通过如下代码示例，测试如何通过 textContent 属性设置指定节点的文本内容:

```javascript
var btn = document.getElementById('btn');btn.textContent = 'A New Button';
```

## innerText 属性

IE 引入了 node.innerText 属性，意图类似 textContent。但有以下区别：- textContent 会获取所有元素的内容，包括 `<script>` 和 `<style>` 元素，然而 innerText 不会。- innerText 意识到样式，并且不会返回隐藏元素的文本，而 textContent 会。- 由于 innerText 受 CSS 样式的影响，它会触发重排（reflow），但 textContent 不会。- 在 IE (小于等于 IE11 的版本) 中对 innerText 进行修改，不仅会移除当前元素的子节点，而且还会永久性地破坏所有后代文本节点。

关于 innerText 属性的具体用法请参考 [MSDN社区的相关说明](https://msdn.microsoft.com/en-us/library/ms533899(v=vs.85).aspx)。

## 浏览器兼容问题解决方案在实际开发中，我们需要尽量满足所有浏览器对文本内容操作的需求。所以，我们可以使用如下代码解决浏览器之间的兼容问题:

```javascript
function text(elem, text){    if(text){        elem.textContent ? elem.textContent = text : elem.innerText = text;    }else{        if(elem.textContent){            // 表示其他浏览器            return elem.textContent;        }else{            // 表示 IE 浏览器            return elem.innerText;        }    }}
```

