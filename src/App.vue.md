
#### transition、keep-alive、router-view结合使用
这样配置路由的路由元信息之后，a路由的$router.meta.keepAlive 便为 true ，而b路由则为 false 。所以为 true 的将被包裹在keep-alive 中，为 false 的则在外层。
```
<!-- template -->
// 过滤模式：https://cn.vuejs.org/v2/guide/transitions.html#%E8%BF%87%E6%B8%A1%E6%A8%A1%E5%BC%8F
<transition name="router-fade" mode="out-in">
    <keep-alive>
        <router-view v-if="$route.meta.keepAlive"></router-view>
    </keep-alive>
</transition>
<transition name="router-fade" mode="out-in">
    <router-view v-if="!$route.meta.keepAlive"></router-view>
</transition>

//router配置
new Router({
    routes: [
        {
            name: 'a',
            path: '/a',
            component: A,
            meta: {
                keepAlive: true
            }
        },
        {
            name: 'b',
            path: '/b',
            component: B
        }
    ]
})
```


[keep-alive：组件级缓存](https://juejin.im/post/5b407c2a6fb9a04fa91bcf0d)
[keep-alive的深入理解与使用(配合router-view缓存整个路由页面)](https://segmentfault.com/a/1190000010546663)

[官方 进入/离开 & 列表过渡](https://cn.vuejs.org/v2/guide/transitions.html)
[官方 状态过渡](https://cn.vuejs.org/v2/guide/transitioning-state.html)