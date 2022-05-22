# 自我修养

## 八股文

## ESNext

## CSS3

## HTML5
- defer/async. (sync) => (defer) => (DOMContentLoaded) => (async/module? 可能在onload前的任何时刻，甚至早于defer) => (onload)
- cookie
- 跨域

## JS原理
### 事件循环
- js单线程，保证dom操作的可靠性
- [setTimeout时延](https://zhuanlan.zhihu.com/p/155752686) 对于chrome，setTimeout(f, 1) 等价于 setTimeout(f, 0)，此外其他相隔1ms的timeout是不可靠的，很容易超时
- [MutationObserver](https://developer.mozilla.org/zh-CN/docs/Web/API/MutationObserver)

## 浏览器工作原理
### url访问
### 前端缓存
### CORS

## HTTPS

## 前端安全
### CSRF
### XSS
### 加密技术
### 登录技术
#### cas
#### jwt
#### oauth
#### 单点登录

## React
### MVVM概念
- model <> viewmodel <> view
### 数据不可变
- 更新state时生成新的对象，不原地修改
- 利于高效diff，避免遍历对象属性
- fiber下，react有两个vdom，一个为原数、树，一个是新树，更新只在新树上操作，以便实施中断。类似v8对短期内存的gc
### hooks/优化
### 最佳实践
### react版本
#### 16
- 引入fiber机制，异步机制，rIC
- react.lazy Suspense，懒加载
- react.memo 函数式组件的PureComponent
- hooks
+ 更好的逻辑/状态复用方式
+ 将生命周期中相互关联的逻辑拆分成更小的函数，内聚
+ 概念精简。避免复杂的class概念，为内部优化预留空间。函数式。更利于组合。
+ 在现代浏览器中，闭包和类的原始性能只有在极端场景下才会有明显的差别。（hooks本身的性能）
+ 比class更小的创建开支
+ 相较于HOC、renderProps，可以减小组件深度，从而提升性能
#### 17
- 全新版本的 JSX 转换
#### 18
- Automatic batching
- Concurrent APIS
- useTransition 返回isPending、startTransition，将内部的setState引起的更新标记为低优先级
- Root API
+ createRoot 在后台使用并发渲染
- Suspense
- 严格模式
- SSR
+ 原过程：1、server获取数据；2、生成HTML并传输；3、client下载js；4、链接交互（hydration）
+ server流式HTML。允许不等整个app生成完毕就开始返回。（结合Suspense，提早第2步）。允许局部提前hydrate
+ selective hydration。提前hydrate用户开始交互的部分。需要createRoot API
### 严格模式
- 由于fiber时间分片机制会导致部分渲染重复进行，因此dev strict下强制渲染阶段跑两次，以排查不应有的副作用，确保渲染阶段的函数是幂等的
- 考虑到fast refresh和未来的resuabled states，dev下组件会先mount->unmount->mount，表明组件可能会多次加载
### 性能优化
- 缓存： memo etc. 用函数初始化useState；延迟初始化useRef.current
- 按需加载：1、懒加载，react.lazy，同时也是代码分割；2、懒渲染，进入可视区域再实际渲染，如虚拟列表
- state批量更新
- 优化state位置。1、状态下方，避免无关子组件重新渲染；2、使用发布订阅者模式的库，避免中间组件重复渲染。
- 频繁更新时，可以使用debounce、throttle，或者useTransition

## 工程化
### Webpack/grunt
#### 工作原理
- 从entry出发，分析ast，递归收集依赖，打包code
- webpack(config) => compiler => recursive loop files => loader & plugin => output
- file => module(by loader) => ast (by acron/babel) => dependency => other files => loop
- chunks: 默认一个entry一个chunk，动态import单独chunk
- 插件：一个具有apply方法的类，基于`tapable`的发布订阅模式，基于hook
- loader：处理不同类型的文件，将其转为可分析的js
#### 编写loader/plugin
#### module-federation
exports：作为remote暴露出的模块
remotes：作为host需要的其他的模块
shared：共享的模块，一般为第三方库，可指定版本
### eslint
### git

## 性能监控/优化
#### 资源加载
- link rel =
  + dns-prefetch 预先解析dns，只对第三方网站有意义，本站已经解析过
  + preconnect dns+tcp+tls
  + prefetch 预先加载暂时用不到，但接下来可能会需要的，lowest，浏览器空闲时进行
  + preload 预先加载接下来需要的，比如css中引用的其他文件

## Nodejs
### Koa/Express
### NextJs

## new stuff
### WMA
### PWA
### svelt

## good to know
### 微前端
#### 关键点
- 独立开发、独立部署、spa体验
- 子应用接入难度
- css隔离
- 全局变量隔离
- 公共库共享、多版本处理
#### 案例
- single-spa 基座模式，通过systemjs加载子应用，本身无js、css隔离
- qiankun 基座模式，特点为html-entry和sandbox、静态资源预加载，实现快速接入、应用隔离，同时提供一定的应用通信能力
- EMP 自组织，通过MF实现
- wujie，shadowDom + iframe + proxy
### RN
### 自动化测试
### 小程序
### 跨端统一方案
### 自动化测试
### k8s
