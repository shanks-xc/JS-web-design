#javascript高级程序设计第七章(函数表达式)
****以后再回来看
生命函数有2仲方法:
函数声明:function person(){} 函数声明提升
函数表达式: var person=function(){}函数调用在声明前报错

递归:不断调用自身的函数
function add(num){
	if(num<=1)
	{
		return 1
	}
	return num * arguments.callee(num-1) 
}//arguments.callee不断调用自身
console.log(add(5))



##闭包 过度使用会消耗内存,是指有权访问另一个函数作用域中的变量的函数
var data=[{age:20,name:"shanks"},{age:19,name:"abc"}]
var end=data.sort(compare("age"))
function compare(name)
{
	return function(obj,obj2)
	{
		var value1=obj[name]
		var value2=obj2[name]
		return value1-value2
	}
	
}

console.log(end[0].name)


##this指向问题


##模拟块级作用域
function number(){
	(function(){for (var i = 0; i < 10; i++) {
		console.log(i)
	}})()
	var i
	console.log(i)
}number()

##私有变量
function person(){
	this.get=function(){
	console.log("get")
   }
}  //调用 person.get()



