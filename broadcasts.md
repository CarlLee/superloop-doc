---
layout: page
title: 分享
permalink: /broadcasts.html
---

分享接口
========

|    接口名    | HTTP方法 |  权限  |                           URL                           |
| ------------ | -------- | ------ | ------------------------------------------------------- |
| 发布分享     | POST     | user   | [/broadcasts](#broadcasts-post)                         |
| 分享详情     | GET      | anyone | [/broadcasts/:id](#broadcasts-get)                      |
| 删除分享     | DELETE   | owner  | [/broadcasts/:id](#broadcasts-delete)                   |
| 查看点赞用户 | GET      | anyone | [/broadcasts/:id/thumbups](#broadcasts-thumbups-get)    |
| 分享点赞     | POST     | user   | [/broadcasts/:id/thumbups](#broadcasts-thumbups-post)   |
| 取消点赞     | DELETE   | user   | [/broadcasts/:id/thumbups](#broadcasts-thumbups-delete) |
| 评论分享     | POST     | user   | [/broadcasts/:id/comments](#broadcasts-comments-post)   |
| 查看评论     | GET      | anyone | [/broadcasts/:id/comments](#broadcasts-comments-get)    |
| 删除评论     | DELETE   | owner  | [/comments/:id](#comments-delete)            |
| 评论点赞     | POST     | user   | [/comments/:id/thumbups](#comments-thumbups-post)       |
| 取消评论点赞 | DELETE   | owner  | [/comments/:id/thumbups](#comments-thumbups-delete)     |

<a name="broadcasts-post"></a>

发布分享
-------

> 发布分享

#####URL

    POST /broadcasts

#####参数列表

|      参数名      |  必要 |  类型  |  长度 |        描述        |
| ---------------- | ----- | ------ | ----- | ------------------ |
| content          | true  | string | 1~600 | 分享内容           |
| attachement_urls | false | array  |       | 分享附件的URL数组  |
| attachment_types | false | array  |       | 分享附件的类型数组 |

#####返回值

    {
        "code" : 0,
        "msg" : "success"
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |

#####备注

- attachment_types可能的值为

    - image 图片
    - video 视频

- attachement_urls和attachement_types中元素按顺序一一对应

- 如果attachment_urls不为空 attachment_types为空或数量少于attachment_urls则按默认为image处理

<a name="broadcasts-get"></a>

分享详情
-------

> 获取分享详细信息

#####URL

    GET /broadcasts/:id

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 分享id |

#####返回值

    {
        "code" : 0,
        "msg" : "success",
        "result" : {
            "id" : 123456789,
            "user" : {
                "id" : 123456789,
                "gender" : 1,
                "avatar" : "http://s11.album.sina.com.cn/pic_3/4c543a9d020017zm",
                "location" : "北京市 朝阳区",
                "nickname" : "毛主席"
            },
            "content" : "今天天气不错",
            "attachments" : [{
                "id" : 123456789,
                "attachment_type" : "image",
                "attachment_url" : "http://s11.album.sina.com.cn/pic_3/4c543a9d020017zm"
            }],
            "created" : 1440569734957,
            "comments_cnt" : 567,
            "thumbups_cnt" : 700
        }
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |
| result | object | 响应内容 |

#####备注

<a name="broadcasts-delete"></a>

删除分享
-------

> 删除分享

#####URL

    DELETE /broadcasts/:id

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 分享id |

#####返回值

    {
        "code" : 0,
        "msg" : "success"
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |

#####备注

<a name="broadcasts-thumbups-get"></a>

查看点赞用户
-------

> 查看点赞用户

#####URL

    GET /broadcasts/:id/thumbups

#####参数列表

| 参数名 |  必要 | 类型 |  长度 | 默认值 |       描述       |
| ------ | ----- | ---- | ----- | ------ | ---------------- |
| :id    | true  | long | 64bit |        | 分享id           |
| pager  | false | int  | 32bit |     20 | 每页所含条目数量 |
| page   | false | int  | 32bit |      0 | 页码             |

#####返回值

    {
        "code" : 0,
        "msg" : "success",
        "result" : [{
            "id" : 123456789,
            "gender" : 1,
            "avatar" : "http://s11.album.sina.com.cn/pic_3/4c543a9d020017zm",
            "location" : "北京市 朝阳区",
            "nickname" : "毛主席"
        }]
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |
| result | array  | 响应内容 |

#####备注

<a name="broadcasts-thumbups-post"></a>

分享点赞
-------

> 给分享点赞

#####URL

    POST /broadcasts/:id/thumbups

#####参数列表

|     参数名     |  必要 |   类型  |  长度 | 默认值 |       描述       |
| -------------- | ----- | ------- | ----- | ------ | ---------------- |
| :id            | true  | long    | 64bit |        | 分享id           |

#####返回值

    {
        "code" : 0,
        "msg" : "success"
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |

#####备注

- 每个人对同一条分享只能点赞一次

<a name="broadcasts-thumbups-delete"></a>

取消点赞
-------

> 取消给分享点的赞

#####URL

    DELETE /broadcasts/:id/thumbups

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 分享id |

#####返回值

    {
        "code" : 0,
        "msg" : "success"
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |

#####备注

<a name="broadcasts-comments-post"></a>

评论分享
-------

> 评论分享

#####URL

    POST /broadcasts/:id/comments

#####参数列表

| 参数名  | 必要 |  类型  |  长度 |   描述   |
| ------- | ---- | ------ | ----- | -------- |
| :id     | true | long   | 64bit | 分享id   |
| content | true | string | 1~600 | 评论内容 |

#####返回值

    {
        "code" : 0,
        "msg" : "success"
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |

#####备注

<a name="broadcasts-comments-get"></a>

查看评论
-------

> 查看分享的评论

#####URL

    GET /broadcasts/:id/comments

#####参数列表

| 参数名 |  必要 | 类型 |  长度 | 默认值 |       描述       |
| ------ | ----- | ---- | ----- | ------ | ---------------- |
| :id    | true  | long | 64bit |        | 分享id           |
| pager  | false | int  | 32bit |     20 | 每页所含条目数量 |
| page   | false | int  | 32bit |      0 | 页码             |

#####返回值

    {
        "code" : 0,
        "msg" : "success",
        "result" : [{
            "id" : 123456789,
            "content" : "呵呵不错",
            "created" : 1440569734957,
            "user" : {
                "id" : 123456789,
                "gender" : 1,
                "avatar" : "http://s11.album.sina.com.cn/pic_3/4c543a9d020017zm",
                "location" : "北京市 朝阳区",
                "nickname" : "毛主席"
            }
        }]
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |
| result | array  | 响应内容 |

#####备注

<a name="comments-delete"></a>

删除评论
-------

> 删除评论

#####URL

    DELETE /comments/:id

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 评论id |

#####返回值

    {
        "code" : 0,
        "msg" : "success"
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |

#####备注

<a name="comments-thumbups-post"></a>

评论点赞
-------

> 给评论点赞

#####URL

    POST /comments/:id/thumbups

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 分享id |

#####返回值

    {
        "code" : 0,
        "msg" : "success"
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |

#####备注

- 每个人对同一条评论只能点赞一次

<a name="comments-thumbups-delete"></a>

取消评论点赞
-------

> 取消给评论点的赞

#####URL

    DELETE /comments/:id/thumbups

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 分享id |

#####返回值

    {
        "code" : 0,
        "msg" : "success"
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |

#####备注
