# JavaScript闭包与内存泄露

- 匿名函数：就是没有函数名的函数；
- 闭包：看下文。

要理解闭包，首先必须理解Javascript的作用域链。

## 作用域链

**当函数被调用时：**

1.先创建一个执行环境(execution context),及相应的作用域链；
2.将arguments和其他命名参数的值添加到函数的活动对象(activation object)

**作用域链：**当前函数的活动对象优先级最高，外部函数的活动对象次之，外部函数的外部函数的活动对象处于第三位，......依次递减，直至作用域链终点的全局执行环境。优先级就是变量查找的先后顺序；

待写。。。

##  什么是闭包？

（1）闭包是指有权访问另一个函数作用域中变量的函数 --《JS高级程序设计第三版》 
（2）函数对象可以通过作用域链相关联起来，函数体内部的变量都可以保存在函数作用域内，这种特性称为 ‘闭包’ 。 --《JS权威指南》 
（3）内部函数可以访问定义它们的外部函数的参数和变量(除了this和arguments)。 --《JS语言精粹》 

**来创建个简单的闭包**

``` python
var sayName = function(){
    var name = 'jozo';
    return function(){
        alert(name);
    }
};
var say = sayName(); 
say();
``` 

来解读后面两个语句：

- **var say = sayName() ：**返回了一个匿名的内部函数保存在变量say中，并且引用了外部函数的变量name，由于垃圾回收机制，sayName函数执行完毕后，变量name并没有被销毁。
- **say() ：**执行返回的内部函数，依然能访问变量name,输出 'jozo' .

## 闭包的用途

闭包可以用在许多地方。它的最大用处有两个，一个是前面提到的可以读取函数内部的变量，另一个就是让这些变量的值始终保持在内存中。

``` python
function f1(){
    var n=999;
    
　　 nAdd = function() { n+=1 }
　　 function f2() {
　　　　alert(n);
　　 }
　　 return f2;
}
var result=f1();
result(); // 999
nAdd();
result(); // 1000
``` 

在这段代码中，result实际上就是闭包f2函数。它一共运行了两次，第一次的值是999，第二次的值是1000。这证明了，函数f1中的局部变量n一直保存在内存中，并没有在f1调用后被自动清除。
为什么会这样呢？原因就在于f1是f2的父函数，而f2被赋给了一个全局变量，这导致f2始终在内存中，而f2的存在依赖于f1，因此f1也始终在内存中，不会在调用结束后，被垃圾回收机制（garbage collection）回收。
这段代码中另一个值得注意的地方，就是"nAdd=function(){n+=1}"这一行，首先在nAdd前面没有使用var关键字，因此nAdd是一个全局变量，而不是局部变量。其次，nAdd的值是一个匿名函数（anonymous function），而这个匿名函数本身也是一个闭包，所以nAdd相当于是一个setter，可以在函数外部对函数内部的局部变量进行操作。

事实上，通过使用闭包，我们可以做很多事情。比如模拟面向对象的代码风格；更优雅，更简洁的表达出代码；在某些方面提升代码的执行效率。

**1. 匿名自执行函数**

我们在实际情况下经常遇到这样一种情况，即有的函数只需要执行一次，其内部变量无需维护，比如UI的初始化，那么我们可以使用闭包：

``` python
//将全部li字体变为红色
(function(){    
    var els = document.getElementsByTagName('li');
    for(var i = 0,lng = els.length;i < lng;i++){
        els[i].style.color = 'red';
    }    
})();  
``` 
我们创建了一个匿名的函数，并立即执行它，由于外部无法引用它内部的变量，
因此els,i,lng这些局部变量在执行完后很快就会被释放，节省内存！
关键是这种机制不会污染全局对象。

**2. 实现封装/模块化代码**

``` python
var person= function(){    
    //变量作用域为函数内部，外部无法访问    
    var name = "default";       

    return {    
       getName : function(){    
           return name;    
       },    
       setName : function(newName){    
           name = newName;    
       }    
    }    
}();
console.log(person.name);//直接访问，结果为undefined    
console.log(person.getName());  //default 
person.setName("jozo");    
console.log(person.getName());  //jozo
```

**3. 实现面向对象中的对象**

这样不同的对象(类的实例)拥有独立的成员及状态，互不干涉。虽然JavaScript中没有类这样的机制，但是通过使用闭包，
我们可以模拟出这样的机制。还是以上边的例子来讲:

``` python
function Person(){    
    var name = "default";       
    return {    
       getName : function(){    
           return name;    
       },    
       setName : function(newName){    
           name = newName;    
       }    
    }    
};    

var person1= Person();    
print(person1.getName());    
john.setName("person1");    
print(person1.getName());  // person1  

var person2= Person();    
print(person2.getName());    
jack.setName("erson2");    
print(erson2.getName());  //person2
```

Person的两个实例person1 和 person2 互不干扰！因为这两个实例对name这个成员的访问是独立的 。

## 内存泄露及解决方案

由于IE9之前的版本对JScript对象和COM对象使用不同的垃圾收集例程，因此闭包在IE的这些版本中会导致一些特殊的问题。具体来说，如果闭包的作用域中保存着一个HTML元素，那么就意味着该元素将无法被销毁。来看下面的例子。

``` python
function assignHandler() {
    var element = document.getElementById("someElement");
    element.onclick = function() {
        alert(element.id);
    }
}
``` 

以上代码创建了一个作为element元素事件处理程序的闭包，而这个闭包则又创建了一个循环引用，由于匿名函数保存了一个对assignHandler()的活动对象的引用，因此它所占用的内存就永远不会被回收，不过，这个问题可以通过稍微改写一下代码来解决，如下所示。

``` python
function assignHandler() {
    var element = document.getElementById("someElement");
    var id = element.id;
    
    element.onclick = function() {
        alert(id);
    };

    element = null;
}
``` 

在上面的代码中，通过把element.id的一个副本保存在一个变量中，并且在闭包中引用该变量消除了循环引用。但仅仅做到这一步，还是不能解决内存泄露的问题。必须要记住：闭包会引用包含函数的整个活动对象，而其中包含着element。即使闭包不直接引用element，包含函数的活动对象中也仍然会保存一个引用。因此，有必要被element变量设置为null。这样就能够解除对DOM对象的引用，顺利地减少其引用数，确保正常回收其占用的内存。

# 使用闭包的注意点

1）由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题，在IE中可能导致内存泄露。解决方法是，在退出函数之前，将不使用的局部变量全部删除。

2）闭包会在父函数外部，改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（private value），这时一定要小心，不要随便改变父函数内部变量的值。
