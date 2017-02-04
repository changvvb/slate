---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

欢迎来到job api 文档中心, 关于这次高端兼职项目的api我将在这里发布,大家加油! 一起努力!!

# Authentication

说明:认证过程, 大部分api请求是要认证的,当使用电话和密码请求后将获得一个cookie,此cookie便是其它请求的凭证.

> To authorize, use this code:

### HTTP Request

`GET http://127.0.0.1/api/auth?tel=<TEL>&password=<PASS>&role=<ROLE>`

Parameter | Description
--------- | -----------
TEL | 注册时的电话
PASS | 密码
ROLE | jobseeker OR company


```shell
# 返回一个cookie,下次请求请务必带上此cookie
curl "http://127.0.0.1/api/auth?tel=xxxx&password=xxxx&role=xxx"
```

api authorize 目前采用GET请求, 此请求成功后状态码为200, 并返回个人数据和一个cookie作为下次请求的凭证,

<aside class="notice">
请记下cookie
</aside>


# Jobseekers

说明:找工作的角色

## 添加一个jobseeker



>添加jobseeker请求的body如下

```json
{
    "name":"name",
    "sex":0,
    "tel":"1234567890",
    "password":"password",
    "resume":"简历",
    "parttime":false
}
```

### HTTP Request

`POST http://127.0.0.1/api/addjobseeker`

请将请求的json数据放到body里,

Parameter | Description
--------- | -----------
name|姓名
sex|姓别 0 OR 1
tel|电话
password|登陆验证的密码
resume|简历
parttime|是否兼职

## 通过ID获得一个Jobseeker

### HTTP Request

`GET http://domain/api/getjobseeker?id=<ID>`

Parameter | Description
--------- | -----------
ID|Jobseekers的ID

# Company

说明:作为公司提供工作岗位的角色

## 添加一个Company

>添加company请求的body如下

```json
{
    "name":"name",
    "tel":"1234567890",
    "password":"password",
    "city":"Tianjin",
    "address":"bin han xin qu",
    "type":"IT"
}
```

### HTTP Request

`POST http://127.0.0.1/api/addcompany`

请将请求的json数据放到body里.

Parameter | Description
--------- | -----------
name|公司名称
tel|电话
password|登陆验证的密码
city|所在城市,
address|公司地址,
type|公司类型

## 通过ID获得一个Company

### HTTP Request

`GET http://domain/api/getcompany?id=<ID>`

Parameter | Description
--------- | -----------
ID|Company的ID

# Job

说明:工作岗位

## 添加一个Job

>添加job请求的body如下

```json
{
    "name":"changvvb",
    "salaryex":0,
    "parttime":false,
    "jobtype":"tester",
    "companyid":2
}
```


### HTTP Request
`POST http://domain/api/addjob`

请将请求的json数据放到body里.

Parameter | Description
--------- | -----------
name|工作职位名称
salary|工资
parttime|是否是兼职工作
jobtype|工作类型
companyid|所属公司的ID

# Application

说明:发布的工作申请

## 添加一个Application

>添加application请求的body如下

```json
{
    "salaryex":10000,
    "positionex":"programer",
    "jobseekerid":2
}
```


### HTTP Request
`POST http://domain/api/addapplication`

请将请求的json数据放到body里.

Parameter | Description
--------- | -----------
salaryex|期望工资
positionex|期望职务
jobseekerid|Jobseeker的ID
