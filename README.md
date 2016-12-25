# you-don`t-need-jquery 速查表
##一、选择器
#### 1、核心选择器
1.1 JQuery用法：<p>
(1)<code>id:$("#id")</code><br>
(2)<code>class:$(".class")</code><br>
(3)<code>element: $("div")</code><br>
(4)伪类：<code>$("input:focus")</code><br>
1.2 Javascript+webAPI用法<br>
(1)<code>id:document.getElementById("id")</code><br>
(2)<code>class:document.getElementsByClass("class')</code><br>
(3)<code>element:document.getElementsByTagName("div")</code><br>
(4)伪类：<code>document.querySelector('input:focus')</code><br>
####2、关系选择器
2.1 JQuery 用法<br>
(1)Jquery中parent()方法得到父元素：<code>$("").parent();</code><br>
(2)Jquery中parent()方法得到父父元素：<code>$("").parent().parent();</code><br>
(3)Jquery中children()方法得到子元素：<code>$("").children();</code><br>
(4)Jquery中选择器方法快速选择:<code>$("DIV>P");</code><br>
(5)Jquery中选择器方法所以节点包括文本：<code>$("").contents();</code><br>
(6)所有节点；<code>$("a > *");</code><br>
2.2 Javascript+webAPI用法<br>
(1)父元素：<code>element.parentNode;</code><br>
(2)父元素的父元素：<code>element.parentNode.parentNode;</code><br>
(3)子元素：<code>element.childNodes;</code><br>
(4)子元素快速选择:<code>document.querySelectorAll("div > p");</code><br>
(5)所有的节点：<code>var result=document.querySelectorAll('DIV > *')</code>;<br>
(6)指定特殊节点：<code>var result=document.querySelectorAll('DIV > P')</code>;//P<br>
(7)制定节点下面的子节点：<code>DIV.childNodes</code><br>
####3、同级选择器
3.1 JQuery 用法<br>
(1)Jquery中siblings()方法得到相邻的兄弟节点（除自己外都是）：<code>$("").siblings()</code>;<br>
(2)Jquery中prev()方法得到前面的相邻节点：<code>$("").prev()</code>;<br>
(3)Jquery中next()方法得到后面的相邻节点：<code>$("").next()</code>;<br>
3.2 Javascript+webAPI用法<br>
(1)所有的节点：<code>var result=document.querySelectorAll('#parent > SPAN ~ *')</code>;<br>
(2)指定SPAN元素旁边是DIV元素的特殊节点：<code>var result=document.querySelectorAll('#parent > SPAN ~ DIV')</code>;//P<br>
(3)指定SPAN元素第一个节点元素：<code>var result=document.querySelector('#parent > SPAN + *')</code><br>
(4)找到所有的子元素：
```
var allSiblings=document.querySelectorAll('#parent > SPAN ~ *');
AllSiblings=[].prototype.slice.call(allSiblings);
var currentElement=document.querySelector("#parent > SPAN");
do{
    currentElement=currentElement.previousElementSibling;
    currentElement && allSiblings.unshift(currentElement);
} while(currentElement)
```
(5)找到后一个节点：<br>
节点：<code>var result=document.querySelector('SPAN').nextSibling.nextSibling.nextSibling;</code>
元素：<code>var result=document.querySelector('SPAN').nextElementSibling.nextElementSibling.nextElementSibling;</code>
####4、祖先元素和后代选择器
4.1 JQuery 用法<br>
(1)Jquery中parent()方法得到父元素：<code>var $result=$('p').parent();</code><br>
(2)Jquery中closet()方法得到最相近的元素：<code>$("p").closet("DIV")</code><br>
(3)Jquery中find()方法得到子元素：<code>$("ul").find("*")</code><br>
(4)Jquery中find()方法得到特定子元素：<code>$("ul").find('p')</code><br>
4.2 Javascript+webAPI用法<br>
(1)找到所有父元素：<br>
```
var currentElement=document.getElementsByTagName('a')[0]；
var parents=[];
while(element.parentElement){
    parents.push(currentElement.parent);
    currentElement=currentElement.parentElement;
}
```
(2)找到最相近的元素<br>
```
var close=function(referElement,closeSelector){
     //如果提供了element.closet()方法
     if(referElement.closet()){
        return referElement.closet(closeSelector)
     }
     var matches=Element.prototype.matches ||
                 Element.prototype.msMatchesSelector ||
                 Element.prototype.webkitMatchesSelector,
                 currentElement=referElement;
     while(currentElement){
         if(matches.call(currentElement,closeSelector)){
            return currentElement;
         }
         current.parentElement;
     }
     return null;

}
```
(3)找到子元素:<code>document.querySelectorAll('UL *')</code><br>
(4)找到所有子元素:<code>document.querySelectorAll('UL SPAN')</code><br>

####5、高级元素选择器
5.1 JQuery 用法<br>
(1)不包括某个元素<code> $("ul li").not('.active')</code>;<br>
5.2Javascript+webAPI用法<br>
(1)不包括某个元素：<code>document.querySelectorAll('ul li:not(.active)')</code>;<br>
//低版本解决
```
var items=document.querySelectorAll('ul li');
var result=[];
for(var i=0;i<items.length;i++){
    if(items[i].className!=='active'){
        result.push(items[i]);
    }
}
```
####6、混合元素选择器
6.1 JQuery 用法<br>
(1)Jquery中同时选择多个元素：<code>var result=$("#one ,.two ,ol");</code><br>
6.2Javascript+webAPI用法<br>
同时选择多个元素：<code>var result=document.querySelectorAll('#one ,.two ,ol');</code><br>

####7、混合元素选择器
7.1Javascript+webAPI用法<br>
(1)指定类型的元素：<code>var result=document.querySelectorAll('input[type="button"]')</code><br>
<code> var result=document.querySelectorAll('input[type="password"]')</code><br>
<code>var result=document.querySelectorAll('input[type="file"]')</code><br>
7.2 JQuery 用法<br>
(1)指定类型的元素：<code>var result=$("input[type='button']")<code><br>

####8、Jquery $的替代
8.1Javascript+webAPI用法<br>
(1)通过document.querySelectorAll实现<br>
```
window.$=function(selector){
    return document.querySelectorAll(selector);
}
$(".someClass");
$("#someId");
$(".someParent > .someChild");
$("ul li:not(.active)");
```

##二、元素属性
####1、使用属性找到元素
1.1 JQuery 用法<br>
(1)指定属性的元素：<code>var result=$("[required],[disabled]")</code><br>
1.2Javascript+webAPI用法<br>
(1)指定属性的元素：<code>var result=document.querySelectorAll('[required],[disabled]')</code><br>
####2、使用属性名称与属性值找到元素
2.1 JQuery 用法<br>
(1)指定属性名称与值的元素：<code>var result=$("a[href='www.si.co']")</code><br>
2.2Javascript+webAPI用法<br>
(1)指定属性名称与值的元素：<code>var result=document.querySelectorAll("a[href='www.cos.s']")</code> <br>

####3、使用属性找到元素选择指定属性具有包含一个给定的子字符串的元素
3.1 JQuery 用法<br>
(1)包含一个给定的子字符串的元素：<code>var result=$("a[href*='www']")</code> <br>
3.2Javascript+webAPI用法<br>
(1)包含一个给定的子字符串的元素：<code>var result=document.querySelectorAll("a[href*='www']")</code> <br>

####4、选择指定属性用空格分隔的值中包含一个给定值的元素。
4.1 JQuery 用法<br>
(1)用空格分隔的值中包含一个给定值的元素:<code>var result=$("div[class~='two']")</code> <br>
4.2Javascript+webAPI用法<br>
(1)用空格分隔的值中包含一个给定值的元素:<code>var result=document.querySelectorAll("[class~='two']")</code> <br>

####5、选择指定属性是以给定字符串开始的元素
5.1 JQuery 用法<br>
(1)选择指定属性是以给定字符串开始的元素:<code>var result=$("div[class^='new']")</code> <br>
5.2Javascript+webAPI用法<br>
(1)选择指定属性是以给定字符串开始的元素:<code>var result=document.querySelectorAll("div[class^='new']")</code> <br>

##三、使用元素属性
####1、读取class属性。
1.1 JQuery 用法 <br>
(1)通过hasClass判断是否包含某个特定的元素 <br>
```
var isTick=$("#test").hasClass("tick");
var type=$("#test").hasClass("tick")?"normal":"unNormal"
```
1.2 Javascript+webAPI用法<br>
(1)通过classList来实现<br>
```
var isTick=document.querySelector("#tick").classList.contains("tick");
var type=document.querySelector("#tick").classList.contains("tick").
```
(2)通过正则来实现<br>
```
var hasClass=function(element,className){
    return new RegExp('(^|\\s)'+className+'(^|\\s)').test(element.className);
}
var isTick=hasClass(document.querySelector("#tick"),"tick");
var type=hasClass(document.querySelector("#tick"),"tick")?"normal":"unNormal"
```
####2、添加和删除class属性。
2.1 JQuery 用法<br>
(1)通过addClass和removeClass实现：<code>$(".test").removeClass("red").addClass("blue")</code><br>
2.2 Javascript+webAPI用法<br>
(1)通过classList实现<br>
```
document.querySelectorAll(".test")[0].classList.add("blue");
document.querySelectorAll(".test")[0].classList.remove("red");
```
(2)通过正则实现<br>
```
var removeClass=function(element,className){
    element.className=element.className.replace(new Regex('(^|\\s)'+className+'(^|\\s)'),' ');
}
removeClass(document.getElementsByClassName("test")[0],className);
document.getElementsByClassName("test")[0].className+="red";
```
####3、触发class属性。
3.1 JQuery 用法<br>
(1)通过toggleClass实现：<br>
<code>$("#test").toggleClass("hide")</code><br>
3.2 Javascript+webAPI用法<br>
(1)通过classList实现<br>
<code>document.getElementsByClassName("test")[0].toggleClass("hide")</code>
(2)通过正则实现<br>
```
var toggleClass=function(element,className){
    var pattern =new Regex(new Regex('(^|\\s)'+className+'(^|\\s)'));
    if(pattern.test(element.className)){
       element.className=element.className.replace(pattern,' ');
    }else{
       element.className+=' '+className;
    }
}
toggleClass(document.getElementsByClassName("test")[0],className);
```
####4、读取attribute属性。
4.1 JQuery 用法<br>
(1)通过attr和is实现：<br>
<code>$("input").attr("type")</code><br>
<code>$("input").is("required")</code><br>
4.2 Javascript+webAPI用法<br>
(1)通过getAttribute和hasAttribute实现：<br>
```
document.getElementsByTagName("input")[0].getAttribute('type')
document.getElementsByTagName("input")[0].hasAttribute('required');
```
####5、设置attribute属性。
5.1 JQuery 用法<br>
(1)通过Jquery中方法attr/removeAttr实现：<br>
```
$("input").attr("type","email")
          .removeAttr("required")
          .attr("name","EmailUser")
```
5.2 Javascript+webAPI用法
(1)通过浏览器的setAttribute/removeAttribute实现：<br>
```
document.getElementsByTagName("input")[0].setAttribute("type","email");
document.getElementsByTagName("input")[0].removeAttribute("required");
document.getElementsByTagName("input")[0].setAttribute('name','userName');
```
##四、HTML数据存储
####1、使用data属性来存储数据。
1.1 JQuery 用法<br>
(1)通过Jquery中方法data实现：<br>
```
<img src="default.png" data-zoom-url="www.com">
$("img").data("user","jack");
```
1.2 Javascript+webAPI用法<br>
```
<img src="default.png" data-zoom-url="www.com">
document.getElementsByTaName("img")[0].setAttribute("user","jack");
```
####2、使用data属性来存储负责数据数据。
2.1 JQuery 用法<br>
(1)通过Jquery中方法data实现：<br>
```
$("img").data("secens",[
    {
        offset: 9,
        title: 'intro',
        description: 'introducing the characters',
        location: 'living room'
    },
    {
        offset: 19,
        title: 'in32tro',
        description: 'introdfducing the casharacters',
        location: 'lividnga room'
    },
    {
        offset: 29,
        title: 'indstro',
        description: 'introdugfcing the chaaracters',
        location: 'lisdving sdroom'
    }
])
//使用获取
$("img").date("secens")[0].tittle
```
2.2 Javascript+webAPI用法<br>
```
var cache=[];
var setData=function(el,key,data){
    var cacheIdx=el.getAttribute("data-cache-idx");
    var cacheEntry=cache[cacheIdx] || {};
    cacheEntry[key]=data;
    if(cacheIdx==null){
        cacheIdx=cache.push(cacheEntry)-1;
        el.setAttribute("data-cache-idx",cacheIdx);
    }
}
setData(document.getElementsByTagName('VIDEO')[0],'scenes',[
    {
            offset: 9,
            title: 'intro',
            description: 'introducing the characters',
            location: 'living room'
        },
        {
            offset: 19,
            title: 'in32tro',
            description: 'introdfducing the casharacters',
            location: 'lividnga room'
        },
        {
            offset: 29,
            title: 'indstro',
            description: 'introdugfcing the chaaracters',
            location: 'lisdving sdroom'
        }
])
var cacheIdx=document.getElementsByTagName("img")[0].getAttribute("data-cache-idx");
var message=cache[cacheIdx].scenes[1].tittle

```