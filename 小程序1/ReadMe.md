##小程序
1.简单，用完即走
2.低频应用
3.性能要求不高

例如  猫眼电影   饿了么    滴滴打车


##小程序启动页面
app.js app.wxss app.json 全部配置 控制着整个页面
##配置路径
在app.json
pages：[
	"page/index/index"数组第一项为启动项
]


文件夹里面的 wxml wxss js json必须保持一致

view为容器大小   text为字体标签   
rpx是微信自适应标签
建议用I6  因为i6下1px=1rpx  i6 plus下 1px=0.6rpx


##新闻阅读列表
准备工作
1.事件与事件对象
2.缓存
3.列表渲染(核心)
4.Template模板的使用


##新闻阅读列表  第4章
flex布局
wx:if={{}}控制显示隐藏
{{}}填写date数据
Page()里面有生命周期的模板
？如何遍历数据  怎么拿到后端数据

wx:for={{xx}}  wx:for-item="item" 默认 指定循环    [{name."shanks"}]  item.name 
索引   wx:for-index="index"默认、

跳转链接
wx.navigateTo({    //onHide执行
	url:"../posts/post"  //子父关系   没返回   最多限制5级
})
wx.redirectTo({      //onUnload执行
	url:"../posts/post"  //平行关系
})

bindtap 与catchtap的区别  catch默认阻止冒泡行为

##数据绑定
在page里面的js代码   data数据里面绑定数据
例如data{
	name:"shanks"
}应用 {{name}}
传递一个数组的时候要重新设置
this.setData({xxx:数组})

循环：
wx:for="{{postList}}" wx:for-item="item" wx:key="unique"



##第五章
//Alt+shift+F  格式化
可以用require  node机制去获取模块JS

吐出
module.exports = {
    postList: local_database
}

var post_datas=require("../../data/posts-data.js")
this.setData({postList:post_datas.postList})



<template name="post"></template>//创建模板
<import src="./post-item-template/post-item-template.wxml"/>引用模板
<template  is="post" data="{{item}}"/>使用模板  //data引用数据
例如:
<block wx:for="{{postList}}" wx:for-item="item" wx:key="unique">
   <template  is="post" data="{{item}}"/>   {{...item}}展开对象  template里面item.date就可以写成date
</block>