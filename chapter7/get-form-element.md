## 获取表单元素

获取表单元素的方式，大体可以分为以下几种方式:

- Document 对象提供的定位页面元素的一系列方法
- Document 对象提供了 forms 属性
- Document 对象通过表单的 name 属性值获取指定表单元素

接下来，我们将分别介绍这几种方式的使用。

### 定位页面元素的方法

Document 对象提供了如下几种定位页面元素的方法:

- getElementById() 方法
- getElementsByName() 方法
- getElementsByTagName() 方法
- getElementsByClassName() 方法
- querySelector() 方法
- querySelectorAll() 方法

> 以上几种方法的具体使用，请参考第二章节的《定位页面元素》一节内容。

上述几种方法的使用，我们可以通过如下示例代码进行学习:

```html
<form id="myform" name="myform" class="login" action="#"></form>
<script>
    var formId = document.getElementById('myform');
    var formName = document.getElementsByName('myform');
    var formElement = document.getElementsByTagName('form')[0];
    var formClass = document.getElementsByClassName('login')[0];
    
    var formId2 = document.querySelector('#myform');
    var formElement2 = document.querySelectorAll('form')[0];
</script>
```

### Document 对象的 forms 属性

Document 对象提供了 forms 属性，用于获取当前 HTML 页面中所有表单的集合。例如如下示例代码:

```html
<form id="myform" name="myform" class="login" action="#"></form>
<script>
    var forms = document.forms;
</script>
```

该属性返回 HTMLCollection 对象，