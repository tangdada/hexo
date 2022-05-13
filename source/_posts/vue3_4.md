---
title: 四、组件化
---

### 组件的实现原理
当页面模块变得越来越大，这时我们就需要组件化的能力。
```js
function patch(n1, n2, container, anchor) {
    if (n1 && n1.type !== n2.type) {
        unmount(n1)
        n1 = null
    }

    const { type } = n2

    if (typeof type === 'string') {
        // 普通标签元素
    } else if (type === Text) {
        // 文本
    } else if (type === Fragment) {
        // 片段
    } else if (type === 'object') {
        if (!n1) {
            // 挂载组件
            mountComponent(n2, container, anchor)
        } else {
            // 更新组件
            patchComponent(n1, n2, anchor)
        }
    }
}
```

#### 组件实例
通过缓存组件实例，防止每次都重新渲染
```js
function mountComponet(vnode, container, anchor) {
    const instance = {
        state,
        isMounted: false,
        subTree: null
    }

    if (!instance.isMounted) {
        patch(null, subTree, container, anchor)
    } else {
        patch(instance.subTree, subTree, container, anchor)
    }
}
```

#### setup
组件的setup函数时Vue.js 3 的新增组件选项。主要用于配合composition API，它用于建立组合逻辑、创建响应式数据、创建通用函数、注册生命周期钩子等场景。在组件的整个生命周期中，setup只会被执行一次。

setup的返回值有两种：
1）返回函数，作为render 函数，不能和template模板共用。
2）返回对象，该对象暴露给template模板使用。
```js
const Comp = {
    props: {
        foo: string
    }
    setup(props, setupContext) {
        props.foo
        const { slots, emit, attrs, expose } = setupContext
    }
}
```
slots: 组件接受到的插槽
emit：一个函数，用来发射事件
attrs：那些没有显式声明的props属性
expose：一个函数，著书时该API还在设计讨论中

#### emit
本质上就是根据事件名称去props数据对象中寻找对应事件处理函数并执行。
```js
function emit(event, ...payload) {
    const eventName = `on${event[0].toUpperCase() + event.slice(1)}`
    const handler = instance.props[eventName]
    if (handler) {
        handler(...payload)
    } else {
        console.error('事件不存在')
    }
}
```

#### slot插槽的工作原理
顾名思义，组件的插槽指组件会预留一个槽位，该槽位具体要渲染的内容由用户插入。

插槽定义：
```js
<template>
    <header><slot name="header" /></header>
    <div>
        <slot name="body" />
    </div>
    <footer><slot name="footer" /></footer>
</template>
```

使用组件时：
```js
<MyComponent>
    <template #header>
        <h1>标题</h1>
    </template>
    <template #body>
        <section>内容</section>
    </template>
    <template #footer>
        <p>底部</p>
    </template>
</MyComponent>
```
组件模板中的插槽内容会被编译成插槽函数，返回值就是具体的插槽内容。

### 异步组件 & 函数式组件
#### 异步组件
其实用户可以自行实现异步组件：
```js
<template>
    <CompA />
    <component :is="asyncComp" />
</template>

<script>
import { shallowRef } from 'vue'
import CompA from 'CompA.vue'

export default {
    components: { CompA },
    setup() {
        const asyncComp = shallowRef(null)

        // 异步加载 CompB 组件
        import('CompB.vue').then(CompB => asyncComp.value = CompB)
        return {
            asyncComp
        }
    }
}
</script>
```
但是出于加载失败、占位内容、Loading、重试等考虑，Vue.js 3 封装了 defineAsyncComponent来异步加载组件，它是一个高阶组件，它返回值是一个包装组件。

#### 函数式组件
函数式组件本质上就是一个普通函数，返回值是虚拟DOM。
函数式组件本身没有自身状态，但它仍然可以接收由外部传入的props：
```js
function MyFuncComp(props) {
    return { type: 'h1', children: props.tile }
}
// 定义 props
MyFuncComp.props = {
    title: String
}
```
在有状态组件的基础上，就可以复用mountComponent函数了：
```js
function mountComponent(vnode, container, anchor) {
    // 检查是否是函数式组件
    const isFunctional = typeof vnode.type === 'function'

    let componentOptions = vnode.type
    if (isFunctional) {
        // 如果是函数式组件，则将 vnode.type 作为渲染函数
        componentOptions = {
            render: vnode.type,
            props: vnode.type.props
        }
    }
}
```

### 内建组件 & 模块
Vue.js 中有几个非常重要的内建组件，例如 KeepAlive、Teleport、Transition 组件等，它们都需要渲染器级别的底层支持。理解他们的原理有助于更好的使用他们。

#### KeepAlive
KeepAlive 借鉴于HTTP协议，HTTP中KeepAlive 可以避免连接频繁的销毁、创建。与HTTP中相似，Vue.js 内建的 KeepAlive 可以避免一个组件被频繁的销毁、创建。\
其实 KeepAlive 的本质就是缓存管理，再加上特殊的挂载/卸载逻辑。
```js
<template>
    <Tab v-if="currentTab === 1"></Tab>
    <Tab v-if="currentTab === 2"></Tab>
    <Tab v-if="currentTab === 3"></Tab>
</template>
```
KeepAlive 使用：
```js
<template>
    <KeepAlive>
        <Tab v-if="currentTab === 1"></Tab>
        <Tab v-if="currentTab === 2"></Tab>
        <Tab v-if="currentTab === 3"></Tab>
    </KeepAlive>
</template>
```
使用 KeepAlive 包裹的组件，在激活和失活时会分别触发 activated、deactivated 两个生命周期。

_deactivated 失活的本质是将组件所渲染后的内容移动到隐藏容器中，而activated 激活的本质是将组件的渲染后内容从隐藏容器中搬运回来。这其中有两个关键点：渲染后的内容、移动。\
KeepAlive 还提供了 include、exclude 来更细粒度的控制缓存。

当缓存容量满时，Vue.js 采用“最新一次访问”的策略。

#### Teleport
Teleport 是 Vue.js 3 新增的内建组件。\
通常情况，虚拟DOM的层级关系与真实渲染出来的真实DOM一致：
```js
<template>
    <div id="parent-box">
        <OverLay />
    </div>
</template>
```
其中 Overlay 渲染的DOM一定在 `id="parent-box"` 的 div 下。无法跨越层级。\
假如有这样一个场景，将无法实现：Overlay 是一个蒙层，我们希望它遮罩在所有元素之上，但此时无论我们 z-index 设置多大都无法实现。

利用 Teleport 重新实现 Overlay：
```js
<template>
    <Teleport to="body">
        <div class="overlay"></div>
    </Teleport>
</template>

<style scoped>
.overlay {
    z-index: 9999;
}
</style>
```
该组件会直接把它的插槽内容渲染到 body 下。

#### Tansition
- 当DOM元素挂载时，将动效附加到该DOM元素上。
- 当DOM元素卸载时，不要立即卸载，先等到DOM元素的动画执行完成后再卸载。
