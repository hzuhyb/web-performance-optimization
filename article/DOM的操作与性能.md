# DOM的操作与性能

## web 的性能瓶颈，主要有一下原因。

（1）**Web基于DOM，而DOM很慢。**浏览器打开网页时，需要解析文档，在内存中生成DOM结构，如果遇到复杂的文档，这个过程是很慢的。可以想象一下，如果网页上有上万个、甚至几十万个形状（不管是图片或CSS），生成DOM需要多久？更不要提与其中某一个形状互动了。

（2）**DOM拖慢JavaScript。**所有的DOM操作都是同步的，会堵塞浏览器。JavaScript操作DOM时，必须等前一个操作结束，才能执行后一个操作。只要一个操作有卡顿，整个网页就会短暂失去响应。浏览器重绘网页的频率是60FPS（即16毫秒/帧），JavaScript做不到在16毫秒内完成DOM操作，因此产生了跳帧。用户体验上的不流畅、不连贯就源于此。

（3）**网页是单线程的。**现在的浏览器对于每个网页，只用一个线程处理。所有工作都在这一个线程上完成，包括布局、渲染、JavaScript执行、图像解码等等，怎么可能不慢？

（4）**网页没有硬件加速。**网页都是由CPU处理的，没用GPU进行图形加速。

上面这些原因，对于PC还不至于造成严重的性能问题，但是对于web app就会有性能瓶颈的问题，因为手机的硬件资源相对有限，而且用户互动又相对频繁。

## 高性能操作DOM

### 缓存DOM对象

``` python
var liNode, i, m;
for (i = 0, m = data.length; i < m; i++) {
    liNode = document.createElement("li");
    liNode.innerText = data[i];
    document.getElementById("container").appendChild(liNode);
}
```
这里每一次循环都会去查找id为container的元素，效率自然非常低，所以我们需要将元素在循环前查询完毕，在循环中仅仅是引用就行了，修改代码为：
``` python
var ulNode = document.getElementById("container");
var liNode, i, m;
for (i = 0, m = data.length; i < m; i++) {
    liNode = document.createElement("li");
    liNode.innerText = data[i];
    ulNode.appendChild(liNode);
}
```

### 在内存中操作DOM

由于DOM操作会导致浏览器的回流，回流需要花费大量的时间进行样式计算和节点重绘与渲染，所以应当尽量减少回流次数。一种可靠的方法就是加入元素时不要修改页面上已经存在的元素，而是在内存中的节点进行大量的操作，最后再一并将修改运用到页面上。DOM操作本身提供一个创建内存节点片段的功能:document.createDocumentFragment()，我们可以将其运用于上述代码中：
``` python
var ulNode = document.getElementById("container");
var liNode, i, m;
var fragment = document.createDocumentFragment();
for (i = 0, m = data.length; i < m; i++) {
    liNode = document.createElement("li");
    liNode.innerText = data[i];
    fragment.appendChild(liNode);
}
ulNode.appendChild(fragment);
```
这样就只会触发一次回流，效率会得到很大的提升。如果需要对一个元素进行复杂的操作（删减、添加子节点），那么我们应当先将元素从页面中移除，然后再对其进行操作，或者将其复制一个（cloneNode()），在内存中进行操作后再替换原来的节点

### 一次性DOM节点生成

在这里我们每次都需要生成节点（document.createElement("li")），然后将其加入到内存片段中，我们可以通过innerHTML属性来一次性生成节点，具体的思路就是使用字符串拼接的方式，先生成相应的HTML字符串，最后一次性写入到ul的innerHTML中。修改代码为：
``` python
var ulNode = document.getElementById("container");
var fragmentHtml = "", i, m;
for (i = 0, m = data.length; i < m; i++) {
    fragmentHtml += "<li>" + data[i] + "</li>";
}
ulNode.innerHTML = fragmentHtml;
```
这样效率也会有提升，不过手动拼写字符串是相当麻烦的一件事

### 虚拟DOM

- [怎么更好的理解虚拟DOM](https://www.zhihu.com/question/29504639)
- [React 虚拟DOM浅析](http://www.alloyteam.com/2015/10/react-virtual-analysis-of-the-dom/)
