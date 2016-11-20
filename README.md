# you-don`t-need-jquery 速查表
##一、选择器
####1、核心选择器
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
2.1JQuery 用法
(1)父元素：$("").parent();<br>
(2)父父元素：$("").parent().parent();<br>
(3)子元素：$("").children();<br>
(4)子元素快速选择:$("DIV>P")<br>
