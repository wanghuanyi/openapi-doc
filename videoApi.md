#片库系统OpenApi

##接口说明
+ 域名
```
开发环境： cms.vmovier.cc
测试环境： openapi.vmovier.com
生成环境： 
```
+ 参数说明

字段名     | 格式     | 默认值     | 备注
-------- | --- | --- | --- 
per_page | int | 20 | 每页数据
page     | int | 1  | 当前页数

+ 返回参数说明
1. 返回格式
```
json
```
2. 字段说明

字段名     | 类型     | 备注
-------- | --- | ---
errCode | int | 错误码，0-返回成功 <>0-获取数据失败
msg | string | 错误提示（success为返回成功）
data | Array | 请求数据
### 获取标签列表
+ 接口地址
```
/api/video/tag
```
+ 请求方式
```
GET
```
+ 请求参数
```
无
```

+ 返回结果
```json
{
    "errCode": 0,
    "msg": "success",
    "data": {
         "total": 11,
         "items": [{
                 "id": 2,
                 "tag_name": "悬疑",
                 "count_video": 0
             },
             {
                 "id": 3,
                 "tag_name": "喜剧",
                 "count_video": 0
             }]
    }
}
```
### 获取分类
+ 接口地址
```
/api/video/category
```
+ 请求方式
```
GET
```
+ 请求参数

参数名     | 类型     | 是否必填     | 描述
-------- | --- | ---| ---
pid | int | 否 | 获取分类id下的二级分类

+ 返回结果
```json
{
    "errCode": 0,
    "msg": "success",
    "data": [{
        "id": 1,
        "category_name": "战争",
        "count_video": 0,
        "child": [{
            "id": 4,
            "category_name": "抗日",
            "count_video": 0
        }]
    }]
}
```