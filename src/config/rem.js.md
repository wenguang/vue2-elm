
1、自执行函数
2、监听window横竖屏、resize、document的DOMContentLoaded，响应recalc函数，重新确定fontSize的大小

```
(function(doc, win) {
    // documentElement 是整个节点树的根节点root
    var docEl = doc.documentElement,
        // window的resize事件、横竖屏事件
        resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
        recalc = function() {
            var clientWidth = docEl.clientWidth;
            if (!clientWidth) return;
            docEl.style.fontSize = 20 * (clientWidth / 320) + 'px';
        };
    if (!doc.addEventListener) return;
    // 监听window横竖屏、resize、document的DOMContentLoaded
    // 响应recalc函数，重新确定fontSize的大小
    win.addEventListener(resizeEvt, recalc, false);
    doc.addEventListener('DOMContentLoaded', recalc, false);
})(document, window);
```

