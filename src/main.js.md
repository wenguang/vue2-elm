
##### fastclick库及使用
在移动浏览器中，从点击屏幕到真正的click事件响应会延迟300毫秒，因为系统要在300毫秒的间隔内检测用户是否有再次的点击来判断是否为双击缩放或双击滚动等行为。但有些应用页面上不用考虑双击行为，这个300毫秒的延迟就有些影响用户体验了。

基本原理：FastClick的实现原理是在检测到touchend事件的时候，会通过DOM自定义事件立即出发模拟一个click事件，并把浏览器在300ms之后真正的click事件阻止掉。

```
// 在document的DOMContentLoaded的函数中给document.body附上fastclick
if ('addEventListener' in document) {
    document.addEventListener('DOMContentLoaded', function() {
        FastClick.attach(document.body);
    }, false);
}
```

参考：
[fastclick 解决移动端click事件300ms延迟](https://www.jianshu.com/p/16d3e4f9b2a9)
[FastClick原理浅析](https://www.jianshu.com/p/05b142d84780)


#### 让我迷糊的vue-router的两种模式及应用场景
mode:'hash'、mode:'history'

参考：
[vue-router的两种模式的区别](https://juejin.im/post/5a61908c6fb9a01c9064f20a)
[请问vue-router两种模式hash,history分别在什么情况下使用？](https://github.com/bailicangdu/vue2-elm/issues/201)


##### 路由的严格模式
```
strict: process.env.NODE_ENV !== 'production'
```
在严格模式下，无论何时发生了状态变更且不是由 mutation 函数引起的，将会抛出错误。这能保证所有的状态变更都能被调试工具跟踪到。不要在发布环境下启用严格模式！严格模式会深度监测状态树来检测不合规的状态变更——请确保在发布环境下关闭严格模式，以避免性能损失。


##### 路由的滚动行为 scrollBehavior
使用前端路由，当切换到新路由时，想要页面滚到顶部，或者是保持原先的滚动位置，就像重新加载页面那样。 vue-router 能做到，而且更好，它让你可以自定义路由切换时页面如何滚动。

scrollBehavior对象信息，长这样：{ x: number, y: number }
scrollBehavior对象仅在支持 history.pushState 的浏览器中可用
```
scrollBehavior (to, from, savedPosition) {
    if (savedPosition) {
        return savedPosition
    } else {
        // [keep-alive：组件级缓存](https://juejin.im/post/5b407c2a6fb9a04fa91bcf0d)
        if (from.meta.keepAlive) {
            from.meta.savedPosition = document.body.scrollTop;
        }
        return { x: 0, y: to.meta.savedPosition || 0 }
    }
}
```
如果你要模拟“滚动到锚点”的行为：
```
scrollBehavior (to, from, savedPosition) {
  if (to.hash) {
    return {
      selector: to.hash
    }
  }
}
```


##### vue组件缓存位置 from.meta.keepAlive from.meta.savedPosition
[keep-alive：组件级缓存](https://juejin.im/post/5b407c2a6fb9a04fa91bcf0d)




