> 建议大家每一道题都要画图（尤其是复杂一些的题目），画图过程能让我们把基础知识掌握的更加扎实，而且更加有效的算出正确的答案
>
> 先自己计算，都完成后在开始测试答案，千万不要直接的输出看答案，这样就没有意义了

#####  一、选择题

1、
# B
```javascript
console.log(a); 
var a=12; 
function fn(){
	console.log(a); 
	var a=13;	
}
fn();   
console.log(a);

/*
 A、undefined  12 13             
 B、undefined undefined 12   
 C、undefined undefined 13         
 D、有程序报错
*/
```

2、
# A
```javascript
console.log(a); 
var a=12;
function fn(){
	console.log(a);
    a=13;
}
fn();
console.log(a);

/*
 A、undefined  12 13             
 B、undefined undefined 12   
 C、undefined undefined 13         
 D、有程序报错
*/
```

3、
# D
```javascript
console.log(a);
a=12;
function fn(){
	console.log(a);
	a=13;	
}
fn();
console.log(a);

/*
 A、undefined  12 13             
 B、undefined undefined 12   
 C、undefined undefined 13         
 D、有程序报错
*/
```

4、
# A
```javascript
var foo=1; 
function bar(){
    if(!foo){
        var foo=10; 
    }
    console.log(foo); 
}
bar();

/*
 A、1     
 B、10     
 C、undefined    
 D、报错
*/
```

5、无需画图

# C
```javascript
var n=0; 
function a(){
	var n=10; 
	function b(){
		n++; 
	    console.log(n); 
    }
    b();
    return b; 
}
var c=a();
c(); 
console.log(n);


/*
 A、1 1 1   
 B、11 11 0  
 C、11 12 0  
 D、11 12 12
*/
```

6、
# D
```javascript
var a=10,b=11,c=12;
function test(a){
     a=1;
     var b=2;
     c=3;
}
test(10);
console.log(a);  
console.log(b);   
console.log(c);

/*
 A、1 11 3   
 B、10 11 12  
 C、1 2 3   
 D、10 11 3
*/
```

7、
#  B
```javascript
if(!("a" in window)){
   var a=1;
}
console.log(a);

/*
 A、1   
 B、undefined   
 C、报错   
 D、以上答案都不对
*/
```

8、
# B
```javascript
var a=4;
function b(x,y,a) {	   
     console.log(a); 
     arguments[2]=10;        
     console.log(a); 
}
a=b(1,2,3);   
console.log(a); 

/*
 A、3  3  4   
 B、3  10  4   
 C、3  10  10   
 D、3  10  undefined
*/
```

9、
# 
```javascript
var foo='hello'; 
(function(foo){
   console.log(foo);
   var foo=foo||'world';
   console.log(foo);
})(foo);
console.log(foo);

/*
 A、hello hello hello   
 B、undefined world  hello   
 C、hello world world   
 D、以上答案都不正确
*/
```

10、需画图
# D
```javascript
var a=9; 
function fn(){ 
	a=0; 	   
    return function(b){ 
	    return b+a++; 
    }    
}
var f=fn();
console.log(f(5));
console.log(fn()(5));
console.log(f(5));
console.log(a);

/*
 A、6 6 7 2   
 B、5 6 7 3   
 C、5 5 6 3   
 D、以上答案都不正确 
*/
```

##### 二、问答题（需要画图）

1、

```javascript
var ary=[1,2,3,4];
function fn(ary){
	ary[0]=0;    
	ary=[0];    
	ary[0]=100;    
	return ary; 
}
var res=fn(ary);    
console.log(ary);    
console.log(res);
```
[0,2,3,4],[100] 
2、

```javascript
function fn(i) {
    return function (n) {
        console.log(n + (i++));
    }
}
var f = fn(10);
f(20);
fn(20)(40);
fn(30)(50);
f(30);
```
12,61,81,42
3、

```javascript
var i = 10;
function fn() {
    return function (n) {
        console.log(n + (++i));
    }
}
var f = fn();
f(20);
fn()(20);
fn()(30);
f(30);
```
31,32,43,44
4、无需画图
# “4 ” “10”
```javascript
var test = (function(i){
    return function(){
        alert(i*=2);
    }
})(2);
test(5);
```

5、

```javascript
var a=1;
var obj ={
   "name":"tom"
}
function fn(){
   var a2 = a;
   obj2 = obj;
   a2 =a;
   obj2.name =”jack”;
}
fn();
console.log(a);
console.log(obj);
```
1 {name:'jack'}
6、无需画图

```javascript
var a = 1;
function fn(a){
    console.log(a)
    var a = 2;
    function a(){}
}
fn(a)
```
1 
7、

```javascript
var a=0,
	b=0;
function A(a){
	A=function(b){
    	alert(a+b++);
	};
    alert(a++);
}
A(1);
A(2);
```
'2','5'


##### 三：附加思考题（面试题）

1、以下代码的功能是要实现为5个input按钮循环绑定click点击事件，绑定完成后点击1、2、3、4、5五个按钮分别会alert输出0、1、2、3、4五个字符。（腾讯）

- 请问如下代码是否能实现？
- 如果不能实现那么现在的效果是什么样的？
- 应该做怎样的修改才能达到我们想要的效果，并说明原理？  
```html
<div id="btnBox">
	<input type="button" value="button_1" />
    <input type="button" value="button_2" />
    <input type="button" value="button_3" />
    <input type="button" value="button_4" />
    <input type="button" value="button_5" />
</div>

<script type="text/javascript">
    var btnBox=document.getElementById('btnBox'),
        inputs=btnBox.getElementsByTagName('input');
    var l=inputs.length;
    for(var i=0;i<l;i++){
	    inputs[i].onclick=function(){
		    alert(i);
	    }
    }
</script>
```
##### 答案
> 不能实现 for 循环中var的i是一个全局作用域，在循环完成后i的值也随之进行了改变，是的是最后循环i的值所以最后i的值是5导致每次弹出框的中值都是‘5’
2、document.parentNode 和 document.parentnode 的区别？（腾讯）

3、你理解的闭包作用是什么，优缺点？（乐视）
- 保护 ：私有变量和外界没有必然的练习
- 保存 ： 形成不销毁的栈内存，里面的私有变量等信息保存下来了
4、简述let和var的区别
#### let 、const和var的区别
> let /const不存在变量提升机制
    创建变量的六种方式当中：var/function有变量提升，而let、const、import都不存在这个机制

> 在同一个作用域下 var可以重复声明let则不可以重复声明
(在相同的作用域当中或执行上下文当中如果使用var关键词或者是function声明变量或者是重复声明，是不会有影响的【声明第一次之后之后在遇到就不会重复声明了】，但是使用let、const就不行，游览器会校验当前作用域当中是否已经存在这个变量了，如果已经存在了，则不再基于let等重新声明就会报错)，【在浏览器开辟咱内存提供代码自上而下执行之前，不仅有变量提升的操作，还有很多其他的操作=>"词法解析"或者是“词法检测”：就是加测当前即将要执行的代码是否会出现语法错误，如果出现错误，代码不还在执行（代码第一行也不会执行）】【所谓重复：不管之前通过什么办法，只要当前栈内存中存在了这个变量，我们使用let还是const等重复再声明这个变量就是语法错误
】

>let 能解决typeof 的暂时性四区的问题，let比var更加严谨
