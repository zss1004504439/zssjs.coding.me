---
title: '实现一个可以拖拽的DIV'
date: 2020-10-15 14:57:45
tags: []
published: true
hideInList: false
feature: 
isTop: false
---
```js
微信公众号：世界上有意思的事

var DragDrop = function(){
  var dragging = null; 
  function handleEvent(event){
    
    //获取事件和目标
    event = EventUtil.getEvent(event);
    var target = EventUtil.getTarget(event);
    
    //确定事件类型 
    switch(event.type){
      case "mousedown":
        if (target.className.indexOf("draggable") > -1){
          dragging = target; 
        }
        break;
      case "mousemove":
        if (dragging !== null){ 
          //指定位置
          dragging.style.left = event.clientX + "px";
          dragging.style.top = event.clientY + "px";
        }
        break;
      case "mouseup": 
        dragging = null;
        break; 
    }
  };
  //公共接口 
  return {
    enable: function(){
      EventUtil.addHandler(document, "mousedown", handleEvent);
      EventUtil.addHandler(document, "mousemove", handleEvent);
      EventUtil.addHandler(document, "mouseup", handleEvent);
    },
    disable: function(){
      EventUtil.removeHandler(document, "mousedown", handleEvent);
      EventUtil.removeHandler(document, "mousemove", handleEvent);
      EventUtil.removeHandler(document, "mouseup", handleEvent);
    }
  }
}();

```

1.DragDrop 对象封装了拖放的所有基本功能。这是一个单例对象，并使用了模块模式来隐藏某些实 现细节。dragging 变量起初是 null，将会存放被拖动的元素，所以当该变量不为 null 时，就知道正 在拖动某个东西。handleEvent()函数处理拖放功能中的所有的三个鼠标事件。它首先获取 event 对 象和事件目标的引用。之后，用一个 switch 语句确定要触发哪个事件样式。当 mousedown 事件发生 时，会检查 target 的 class 是否包含"draggable"类，如果是，那么将 target 存放到 dragging 中。这个技巧可以很方便地通过标记语言而非 JavaScript 脚本来确定可拖动的元素。


2.handleEvent()的 mousemove 情况和前面的代码一样，不过要检查 dragging 是否为 null。当 它不是 null，就知道 dragging 就是要拖动的元素，这样就会把它放到恰当的位置上。mouseup 情况 就仅仅是将 dragging 重置为 null，让 mousemove 事件中的判断失效。


3.DragDrop 还有两个公共方法:enable()和 disable()，它们只是相应添加和删除所有的事件处 理程序。这两个函数提供了额外的对拖放功能的控制手段。


4.要使用 DragDrop 对象，只要在页面上包含这些代码并调用 enable()。拖放会自动针对所有包含 "draggable"类的元素启用，如下例所示:
```<div class="draggable" style="position:absolute; background:red"> </div>```
复制代码注意为了元素能被拖放，它必须是绝对定位的。

作者：何时夕
链接：https://juejin.im/post/6844904121380667399
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。














```html
<div id="xxx"></div>
```
```js
var dragging = false
var position = null

xxx.addEventListener('mousedown',function(e){
  dragging = true
  position = [e.clientX, e.clientY]
})


document.addEventListener('mousemove', function(e){
  if(dragging === false) return null
  console.log('hi')
  const x = e.clientX
  const y = e.clientY
  const deltaX = x - position[0]
  const deltaY = y - position[1]
  const left = parseInt(xxx.style.left || 0)
  const top = parseInt(xxx.style.top || 0)
  xxx.style.left = left + deltaX + 'px'
  xxx.style.top = top + deltaY + 'px'
  position = [x, y]
})
document.addEventListener('mouseup', function(e){
  dragging = false
})

```