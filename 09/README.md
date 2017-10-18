#javascript高级程序设计第八章(BOM)
window
innerWidth  innerHeight 页面视图大小 PS值根据视口变化
outerWidth  outerHeight 视口大小 PS不变的值
##移动设备
document.body.clientWidth document.body.clientHeight

打开新页面
window.open("http://www.shanks.top/","_blank","width=400")

setInterval() clearInterval()
setTimeout() clearTimeout()


alert()  	confirm()   prompt()



##location是BOM最有用的对象之一

##将url后面的参数转为对象
//将url后面的参数转为对象
var obj={}
name=null
age=null
var parse=location.search.substring(1).split("&")
parse.forEach(function(item,index){
	var newItem=item.split("=")
	for(var i=0;i<newItem.length;i++)
	{
			 name=newItem[0]
			 age=newItem[1]
			obj[name]=age
			return obj
	}	
})
console.log(obj)

window.location=url location.href=url 改变浏览器位置

replace可以禁止后退
location.reload()//重新加载(有可能从缓存中加载)
location.reload(true)//从服务器会从新加载



##navigator对象
//检查是否有这个插件
function hasPlugin(name)
{
	name=name.toLowerCase()
	var plugins=navigator.plugins
	
	for (var i = 0; i < plugins.length; i++) {
		if(plugins[i].name.toLowerCase().indexOf(name)>-1)
			{return true}
		else{
			return false
		}
	}
}

**screen  注册处理程序  先省略

##history对象
history.go() -1后退 1前进1页 2前进2页
history.back()后退  history.forward()前进