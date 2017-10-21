#javascript高级程序设计第二十三章(数据存储)


##Cookie,最初是在客户端用于存储会话信息的。该标准要求服务器对
任意 HTTP 请求发送 Set-Cookie HTTP 头作为响应的一部分，其中包含会话信息

var CookieUtil = {
get: function (name){
var cookieName = encodeURIComponent(name) + "=",
cookieStart = document.cookie.indexOf(cookieName),
cookieValue = null;
if (cookieStart > -1){
var cookieEnd = document.cookie.indexOf(";", cookieStart);
if (cookieEnd == -1){
cookieEnd = document.cookie.length;
}
cookieValue = decodeURIComponent(document.cookie.substring(cookieStart
+ cookieName.length, cookieEnd));
}
return cookieValue;
},
set: function (name, value, expires, path, domain, secure) {
var cookieText = encodeURIComponent(name) + "=" +
encodeURIComponent(value);
if (expires instanceof Date) {
cookieText += "; expires=" + expires.toGMTString();
}
if (path) {
cookieText += "; path=" + path;
}
if (domain) {
cookieText += "; domain=" + domain;
}
if (secure) {
cookieText += "; secure";
}
document.cookie = cookieText;
},
unset: function (name, path, domain, secure){
this.set(name, "", new Date(0), path, domain, secure);
}
};

//设置 cookie
CookieUtil.set("name", "Nicholas");
CookieUtil.set("book", "Professional JavaScript");
//读取 cookie 的值
alert(CookieUtil.get("name")); //"Nicholas"
alert(CookieUtil.get("book")); //"Professional JavaScript"
//删除 cookie
CookieUtil.unset("name");
CookieUtil.unset("book");



#sessionStorage 对象
sessionStorage 对象存储特定于某个会话的数据，也就是该数据只保持到浏览器关闭。这个对象
就像会话 cookie，也会在浏览器关闭后消失。存储在 sessionStorage 中的数据可以跨越页面刷新而
存在，同时如果浏览器支持，浏览器崩溃并重启之后依然可用（Firefox 和 WebKit 都支持，IE 则不行）。
sessionStorage.setItem("name", "Nicholas");


#localStorage取代globalStorage
localStorage 对象在修订过的 HTML 5 规范中作为持久保存客户端数据的方案取代了
globalStorage 。
//使用方法存储数据
localStorage.setItem("name", "Nicholas");
//使用属性存储数据
localStorage.book = "Professional JavaScript";
//使用方法读取数据
var name = localStorage.getItem("name");
//使用属性读取数据
var book = localStorage.book;










