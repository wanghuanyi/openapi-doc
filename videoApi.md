#片库系统OpenApi

    1. 该接口适用对象：
	   对接新片场视频，接入片库系统，使公司对外视频的统一性
    2. 该接口实现功能：
       [视频录入] 
        > 第三方视频
	    > 可直接使用的视频资源
	   [视频处理]
	    > 视频抓取
		> 根据profile进行视频格式的处理
	   [视频信息]
	    > 视频基础属性
		> 处理后资源的获取
    3. 该接口调用规范：
	   采用REST规范的HTTP请求
    4. 该接口调用权限：
	   暂未对资源独立控制，后续可支持access_token,ip白名单方式
	
------
>注：
>   名词说明：
>	    视频：包含第三方平台的视频以及上传的视频
>	    资源：对视频进行处理后对外的可用mp4,flv,m3u8等格式
>>PS: 该API仍处于 `Beta` 阶段

------
+ 系统功能思维导图

![](http://oiky1wrat.bkt.clouddn.com/video-library.svg)
##通用说明
+ 域名

    开发环境： cms.vmovier.cc
    测试环境： openapi.vmovier.com
    生成环境： 
    

+ 参数说明

字段名     | 格式     | 默认值     | 备注
-------- | --- | --- | ---  |
per_page | int | 20 | 每页数据 |
page     | int | 1  | 当前页码 |

+ 返回参数说明

1\. 返回格式

    json
2\. 字段说明

字段名     | 类型     | 备注     | 
-------- | --- | --- | 
errCode | int | 错误码，0-返回成功 <>0-获取数据失败 |
msg | string | 错误提示（success为返回成功）|
data | Array | 请求数据 |
3\. 响应Header
请求 Method 不被支持的情况下
    
    HTTP/1.1 405 Method Not Allowed
请求 URL 不存在
    
    HTTP/1.1 404 Not Found
##接口说明
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

参数名     | 类型     | 是否必填     | 描述
-------- | --- | ---| ---
per_page | int | 否 | 一次请求多少条数据
page | int | 否 | 获取第几页数据 |

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
per_page | int | 否 | 一次请求多少条数据
page | int | 否 | 获取第几页数据 |

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
### 获取视频信息
+ 接口地址
```
/api/video/getVideoInfo/{vid}
```
+ 请求方式
```
GET
```
+ 请求参数

参数名     | 类型     | 是否必填     | 描述 |
-------- | --- | --- | --- |
vid | int | 是 | 获取vid对应的视频信息 |

+ 返回结果
```json
{
    "status": 0,
    "msg": "success",
    "data": {
        "vid": "5886ec43958d4",
        "video": {
            "source_type": 1,
            "source_link": "http://v.youku.com/v_show/id_XMTQ5Mzg5MzgxNg==.html",
            "title": "我是梅西，所以我不能倒下！",
            "cover": "http://cs.vmoiver.com/Uploads/avatar/2017/01/19/de91eb6b0d1da1b61d3dfed879966d77.jpeg",
            "regisseur": "",
            "filmmaking": "",
            "duration": 84,
            "preview_image_path": "",
            "preview_video_path": "",
            "score": 1,
            "origin_title": "",
            "origin_website_link": "",
            "origin_resource_link": "",
            "subtitles_link": "",
            "property": "1,"
        },
        "resource": {
            "hls": [],
            "progressive": [
                {
                    "id": 100,
                    "profile": 164,
                    "bucket": "com-video",
                    "key": "5886d150b34a7.mp4",
                    "sha1": "b05cc07832d9be03ed7fbde79a968a0f3d68ee75",
                    "md5": "9436f98b08a3927d482e2210a4c13f69",
                    "filesize": 4620063,
                    "duration": 53290,
                    "video_bitrate": 693572,
                    "video_codec_name": "h264",
                    "width": 202,
                    "height": 360,
                    "coded_width": 208,
                    "coded_height": 368,
                    "sample_aspect_ratio": "7200:7171",
                    "display_aspect_ratio": "40:71"
                },
                {
                    "id": 100,
                    "profile": 164,
                    "bucket": "com-video",
                    "key": "5886d150b34a7.mp4",
                    "sha1": "b05cc07832d9be03ed7fbde79a968a0f3d68ee75",
                    "md5": "9436f98b08a3927d482e2210a4c13f69",
                    "filesize": 4620063,
                    "duration": 53290,
                    "video_bitrate": 693572,
                    "video_codec_name": "h264",
                    "width": 202,
                    "height": 360,
                    "coded_width": 208,
                    "coded_height": 368,
                    "sample_aspect_ratio": "7200:7171",
                    "display_aspect_ratio": "40:71"
                }
            ]
        }
    }
}
```
### 上传视频
+ 接口地址
```
/api/video/saveVideo
```
+ 请求方式
```
POST
```
+ 请求参数

参数名     | 类型     | 是否必填     | 默认值     | 描述     |
-------- | --- | --- | --- |
source_type | int       | 否 | 0 | 视频源类型 0-外链 1-mp4 |
source_link | string    | 是 |  | 视频源地址（url） |
title       | string    | 否 |  | 标题，没有填写标题程序会自动抓取 |
cover       | string    | 是 |  | 封面图 |
duration    | int       | 是 |  | 视频时长 单位 毫秒 |
score       | int       | 是 |  | 影片平均分，100分制度，可多人打分 |
property    | string    | 否 | 1 | 视频处理属性 1-mp4 2-m3u8，填写多个属性用“,”隔开，例如：1,2 |
regisseur   | string    | 否 |  | 导演 |
filmmaking  | string    | 否 |  | 制片人 |
extend      | json      | 否 |  | 扩展信息，例： [{"origin_title":"影片标题","origin_website_link":"原视频网站地址","origin_resource_link":"无字幕原片地址","subtitles_link":"字幕文件地址","preview_image_path":"视频预览图地址，8*8视频截图，合并图","preview_video_path":"预览视频地址"}]|

+ 返回结果
```json
{
    "errCode": 0,
    "msg": "success",
    "data": []
}
```
