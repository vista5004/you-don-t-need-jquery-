# you-don`t-need-jquery 速查表
##一、选择器
#### 1、核心选择器
1.1 JQuery用法
(1)id:$("#id")<br>
(2)class:$(".class")<br>
(3)element: $("div")<br>
(4)伪类：$("input:focus")<br>
1.2 Javascript+webAPI用法
(1)id:document.getElementById("id")<br>
(2)class:document.getElementsByClass("class')<br>
(3)element:document.getElementsByTagName("div")<br>
(4)伪类：document.querySelector('input:focus')<br>
####2、关系选择器
2.1 JQuery 用法
(1)父元素：$("").parent();<br>
(2)父父元素：$("").parent().parent();<br>
(3)子元素：$("").children();<br>
(4)子元素快速选择:$("DIV>P");<br>
(5)所以节点包括文本：$("").contents();<br>
(6)所有节点；$("a > *");<br>
2.2 Javascript+webAPI用法
(1)父元素：element.parentNode;<br>
(2)父元素的父元素：element.parentNode.parentNode;<br>
(3)子元素：element.childNodes;<br>
(4)子元素快速选择:document.querySelectorAll("div > p");<br>
####3、同级选择器
(1)相邻的兄弟节点（除自己外都是）：$("").siblings();
(2)前面的相邻节点：$("").prev();
(3)后面的相邻节点：$("").next();
(4)
(5)
(6)
(7)
