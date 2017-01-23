#Video Open Api

##接口说明
+ 域名
```
开发环境： cms.vmovier.cc
测试环境： openapi.vmovier.com
生成环境： 
```
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
```
无
```

+ 返回结果
```json