#javascript高级程序设计第十二章(DOM拓展)
document.querySelector(css)
document.querySelectorAll(css)返回数组
document.body.matchesSelector(css)
document.getElementsByClassName(className)

##className操作
document.getElementById.classList.add()添加类
document.getElementById.classList.remove()删除类别
document.getElementById.classList.toggle()切换类别
document.getElementById.classList.contains()是否有次类别


##焦点管理
document.hasFocus()  PS有待完善

readyState
document.readyState=="loading"||"complete"
标准模式:document.compatMode 


##data自定义数据属性
element.dataset.XXXX

#插入标志 
element.innerHTML  可以输入html格式，返回文本
element.outerHTML  返回它的元素以及所有子节点
element.insertAdjacentHTML(位置,插入内容)
位置:beforebegin afterbegin beforeend afterend

#访问元素样式
element.style.background="red"


