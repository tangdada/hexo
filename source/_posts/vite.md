---
title: Vite
---

### 概述
Vite是新一代的前端构建工具，类似于 Webpack+ Webpack-dev-server。\
在开发环境利用浏览器的 ESM，完全跳过打包环节，按需加载；生产环境则利用 Rollup 打包。

特点：
- 快速冷启动，`No Bundle` + esbuild
- 模块热更新，基于 ESM 的 HMR，同时利用浏览器缓存
- 按需加载，基于 ESM

#### ESM
ESM 是 JavaScript 提出的官方标准化模块系统，作为 ECMA 标准，已经有绝大部分浏览器支持。

ESM的执行可以分为三个步骤：
- 构建，查找模块
- 实例化，创建实例
- 运行，内存关联实例

从上面实例化的过程可以看出，ESM 使用实时绑定的模式，导出和导入的模块都指向相同的内存地址，也就是值引用。而 CommonJS 采用的是值拷贝，即所有导出值都是拷贝值。

#### Esbuild
Vite底层使用Esbuild实现对 .ts、.jsx、.js 代码文件的转化。

Esbuild 是由 Figma 的 CTO 「Evan Wallace」基于 Golang 开发的一款打包工具，相比传统的打包工具，主打性能优势，在构建速度上可以快10~100 倍。

它的优势来源于 GO 语言的能力：
- 编译运行 vs 解释运行
- 多线程 vs 单线程

目前他支持以下的功能：
- 加载器
- 压缩
- 打包
- Tree Shaking
- Source Map

Esbuild总共提供了四个函数：transform、build、buildSync、Service。有兴趣的可以移步[官方文档](https://esbuild.github.io/api/)了解。

#### Rollup
在生产环境下，Vite 使用 Rollup 来进行打包。

Rollup是基于ESM的JavaScript打包工具。\
能针对源码进行 Tree Shaking。\
Scope Hoisting 减小输出文件大小。

#### 核心原理

ES6 的模块加载：
```js
<script type="module" src="/src/main.js"></script>
```
当声明一个模块时，浏览器会解析地址并在当前域名发起一个 GET 请求 main.js 文件。并在文件内部递归发起 `import` 的文件请求。

Vite核心原理：
- 利用 ES6 的 import， 遇到 import 就发送一个 HTTP 请求加载文件
- Vite 启动一个 Koa 服务拦截发送的请求，在Koa服务中对文件进行简单的分解 与 整合
- 以 ESM 格式返回给浏览器

#### 按需加载
只加载当前页面用到的模块，而且不需要解析依赖、打包 等过程。

#### 热更新

**webpack**：通过 WebSocket 建立浏览器和服务器的连接，监听到文件变化，则重新加载模块。

**Vite**:
- 创建 WebSocket
- chokidar 监听文件变更
- 通知变更
- 获取更新文件

#### 利用浏览器的缓存
因为是利用 HTTP 发起的文件请求，所以可以利用浏览器的缓存机制。

#### 基于esbuild的预编译
Vite预编译之后，将文件缓存在 `node_modules/.vite/`。

预编译的作用：
- 支持CommonJS，转化成 ESM 模块并缓存入 node_modules/.vite
- 减少请求数量
  例如：lodash-es 这种包会有几百个子模块，当代码中出现 import { debounce } from 'lodash-es' 会发出几百个 HTTP 请求， Vite 将有许多内部模块的 ESM 依赖关系转换为单个模块，以提高后续页面加载性能。
