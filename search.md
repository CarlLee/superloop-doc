---
layout: page
title: 搜索
permalink: /search.html
---

搜索接口
=======

|  接口名  | HTTP方法 |  权限  |                   URL                    |
| -------- | -------- | ------ | ---------------------------------------- |
| 搜索用户 | GET      | anyone | [/search/users](#search-users)           |
| 搜索分享 | GET      | anyone | [/search/broadcasts](#search-broadcasts) |
| 搜索话题 | GET      | anyone | [/search/topics](#search-topics)         |


<a name="search-users"></a>

搜索用户
-------

> 搜索用户

#####URL

    GET /search/users

#####参数列表

|   参数名    |  必要 |  类型  |  长度 |    描述    |
| ----------- | ----- | ------ | ----- | ---------- |
| text        | true  | string |       | 搜索关键字 |
| location_id | false | long   | 64bit | 地点id     |
| category_id | false | long   | 64bit | 分类id     |
| order       | false | string |       | 排序方式   |

#####返回值

    {
        "code" : 0,
        "msg" : "success",
        "result" : [{
            "id" : 123456789,
            "gender" : 1,
            "avatar" : "http://s11.album.sina.com.cn/pic_3/4c543a9d020017zm",
            "cellphone" : "13800138000",
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

- 参见[排序方式格式](index.html#order-format)


<a name="search-broadcasts"></a>

搜索分享
-------

> 搜索分享

#####URL

    GET /search/broadcasts

#####参数列表

|   参数名    |  必要 |  类型  |  长度 |    描述    |
| ----------- | ----- | ------ | ----- | ---------- |
| text        | true  | string |       | 搜索关键字 |
| category_id | false | long   | 64bit | 分类id     |
| order       | false | string |       | 排序方式   |

#####返回值

    {
        "code" : 0,
        "msg" : "success",
        "result" : [{
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
        }]
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |

#####备注

- 参见[排序方式格式](index.html#order-format)


<a name="search-topics"></a>

搜索话题
-------

> 搜索话题

#####URL

    GET /search/topics

#####参数列表

|   参数名    |  必要 |  类型  |  长度 |    描述    |
| ----------- | ----- | ------ | ----- | ---------- |
| text        | true  | string |       | 搜索关键字 |
| category_id | false | long   | 64bit | 分类id     |
| order       | false | string |       | 排序方式   |

#####返回值

    {
        "code" : 0,
        "msg" : "success",
        "result" : [{
            "id" : 123456789,
            "user" : {
                "id" : 123456789,
                "gender" : 1,
                "avatar" : "http://s11.album.sina.com.cn/pic_3/4c543a9d020017zm",
                "location" : "北京市 朝阳区",
                "nickname" : "王二小"
            },
            "title" : "请问羊一天放养多少小时合适？？",
            "content" : "一天几小时才是合理的",
            "created" : 1440569734957,
            "views" : 567,
            "replies_cnt" : 200,
            "thumbups_cnt" : 700
        }]
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |

#####备注

- 参见[排序方式格式](index.html#order-format)
