设置 class 属性与获取 class 属性方式类似，都是通过 Element 对象提供的 className 属性和 classList 属性实现。

## Element 对象的 className 属性Element 对象提供的 className 属性既可以实现获取，也可以实现设置。其设置的语法结构如下:

```javascript
elementNodeReference.className = cName;
```

上述语法结构中，作为值的 cName 是一个字符串变量。表示当前元素的class属性的值，可以是由空格分隔的多个class属性值。我们可以通过以下示例代码，学习如何通过 className 属性设置:

```javascript
var btn = document.getElementById('btn');var className = btn.className;className += ' animate';btn.className = className;
```

## Element 对象的 classList 属性

Element 对象提供的 classList 属性与 className 属性类似，既可以实现获取，也可以实现设置。

但 classList 属性自身是只读属性，换句话讲，我们并不能通过 classList 属性进行设置。而是通过以下方法实现:

| 方法名称 | 描述 |
| --- | --- |
| add() | 添加指定的类值。如果这些类已经存在于元素的属性中，那么它们将被忽略。|
| remove() | 删除指定的类值。|
| item() | 按集合中的索引返回类值。|
| toggle() | 切换指定的类值。 |
| contains() | 检查元素的类属性中是否存在指定的类值。|

我们可以通过以下示例代码，学习上述方法的使用:

```javascript
var btn = document.getElementById('btn');var classList = btn.classList;// 添加 .animate 样式classList.add('animate');// 删除 .animate 样式classList.remove('animate');// 如果 .animate 存在，则删除；如果 .animate 不存在，则添加classList.toggle('animate');// 判断是否存在 .animate 样式console.log(classList.contains('animate'));
```

