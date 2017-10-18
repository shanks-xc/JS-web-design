#javascript高级程序设计第五章(引 用 类 型)
创建对象的两种方法:
var person={name:"shanks"}  var person=new Object() person.name="shanks" 字面量表示


5.2  Array 类型
创建数组的两种方法:
var colors = new Array()
var colors = ["red", "blue", "green"] 字面量表示
检测是不是数组的两个方法:
instanceof array instanceof Array  trut:为数组
Array.isArray(value)

toLocaleString(),toString(),valueOf()都可以返回字符窜但是都以逗号分隔



join()将数组返回字符窜，传参表示用参数分隔 如join("||") red||blue
push()数组添加至后一项
pop()移出最后一项并取出最后一项
shift()移出第一项并取出第一项
unshift()往数组前面添加一项


重排序方法:
 reverse() 大到小 和 sort(fn)小到大 可传参
 小于函数function compare(value1,value2)
{
	if(value1<value2)
	{
		return -1
	}
	else if(value1>value2)
	{
		return 1
	}
	else{
		return 0
	}
}
简便方法
function compare(value1, value2){
return value1 - value2;
}
concat()连接两个数组并返回新的数组
slice(start,end)返回新的数组   传参起始跟结束项 PS:传入是负数的话后最后一项开始数
splice 最强大的数组方法
删除 splice(0,2)0表示起始位置  2表示要删除的项
插入 splice(2,0,"red","blue") 从索引为2删除数为0插入red和blue

位置方法indexOf()从前面开始数 lastIndexOf()从后面开始数

迭代方法:
every() ：只要有一项是false就false
对数组中的每一项运行给定函数，如果该函数对每一项都返回 true ，则返回 true 。
filter() ：过滤
对数组中的每一项运行给定函数，返回该函数会返回 true 的项组成的数组。
forEach() ：循环执行函数,类似于for
对数组中的每一项运行给定函数。这个方法没有返回值。
map() 循环返回新的数组 :对数组中的每一项运行给定函数，返回每次函数调用的结果组成的数组。
some() ： 只要有一项是true的就true
对数组中的每一项运行给定函数，如果该函数对任一项返回 true ，则返回 true 。


 reduce() 和 reduceRight()
 迭代所有数组项，构建最终一个返回
 传参4个，pre,cur,index,array上一个值，当前值，索引，当前数组本身
 应用场景 求和 求积






5.3 Date类型
Date.parse() 方法接收一个表示日期的字符串参数
Date.UTC() 方法同样也返回表示日期的毫秒数
两个传参的格式不同



5.3.2 日期格式化方法
Date 类型还有一些专门用于将日期格式化为字符串的方法，这些方法如下。
toDateString() ——以特定于实现的格式显示星期几、月、日和年；
toTimeString() ——以特定于实现的格式显示时、分、秒和时区；
toLocaleDateString() ——以特定于地区的格式显示星期几、月、日和年；
toLocaleTimeString() ——以特定于实现的格式显示时、分、秒；
toUTCString() ——以特定于实现的格式完整的 UTC 日期。



##5.4正则
var parttern=/[bc]at/i
var parttern=new RegExp("[bc]at","i")
实例 parttern.test("bat")返回布尔值
parttern.exec()


##5.5函数 
1.函数表达式
var sum=function(value,value2){return value+value2}
2.函数声明表达式(加载提前，可在它前面调用)
function sum(value,value2){}

arguments.callee  表示自身函数
inner.caller==arguments.callee.caller  当前自身

修改作用域
apply(传arguments或者数组)
call(传准确参数)
bind(绑定，传参)


函数分隔方法
splice() //数组
substr(start,length)可传负数
substring(start,end) end为绝对值
slice(start,end) end可为负数





##number
以下三个方法都是向上向下舍入
toFixed(返回小数位数)
toExponential(e表示法)
toPrecision()


##
charCodeAt(数字)返回当前数字位置的字符编码
charAt(数字)返回当前数字位置的字符
concat()可连接字符窜或者数组
indexOf() indexLastOf()字符窜位置
trim()格式化前后空格
trimLeft()前面空格  trimRight()后面空格
转大小写
toLocaleUpperCase() toUpperCase() =>转为大写
toLocaleLowerCase() toLowerCase() =>转为小写
匹配字符窜 match search replace()替换
split()分隔符  转为数组
localeCompare() -1之前 1之后 0等于
String.fromCharCode()将字符窜编码转为字符窜 与charCodeAt(相反)
Global对象方法:isNaN(), isFinite(),parseInt(),parseFloat()
URI编码方法:
encodeURI()编码encodeURIComponent()解码
decodeURI()编码decodeURIComponent()解码

eval()最强大的方法 ESMAscript解析器



###Math对象的方法
Math.max()求最大值   Math.min()求最小值
数组求最大
var  num=[1,5,2,65464,6131,1684,646,5456]
console.log(Math.max.apply(Math,num))
四舍五入：Math.ceil(向上取整) Math.floor(想下取整) 
Math.round(四舍五入) 
Math.random()随机取整
function select(lowerValue,upperValue){
	var choices=upperValue-lowerValue+1
	var random=Math.floor(Math.random()*choices+lowerValue)
	if(random==upperValue)
	{
			alert(upperValue)
	} 
	console.log(random)
}