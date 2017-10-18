#javascript高级程序设计第十三章(事件)


##事件流
IE的事件流是事件冒泡流，有些是事件捕获流

事件冒泡
div=>document
return event.stopPropagation();阻止事件网上冒泡。
return event.preventDefault();阻止默认行为。
事件捕获
document=>div

先捕获再到冒泡


##事件处理程序
addEventListener(事件名，处理函数，布尔值)
匿名函数不能移除
removeEventListener() 
**监听事件没有on  如click不是onclick 
attachEvent() detachEvent() 作用域this指向window

##DOM事件中的对象
event.stopPropagation();阻止事件网上冒泡。
event.preventDefault();阻止默认行为。
event.target  事件目标


##UI事件
load:页面加载  触发在windows
unload:页面卸载后  触发在windows
error：js报错时   触发在windows
select: Input 选择事件
resize:窗口或者框架大小的变化在 widnows触发
scroll：滚动事件  body上  ps:window也行，亲测
EventUtil.addHandle(window,"load",funciton(){
	alert("this is a load")
})

##焦点事件
blur:失去焦点的时候触发的事件
focus:获得焦点的时候触发的事件


##鼠标与滚轮事件
click:单击事件**
dbclick:双击事件
mousedown:鼠标按下事件
mouseenter:鼠标进入某个区域触发的事件
mouseleave:鼠标离开某个区域的事件**
mousemove:鼠标在元素内部移动的事件**
mouseout:在鼠标离开吧，将其移入另外元素时候的触发
mouseover:首次进入**
mouseup:鼠标在元素内释放时



##客户区坐标位置
鼠标位置信息保存在clientX和clientY上面 视口
pageX和pageY非视口  代表光标在页面中的位置而不是所见区域
在没有滚动的情况下page=client page>client
screenX和screenY相对于电脑屏幕的位置就是说获取的是电脑的位置而不是网页的位置或者视口大小


##修改健
event.(shift,ctrl,alt,,meta)Key
检查这几个属性可以检测是否按了这几个按键


##键盘与文本事件
keydown:键盘按下事件
keyup:释放键盘触发
keyCode:键码   键码13为回车

##readystatechange事件
uninitialized:未初始化
loading:正在加载
loaded:加载完毕
interactive:可以操作对象
complete:对象已经加载完毕


##事件委托



