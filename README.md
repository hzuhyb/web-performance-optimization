# 在这里记录了自己做的一些性能优化工作。

### :closed_book: 关于性能优化的关键词

#### 性能优化的工具

Chrome DevTool、火焰图、瀑布流、时间轴、Fiddle抓包、Charles、AB 工具、网速设置工具

#### 性能优化的网络优化

DNS-Prefetch、preload、preRender、TTL、TTFB、GZip、307 状态码

#### 页面的优化

资源的压缩、打包、内敛，模块的懒加载、懒执行、懒渲染

#### 代码层面的优化

重绘、回流、FPS、节流、去抖、去定时器、事件代理



### :closed_book: 使用第三方网站获取性能测试报告

- [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
- [GTmetrix](https://gtmetrix.com/)
- [WebPagetest](https://www.webpagetest.org/)



### :closed_book: 学会用Chrome DevTools收集性能指标

- [Chrome开发者工具详解系列](http://web.jobbole.com/89079/)
- [Chrome DevTools — Network](https://segmentfault.com/a/1190000008407729)
- [Chrome DevTools 之 Network](http://www.jianshu.com/p/471950517b07)
- [Chrome DevTools 之 Timeline](http://www.jianshu.com/p/b8cdcd9bfad8)
- [Chrome DevTools 之 Profiles](http://www.jianshu.com/p/504bde348956)



### :closed_book: 了解内存泄漏

- [JavaScript闭包与内存泄露](https://github.com/huangtubiao/performance-optimization-road/blob/master/article/JavaScript闭包与内存泄露.md)
- [JavaScript垃圾收集机制](https://github.com/huangtubiao/performance-optimization-road/blob/master/article/JavaScript垃圾收集机制.md)
- [搞定JavaScript内存泄漏](https://boke.io/gao-ding-nei-cun-xie-lou/)
- [JavaScript常见的内存泄漏原因](https://boke.io/javascriptnei-chang-jian-nei-cun-xie-lou-yuan-yin/)
- [关于dom清空的内存泄漏问题](https://boke.io/guan-yu-domqing-kong-de-nei-cun-xie-lu-wen-ti/)
- [4类 JavaScript 内存泄漏及如何避免](http://jinlong.github.io/2016/05/01/4-Types-of-Memory-Leaks-in-JavaScript-and-How-to-Get-Rid-Of-Them/)
- [使用 Chrome Timeline 来优化页面性能](https://blog.coding.net/blog/Chome-Timeline)
- [单页面应用下的JS内存管理](http://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651225853&idx=1&sn=e2a7686a9eea4775eaf4065e002cc4d5&chksm=bd49a7798a3e2e6f8bdaa3d07c99ddf2ae4802afa708c08762ab2a58aaa48004d4e38cc9939b&scene=21#wechat_redirect)
- [单页面应用下的JS内存管理实战](http://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651225864&idx=1&sn=292dd36cbcbb7d57c67718752ceaf6d0&chksm=bd49a68c8a3e2f9aa91e21741e1b7a6c46119d68ad1f8e8ad8578f302b18f304e3b345c10c76&mpshare=1&scene=23&srcid=0224iCeq1IV4iqbA42OSOYxi%23rd)
- [JS内存泄漏排查方法-Chrome Profiles](http://caibaojian.com/chrome-profiles.html)
- [深入理解Node.js垃圾回收与内存管理](http://www.jianshu.com/p/4129a3fce7bb)



### :closed_book: 知道浏览器的工作原理以及渲染过程

- [浏览器的工作原理：新式网络浏览器幕后揭秘（上）](http://mp.weixin.qq.com/s/ux2QduYgN_LMjLhmMg8ToA)
- [浏览器的工作原理：新式网络浏览器幕后揭秘（中）](http://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651226390&idx=2&sn=b25a894eab68f98d65e23c5ea24b8b73&chksm=bd4958928a3ed184d09d15661414e889116e0a3f0e37ce89b40ad8ddfe67efa24380e3443cd7&mpshare=1&scene=23&srcid=0423abTS9uh9nRZmSfv3SYjG#rd)
- [浏览器的工作原理：新式网络浏览器幕后揭秘（下）](http://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651226390&idx=3&sn=c4aa43af945ad73250b7ea71ae5816f8&chksm=bd4958928a3ed1849a47b139a3bd6884b2424638ba47f6f2b4939fe969fb405fb358edac59e1&mpshare=1&scene=23&srcid=0423bMoeJZYRTd5OmFgjLu7R#rd)
- [深度剖析浏览器渲染性能原理，你到底知道多少？](http://www.jianshu.com/p/a32b890c29b1)



### :closed_book: 性能优化的网络优化

- [【前端性能】浅谈域名发散与域名收敛 ](https://github.com/chokcoco/cnblogsArticle/issues/1)
- [移动Web首屏优化实践 ](https://github.com/huangtubiao/web-performance-optimization/blob/master/PDF/%E7%A7%BB%E5%8A%A8Web%E9%A6%96%E5%B1%8F%E4%BC%98%E5%8C%96%E5%AE%9E%E8%B7%B5.pdf)



### :closed_book: 首屏优化

- [深入研究Chrome：Preload与Prefetch原理，及其优先级](http://www.10tiao.com/html/184/201704/2247485131/1.html)
- [手Q Hybrid App优化之路](https://github.com/huangtubiao/web-performance-optimization/blob/master/PDF/%E6%89%8BQ%20Hybrid%20App%E4%BC%98%E5%8C%96%E4%B9%8B%E8%B7%AF.pdf)
- [移动端首屏白屏的解决方案]()
- [移动Web首屏优化实践](https://github.com/huangtubiao/web-performance-optimization/blob/master/PDF/%E7%A7%BB%E5%8A%A8Web%E9%A6%96%E5%B1%8F%E4%BC%98%E5%8C%96%E5%AE%9E%E8%B7%B5.pdf)
- [Web性能优化之 “直出” 理论与实践总结](https://segmentfault.com/a/1190000005641012)
- [淘宝首页性能优化实践](http://taobaofed.org/blog/2016/04/05/optimize-in-tbhome/)


### :closed_book: 代码层面上优化

#### :book: JS优化

- [【译】编写高性能JavaScript](http://www.alloyteam.com/2012/11/performance-writing-efficient-javascript/#prettyPhoto)
- [浅谈函数节流](http://www.alloyteam.com/2012/11/javascript-throttle/)
- [JavaScript 启动性能探究](https://github.com/xitu/gold-miner/blob/master/TODO/javascript-start-up-performance.md)

#### :book: DOM优化

- [高频dom操作和页面性能优化探索](https://segmentfault.com/p/1210000008426904/read)
- [DOM的操作与性能](https://github.com/huangtubiao/performance-optimization-road/blob/master/article/DOM的操作与性能.md)

#### :book: 动画优化

- [说说动画卡顿的解决方案](https://segmentfault.com/a/1190000006708777)
- [CSS3 3D 行星运转动画 + 浏览器渲染原理](http://web.jobbole.com/85993/)
- [页面滚动FPS较低的解决方案]()

#### :book: 滚动优化

- [移动web之滚动篇](http://www.alloyteam.com/2017/04/secrets-of-mobile-web-scroll-bars-and-drop-refresh/)
- [高性能滚动 scroll 及页面渲染优化](http://web.jobbole.com/86158/)
- [手Q Hybrid App优化之路](https://github.com/huangtubiao/web-performance-optimization/blob/master/PDF/%E6%89%8BQ%20Hybrid%20App%E4%BC%98%E5%8C%96%E4%B9%8B%E8%B7%AF.pdf)
- [开发眼中的交互优化](https://github.com/huangtubiao/web-performance-optimization/blob/master/PDF/%E5%BC%80%E5%8F%91%E7%9C%BC%E4%B8%AD%E7%9A%84%E4%BA%A4%E4%BA%92%E4%BC%98%E5%8C%96.pdf)
- [如何不择手段提升scroll事件的性能](https://zhuanlan.zhihu.com/p/30078937?utm_medium=social&utm_source=wechat_session)


### :closed_book: 底层上优化

#### :book: 浏览器对代码做的一些优化

- [V8引擎深入研究目录贴](https://segmentfault.com/a/1190000008618731)
- [WebRender：让网页渲染如丝顺滑](http://www.zcfy.cc/article/4386?from=timeline&isappinstalled=0)

#### :book: JS与Native交互时相互通信的成本问题



### :closed_book: 自动化的性能监控方案



### :closed_book: 泛谈性能优化

- [前端性能优化](http://ymfe.tech/blog/2016-09-24-fe-performance-optimization/)
- [性能专栏（Performance Column）](https://github.com/barretlee/performance-column)
- [前端细节优化](https://github.com/kangkk/web_performance_optimization)

#### :book: H5
- [手Q Hybrid App优化之路](https://github.com/huangtubiao/web-performance-optimization/blob/master/PDF/%E6%89%8BQ%20Hybrid%20App%E4%BC%98%E5%8C%96%E4%B9%8B%E8%B7%AF.pdf)
- [移动Web首屏优化实践 ](https://github.com/huangtubiao/web-performance-optimization/blob/master/PDF/%E7%A7%BB%E5%8A%A8Web%E9%A6%96%E5%B1%8F%E4%BC%98%E5%8C%96%E5%AE%9E%E8%B7%B5.pdf)
- [移动 WEB 通用优化策略介绍](https://imququ.com/post/wpo-of-mobile-web-1.html)
- [WebView性能、体验分析与优化](http://tech.meituan.com/WebViewPerf.html)

#### :book: PC
- [如何让博客速度快到哭](https://ppt.baomitu.com/d/a8a49a00?from=timeline&isappinstalled=0#/1)

### :closed_book: 优化方案

- [AMP，来自 Google 的移动页面优化方案](https://imququ.com/post/amp-project.html)
- [MIP](https://www.mipengine.org/)

### :closed_book: 其它

- [Google开发者官网-web](https://developers.google.com/web/?hl=zh-cn)
