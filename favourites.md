---
layout: page
title: 收藏
permalink: /favourites.html
---

收藏接口
========

###收藏接口

|     接口名     | HTTP方法 | 权限 |                          URL                          |
| -------------- | -------- | ---- | ----------------------------------------------------- |
| 收藏分享       | POST     | user | [/favourites/broadcasts](#favourites-broadcasts-post) |
| 获取收藏的分享 | GET      | user | [/favourites/broadcasts](#favourites-broadcasts-get)  |
| 收藏话题       | POST     | user | [/favourites/topics](#favourites-topics-post)         |
| 获取收藏的话题 | GET      | user | [/favourites/topics](#favourties-topics-get)          |

<a name="favourites-broadcasts-post"></a>

收藏分享
-------

> 收藏分享

#####URL

    POST /favourites/broadcasts

#####参数列表

|    参数名    | 必要 | 类型 |  长度 |  描述  |
| ------------ | ---- | ---- | ----- | ------ |
| broadcast_id | true | long | 64bit | 分享id |

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

<a name="favourites-broadcasts-get"></a>

获取收藏的分享
-------------

> 获取收藏的分享

#####URL

    GET /favourites/broadcasts

#####参数列表

| 参数名 |  必要 | 类型 |  长度 | 默认值 |       描述       |
| ------ | ----- | ---- | ----- | ------ | ---------------- |
| pager  | false | int  | 32bit |     20 | 每页所含条目数量 |
| page   | false | int  | 32bit |      0 | 页码             |

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

<a name="favourites-topics-post"></a>

收藏话题
-------

> 收藏话题

#####URL

    POST /favourites/topics

#####参数列表

|  参数名  | 必要 | 类型 |  长度 |  描述  |
| -------- | ---- | ---- | ----- | ------ |
| topic_id | true | long | 64bit | 话题id |

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

<a name="favourites-topics-get"></a>

获取收藏的话题
-------

> 获取收藏的话题

#####URL

    GET /favourites/topics

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |

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
                "nickname" : "王二小"
            },
            "title" : "请问羊一天放养多少小时合适？？",
            "content" : "一天几小时才是合理的",
            "created" : 1440569734957,
            "views" : 567,
            "replies_cnt" : 200,
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
