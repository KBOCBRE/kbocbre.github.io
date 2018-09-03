---
layout:     post
title:      jquery中$.ajax、$.get()、$.post()区别和联系
subtitle:   Ajax
date:       2018-9-3
author:     KBOCBRE
header-img: img/home-bg-o.jpg
catalog: true
tags:
    - Ajax
---


# 首先说一下这三者之间的关系
`$.get()和$.post()是$.ajax()在进行简单的get和post请求的简写形式`

**$.get()**的语法：
```
$(selector).get(url,data,success(response,status,xhr),dataType)
```
等价于：
```
$.ajax({
  url: url,
  data: data,
  success: success,
  dataType: dataType
});
```
```
    //$.get()请求是$.ajax()进行简单的get请求的一种简写方式
    //语法规则:  $(selector).get(url,data,success(response,status,xhr),dataType)
    //参数： 有四个参数，url参数是必须的，其他三个都是可选的
    //data： 参数类型两种（PlainObject，或者字符串）翻阅官方api发现js的json对象是PlainObject对象所以可以直接使用，
    //如果使用字符串请使用key=value&key=value这种形式"字段名=值&字段名=值"
    //由于get方法是将参数放在http请求的header里面所以参数是拼接在URL后面的
    //success：是参数类型是function
    //dataType： 预期希望服务器返回的数据类型
```
**例子**

前端请求：
```
   $(".btn3").click(function(){
    //GET:
    //
    //$.get()请求是$.ajax()进行简单的get请求的一种简写方式
    //语法规则:  $(selector).get(url,data,success(response,status,xhr),dataType)
    //参数： 有四个参数，url参数是必须的，其他三个都是可选的
    //data： 参数类型两种（PlainObject，或者字符串）翻阅官方api发现js的json对象是PlainObject对象所以可以直接使用，
    //如果使用字符串请使用key=value&key=value这种形式"字段名=值&字段名=值"
    //由于get方法是是将参数放在http请求的header里面所以参数是拼接在URL后面的
    //success：是参数类型是function
    //dataType： 预期希望服务器返回的数据类型
            $.get("/ajaxgetd","name=科比&age=18", function(data,status){
              alert("数据："+ data + "\n状态:" + status);
            });
        });
```
后端处理：
```
@app.route('/ajaxgetd', methods=['GET','POST'])
def ajaxgetd():
	info = request.args
	name = info["name"]
	age = info.get("age")
	print(info)
	print(age)
	if name == "科比":
		return "科比"
	return 'some strings'
```
**两种data数据类型请求方式**

```
$.get("/cldz",{"name":"科比"，"age":41},function(data,status){
	alert("数据："+data+"\n状态:" + satatus);
});

$.get("/cldz","name=科比&age=41",function(data,status){
	alert("数据："+data+"\n状态："+ status);
})；
```
