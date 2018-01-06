所谓事件，就是浏览器告知 JavaScript 程序用户的行为。例如用户点击了 HTML 页面中的某个按钮，或者用户输入用户名或密码等操作。


```html
<div class="button-group">
```

根据上述示例代码，具体执行流程如下:

![](images/01.png)

## 事件类型

| --- | --- |
| keydown | 用户按下一个按键。|
| keypress | 用户按下并释放一个按键。如果该按键不是修饰键时，触发该事件。|
| keyup | 用户释放一个按键。|

> **值得注意的是:** 如果是切换指示灯的状态，如Caps Lock键，Num Lock键和Scroll Lock键。这些按键仅发送 keydown 事件和 keyup 事件。

| 事件名称 | 描述 |
| --- | --- |
| mousedown | 用户按下鼠标按键。|
| mouseup | 用户释放鼠标按钮。|
| mouseover | 用户移动鼠标到指定元素上。|
| mousemove | 用户鼠标移动。|
| mouseout | 用户将鼠标从指定元素上移除。|

## 独立于设备的输入事件

| 事件名称 | 描述 |
| --- | --- |
| click | 用户点击一下。|
| dblclick | 用户连续点击两下。|
| contextmenu | 用户点击鼠标右键打开上下文菜单。|

## 状态变化的相关事件

| 事件名称 | 描述 |
| --- | --- |
| load | 表示 HTML 页面或图片加载完毕。|
| unload | 表示离开或关闭 HTML 页面。|
| resize | 表示浏览器窗口被重新调整的大小。|
| scroll | 表示 HTML 页面滚动。|
