#javascript高级程序设计第六章(面向对象的程序设计)
对象属性
1.数据属性：
Object.defineProperty(所在对象,属性的名字,一个描述符对象)
configurable:能否把属性修改为访问器属性 默认true  
enumerable:能否for in循环属性 默认true 
writable:表示能否修改属性的值 默认true
value:属性值
2.访问器属性:
configurable:能否把属性修改为访问器属性 默认true  
enumerable:能否for in循环属性 默认true 
get:在读写时调用的函数
set:在写入属性时调用的函数

var obj={
	_year:2004,
	edition:1
}
Object.defineProperty(obj,"year",{
	enumerable:true,
	get:function(){
		return this._year*2
	},
	set:function(newValue){
		if(newValue>2004)
		{
			this._year=newValue
			this.edition=newValue-2004
		}
	}
})
obj.year=2006
console.log(obj.edition)


Object.defineProperties(对象，对象要修改的属性)修改多个属性

读取属性的特征:Object.getOwnPropertyDescriptor


##工厂模式:在函数里面创建对象并且return
function createPerson(name,age)
{
	var obj={name:name,age:age}
	return obj
}
var person1=createPerson("shanks",11)


##构造函数 可用instaceof判断对象类型
function createPerson(name,age)
{
	this.name="shanks"
	this.age=22
}
var person1=new createPerson("shanks",11)
console.log(person1 instanceof Array)

##原型模式
function Person(){}
Person.prototype.name="shanks"
Person.prototype.age=22
//字面量方法
Person.prototype={
	name:"shanks",
	age:22
}


##组合模式   构造函数加上原型方法
function Person(name,age)
{
this.name=name
this.age=age
}
Person.prototype={
	constructor:Person,
	sayName:function(){return this.name}
}
var friend=new Person("shanks",22)



##
function Person(name,age)
{
this.name=name
this.age=age
if(typeof this.sayName!="function"){
	Person.prototype.sayName=function(){return this.name}
	}
}




##测试是否指向某个原型
isPrototypeOf()  instanceof 都是确定原型跟实例之间的关系
例如Person.prototype.isPrototypeOf(person1)
或者新方法
Object.getPrototypeOf(person1)==Person.prototype  true

#hasOwnProperty() 检测属性是来自于原型还是实例
person1.hasOwnProperty("name")  true为实例 false原型
#Object.keys 列出可枚举的属性  例如 Object.keys(Person.prototyoe)

#得到所有属性  枚举或非枚举 Object.getOwnPropertyNames()

createPerson.prototype.name="shanks"
createPerson.prototype.age=22
createPerson.prototype.sayname=function(){return this.name}
console.log(person1.constructor==createPerson) //true

createPerson.prototype={
	//constructor:createPerson //true 
	name:"shanks",
	age:22,
	sayname:function(){}
}
console.log(person1.constructor==createPerson) //false

PS:用字面量重写原型在调用后会报错


##原型链 PS弊端全都共享
function subs(){
	this.subsValue=false
}
subs.prototype.getsubs=function(){
	return this.subsValue
}

function supers(){
	this.supersValue=true
}
supers.prototype=new subs()
supers.prototype.getsupers=function(){
	return this.supersValue
}
supers.property=function(){return "shanks"}
instance=new supers()
console.log(instance.constructor)

PS：在subs里面添加属性也会变成原型属性，应为super.prototype实例化了，继承super将继承subs的原型属性



##借用构造函数 PS方法不能共享
function subs(){
	this.subsValue=false
	this.color=["red","green"]
}
subs.prototype.getsubs=function(){
	return this.subsValue
}

function supers(){
	this.supersValue=true
	subs.call(this) ******借用subs，继承修改this指向
}

supers.prototype.getsupers=function(){
	return this.supersValue
}
supers.property=function(){return "shanks"}
instance1=new supers()
instance1.color.push("black")
instance2=new supers()

console.log(instance1.color)
console.log(instance2.color)


##组合继承 (选择组合吧  更加容易理解)
function subs(){
	this.subsValue=false
	this.color=["red","green"]
}
subs.prototype.getsubs=function(){
	return this.color
}

function supers(){
	this.supersValue=true
	subs.call(this)
}
supers.prototype=new subs()
supers.prototype.getsupers=function(){
	return this.supersValue
}
supers.property=function(){return "shanks"}
instance1=new supers()
instance1.color.push("black")
instance2=new supers()

console.log(instance1 instanceof supers)
console.log(instance2.getsubs())

##Object.create()







##寄生组合继承
function object(o)
{
	function F(){}
	F.prototype=o
	return new F()
}


function inheritPrototype(subType,superType)
{
	var prototype=object(superType.prototype)
	prototype.constructor=subType
	subType.prototype=prototype
}

function SuperType(name){
	this.name=name
	this.colors=["red","black"]
}
SuperType.prototype.sayName=function(){
	alert(this.name)
}
function SubType(name,age){
	SuperType.call(this,name)
	this.age=age
}
inheritPrototype(SubType,SuperType)
SubType.prototype.sayAge=function(){
	alert(this.age)
}
