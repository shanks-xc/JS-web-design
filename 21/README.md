#javascript高级程序设计第二十一章(XMLHttpRequest)


##用XHR  XMLHttpRequest
1.先创建xhr对象 var  xhr=new XMLHttpRequest()
2.xhr.open(发送类型,url,false)是否异步
xhr.open("GET",url,true)
*xhr.setRequestHeader("","")请求中 open跟send之间
3.xhr.send(null)
4.onreadystatechange事件判断响应过程
xhr.onreadystatechange=function(){
		if(xhr.readyState==4) //表示响应过程
		{
			if(xhr.status==200)//http状态码
			{
				console.log(xhr.responseText)
			}
		}
	}
xhr.getResponseHeaders()取得头部信息
xhr.getAllResponseHeaders()取得头部所有信息


##GET  是常见的类型，最常用于向服务器查询某些。必要时，可以将查询字符窜追加到URL的末尾
get请求数据和添加参数
var  xhr=new XMLHttpRequest()|| new ActiveXObject("Microsoft.XMLHTTP")
	//在get后面添加参数
	function addURLparse(url,name,value)
	{
		url+=url.indexOf("?")==-1 ?"?":"&"
		url+=encodeURIComponent(name)+"="+encodeURIComponent(value)
		return url

	}
	var url="name.json"
	url=addURLparse(url,"name","shanks")
	url=addURLparse(url,"name2","shanks2")
	xhr.open("GET",url,true) //异步
	xhr.send()
	xhr.onreadystatechange=function(){
		if(xhr.readyState==4) //表示响应过程
		{
			if(xhr.status==200)//http状态码
			{
				console.log(xhr.responseText)
				console.log(xhr.getAllResponseHeaders())
			}
		}
	}


##POST向服务器发送应该被保存的数据。POST请求应该把数据作为请求的主体提交
**服务器对 POST 请求和提交 Web 表单的请求并不会一视同仁。因此，服务器端必须有
程序来读取发送过来的原始数据，并从中解析出有用的部分。
function submitData(){
var xhr = createXHR();
xhr.onreadystatechange = function(){
if (xhr.readyState == 4){
if ((xhr.status >= 200 && xhr.status < 300) || xhr.status == 304){
alert(xhr.responseText);
} else {
alert("Request was unsuccessful: " + xhr.status);
}
}
};
xhr.open("post", "postexample.php", true);
xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
var form = document.getElementById("user-info");
xhr.send(serialize(form));
}


##post请求
http://www.cnblogs.com/aaronjs/p/4165049.html


##FormData
免去序列化和POST请求头
new FromData(form)

##超时设定
xhr.timeout=1000
xhr.ontimeout=function(){}


##同源跨域
1.CORS修改服务端代码, header("Access-Control-Allow-Origin: *");
*默认所有域名都可以请求   
PS建议针对某些域名进行获得跨域权限
2.JSONP跨域
我们都知道script标签可以链接其他不同域名的js文件，
jsonp正是利用这个原理
定义一个函数处理jsonp信息
html页面代码
jsopn(result){
	console.log(result)
}
<script src="xxxx.com?callback=jsopn"></script>

服务端代码php:
 <?php
//服务端返回JSON数据  
$arr=array('a'=>1,'b'=>2,'c'=>3,'d'=>4,'e'=>5);  
$result=json_encode($arr);  
//echo $_GET['callback'].'("Hello,World!")';  
//echo $_GET['callback']."($result)";  
//动态执行回调函数  
$callback=$_GET['callback'];  
echo $callback."($result)";  
 ?>


服务端会返回一段执行函数
jsonp(result)  jspon正是我们传递过去的函数
 












