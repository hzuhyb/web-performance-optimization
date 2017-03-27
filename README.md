# 在这里记录了自己做的一些性能优化工作。


## Step（性能优化的工作步骤）

### 关键词

#### 性能优化的工具

火焰图、瀑布流、时间轴、Fiddle抓包、AB 工具、网速设置工具

#### 性能优化的网络优化

DNS-Prefetch、preload、preRender、TTL、TTFB、GZip、307 状态码

#### 页面的优化

资源的压缩、打包、内敛，模块的懒加载、懒执行、懒渲染

#### 代码层面的优化

重绘、回流、FPS、节流、事件代理

### 学会用Chrome DevTools

- [Chrome开发者工具详解系列](http://web.jobbole.com/89079/)
- [Chrome DevTools — Network](https://segmentfault.com/a/1190000008407729)
- [Chrome DevTools 之 Network](http://www.jianshu.com/p/471950517b07)
- [Chrome DevTools 之 Timeline](http://www.jianshu.com/p/b8cdcd9bfad8)
- [Chrome DevTools 之 Profiles](http://www.jianshu.com/p/504bde348956)


### 了解内存，知道内存的产生原因；了解 JavaScript 的垃圾收集机制，知道垃圾收集方式；然后学会用Chrome DevTools发现内存泄漏，以及知道内存泄漏的原因和如何避免

- [JavaScript垃圾收集机制](https://github.com/huangtubiao/performance-optimization-road/blob/master/article/JavaScript垃圾收集机制.md)
- [搞定JavaScript内存泄漏](https://boke.io/gao-ding-nei-cun-xie-lou/)
- [JavaScript常见的内存泄漏原因](https://boke.io/javascriptnei-chang-jian-nei-cun-xie-lou-yuan-yin/)
- [关于dom清空的内存泄漏问题](https://boke.io/guan-yu-domqing-kong-de-nei-cun-xie-lu-wen-ti/)
- [4类 JavaScript 内存泄漏及如何避免](http://jinlong.github.io/2016/05/01/4-Types-of-Memory-Leaks-in-JavaScript-and-How-to-Get-Rid-Of-Them/)
- [使用 Chrome Timeline 来优化页面性能](https://blog.coding.net/blog/Chome-Timeline)
- [高频dom操作和页面性能优化探索](https://segmentfault.com/p/1210000008426904/read)
- [单页面应用下的JS内存管理](http://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651225853&idx=1&sn=e2a7686a9eea4775eaf4065e002cc4d5&chksm=bd49a7798a3e2e6f8bdaa3d07c99ddf2ae4802afa708c08762ab2a58aaa48004d4e38cc9939b&scene=21#wechat_redirect)
- [单页面应用下的JS内存管理实战](http://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651225864&idx=1&sn=292dd36cbcbb7d57c67718752ceaf6d0&chksm=bd49a68c8a3e2f9aa91e21741e1b7a6c46119d68ad1f8e8ad8578f302b18f304e3b345c10c76&mpshare=1&scene=23&srcid=0224iCeq1IV4iqbA42OSOYxi%23rd)


### 学会JavaScript设计模式，优化现有的代码

- 【JavaScript设计模式与开发实践】书籍。


### 性能优化，了解HTTP协议必不可少

- 【HTTP权威指南】书籍。


### 因为这次主要是动画的优化，因此必须记录要关于动画的优化

- [说说动画卡顿的解决方案](https://segmentfault.com/a/1190000006708777)


### 视频直播


## 关于性能优化的一些好文章

- [前端性能优化](http://ymfe.tech/blog/2016-09-24-fe-performance-optimization/)
- [深度剖析浏览器渲染性能原理，你到底知道多少？](http://www.jianshu.com/p/a32b890c29b1)
- [【译】编写高性能JavaScript](http://www.alloyteam.com/2012/11/performance-writing-efficient-javascript/#prettyPhoto)
- [浅谈函数节流](http://www.alloyteam.com/2012/11/javascript-throttle/)
- [DOM的操作与性能](https://github.com/huangtubiao/performance-optimization-road/blob/master/article/DOM的操作与性能.md)
- [JavaScript闭包与内存泄露](https://github.com/huangtubiao/performance-optimization-road/blob/master/article/JavaScript闭包与内存泄露.md)
- [JavaScript 启动性能探究](https://github.com/xitu/gold-miner/blob/master/TODO/javascript-start-up-performance.md)
