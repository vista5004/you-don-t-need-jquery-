# you-don`t-need-jquery 速查表
##一、选择器
#### 1、核心选择器
1.1 JQuery用法
(1)<code>id:$("#id")</code><br>
(2)<code>class:$(".class")</code><br>
(3)<code>element: $("div")</code><br>
(4)伪类：<code>$("input:focus")</code><br>
1.2 Javascript+webAPI用法
(1)<code>id:document.getElementById("id")</code><br>
(2)<code>class:document.getElementsByClass("class')</code><br>
(3)<code>element:document.getElementsByTagName("div")</code><br>
(4)伪类：<code>document.querySelector('input:focus')</code><br>
####2、关系选择器
2.1 JQuery 用法
(1)父元素：<code>$("").parent();</code><br>
(2)父父元素：<code>$("").parent().parent();</code><br>
(3)子元素：<code>$("").children();</code><br>
(4)子元素快速选择:<code>$("DIV>P");</code><br>
(5)所以节点包括文本：<code>$("").contents();</code><br>
(6)所有节点；<code>$("a > *");</code><br>
2.2 Javascript+webAPI用法
(1)父元素：<code>element.parentNode;</code><br>
(2)父元素的父元素：<code>element.parentNode.parentNode;</code><br>
(3)子元素：<code>element.childNodes;</code><br>
(4)子元素快速选择:<code>document.querySelectorAll("div > p");</code><br>
(5)所有的节点：<code>var result=document.querySelectorAll('DIV > *')</code>;<br>
(6)指定特殊节点：<code>var result=document.querySelectorAll('DIV > P')</code>;//P
(7)制定节点下面的子节点：<code>DIV.childNodes</code>
####3、同级选择器
3.1 JQuery 用法
(1)相邻的兄弟节点（除自己外都是）：<code>$("").siblings()</code>;
(2)前面的相邻节点：<code>$("").prev()</code>;
(3)后面的相邻节点：<code>$("").next()</code>;
3.2 Javascript+webAPI用法
(1)所有的节点：<code>var result=document.querySelectorAll('#parent > SPAN ~ *')</code>;
(2)指定SPAN元素旁边是DIV元素的特殊节点：<code>var result=document.querySelectorAll('#parent > SPAN ~ DIV')</code>;//P
(3)指定SPAN元素第一个节点元素：<code>var result=document.querySelector('#parent > SPAN + *')</code>
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
4.1 JQuery 用法
(1)父元素：<code>var $result=$('p').parent();</code>
(2)最相近的元素：<code>$("p").closet("DIV")</code>
(3)找到子元素：<code>$("ul").find("*")</code>
(4)找到特定子元素：<code>$("ul").find('p')</code>
4.2 Javascript+webAPI用法
(1)找到所有父元素：
```
var currentElement=document.getElementsByTagName('a')[0]；
var parents=[];
while(element.parentElement){
    parents.push(currentElement.parent);
    currentElement=currentElement.parentElement;
}
```
(2)找到最相近的元素
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
(3)找到子元素:<code>document.querySelectorAll('UL *')</code>
(4)找到所有子元素:<code>document.querySelectorAll('UL SPAN')</code>











