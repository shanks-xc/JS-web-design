#javascript高级程序设计第十章(DOM)


nodeType检测  1是元素
someNode.childNodes[0]||someNode.childNodes.item(0)
第一个子节点
appendChild()在最后插入节点 一般只是文本
var textnode=document.createTextNode("<ul>Water</ul>")
insertBefore(插入文本，节点位置) 节点位置要someNode.firstChild
replaceChild(要插入的节点和要替换的节点)
removeChild(要移除的节点)
cloneNode()克隆节点
normalize()


##document类型
document只有一个节点
document.documentElement==document.firstChild
document.body=body节点
document.documentElement=html节点

document.getElementById(元素ID)
document.getElementsByTagName(取得元素)返回数组
document.getElementsByName()
write() writeln() open() close()

#Element类型 nodeType为1
div=document.getElementById("div")
div.title div.className div.id

##取得特性
getAttribute()  setAttribute()  removeAttribute()

##创建元素
document.createElement()

#动态添加脚本文件
var script=document.createElement("script")
script.type="text/javascript"
script.src="client.js"
document.body.appendChild(script)