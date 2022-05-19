# 自我修养

## 八股文

## ESNext

## CSS3

## HTML5

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
#### 18
### 严格模式
- 由于fiber时间分片机制会导致部分渲染重复进行，因此dev strict下强制渲染阶段跑两次，以排查不应有的副作用，确保渲染阶段的函数是幂等的
- 考虑到fast refresh和未来的resuabled states，dev下组件会先mount->unmount->mount，表明组件可能会多次加载

## 工程化
### Webpack/grunt
#### 工作原理
#### 编写loader/plugin
#### module-federation
### eslint
### git

## 性能监控/优化

## Nodejs
### Koa/Express
### NextJs

## new stuff
### WMA
### PWA
### svelt

## good to know
### 微前端
### RN
### 自动化测试
### 小程序
### 跨端统一方案
### 自动化测试
### k8s
