# HUGEMINI

## 项目描述

该项目是对Gemini提供的API创建的web服务，可以通过web界面来更方便地使用Gemini模型。

## 项目预览

![image-20240228085931761](./README/image-20240228085931761.png)

## 启动项目

```
flask run --host=0.0.0.0 --port=6666
```

## 命名规则

- python
    - 变量、函数：全小写+下划线命名法
    - 全局变量（Config）：全大写+下划线命名法
    - 类：大驼峰命名法
- html、js
	- class：全小写+破折号
	- 变量、函数、id：全小写+下划线命名法

## 接口描述

### website.py

- `/`
  methods：GET、POST
  function：index()
  功能：跳转去`/Chat`
- `/Chat`
  methods：GET、POST
  function：chat()
  功能：新建对话界面
- `/chat/<conversation_id>` （未使用）
  methods：GET、POST
  function：chat()
  功能：指定conversation_id的对话界面

### backend.py

- `/gemini/text`
  methods：POST
  function：text()
  功能：输入问题返回Gemini的回答
  POST参数：
  	`history`：消息历史（可以为空）
  	`question`：输入的问题
  返回的结果：
  
  ​	`code`: 状态码,
  
  ​	`result`: 返回结果
  
- `/gemini/version`
  methods：POST
  function：version()
  功能：输入图片和问题返回Gemini的回答
  POST参数：
  	`question`：输入的问题（可以为空）
  	`imgs`：输入的图片json格式，包含1-多张图片
  返回的结果：
  	`code`: 状态码,

  ​	`result`: 返回结果
  
- /models_name
  methods：GET
  function：models_name()
  功能：返回可使用的ai模型

