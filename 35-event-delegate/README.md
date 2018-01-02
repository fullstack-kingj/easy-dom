# 事件委托

## 什么是事件委托

当为大量的 HTML 元素注册相同事件，并且事件的句柄逻辑完全相同时，会造成页面速度下降。不过，事件流允许在这些 HTML 元素的共同父级元素注册事件。这种方式被称为事件委托。

```html
<div id="parent" class="button-group">
    <button class="button">按钮</button>
    <button class="button">按钮</button>
    <button class="button">按钮</button>
</div>
<script>
    var btn = document.getElementById('parent');
    btn.addEventListener('click', function(event){
        if (event.target.nodeName === 'BUTTON'){
            alert('我是一个链接.')
        }
    });
</script>
```

## 事件委托的优势

- 适用于新创建的元素

如果向 DOM 树结构中添加新的元素，那么不需要再向这个新元素注册相同事件。因为注册事件已经委托给了该元素的祖先元素完成。

- 简化逻辑代码

这种方式只需要祖先元素一次注册事件，而不需要分别为大量元素注册事件。使得逻辑代码的性能提高，也更加容易维护。
