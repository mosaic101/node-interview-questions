//fixme node是搞后端的，不应该被被归为前端，更不应该用前端的观点去理解，去面试node开发人员。所以这份面试题大全，更侧重后端应用与对Node核心的理解。

#### 1.module.exports与exports 的区别？
参考答案：模块内部大概是这样：
```javascript
exports = module.exports = {};
```
- exports是module.exports的一个引用
- require引用模块后，返回给调用者的是`module.exports`而不是`exports`
- exports.xxx，相当于在导出对象上挂属性，该属性对调用模块直接可见
- exports =相当于给`exports`对象重新赋值，调用模块不能访问`exports`对象及其属性
- 如果此模块是一个类，就应该直接赋值给`module.exports`，这样调用者就是一个类构造器，可以直接new实例

官方api ： https://nodejs.org/api/modules.html#modules_module_exports
cnode社区：https://cnodejs.org/topic/52308842101e574521c16e06
github issues: https://github.com/chemdemo/chemdemo.github.io/issues/2

#### 2.ES6有哪些新特性？

参考答案：类的支持，模块化，箭头操作符，let/const块作用域，字符串模板，解构，参数默认值/不定参数/拓展参数,for-of遍历,generato
r器, Map/Set, Promise

#### 3.你对ES6的个人看法？

参考答案：ES6必火！从软件工程角度来看，以前真的很弱，不适合做大型应用，很容易导致烂尾工程。ES6就相当于当年的Java5,是历史性的发展，从此我们可以用js做大型项目了。事实上，各大主流浏览器现在已经支持大部分新特性了，后端的Node.js更是可以直接使用ES6的绝大多数语法。

#### 4.常用js类定义的方法有哪些？  

参考答案：主要有构造函数原型和对象创建两种方法。原型法是通用老方法，对象创建是ES5推荐使用的方法.目前来看，原型法更普遍.  

代码演示  
1) 构造函数方法定义类  
```javascript
	function Person(){
		this.name = 'michaelqin';
	}
	Person.prototype.sayName = function(){
		alert(this.name);
	}

	var person = new Person();
	person.sayName();
```
2) 对象创建方法定义类  
```
	var Person = {
		name: 'michaelqin',
		sayName: function(){ alert(this.name); }
	};

	var person = Object.create(Person);
	person.sayName();
```

#### 5.js类继承的方法有哪些？

参考答案：原型链法，属性复制法和构造器应用法.  另外，由于每个对象可以是一个类，这些方法也可以用于对象类的继承．

