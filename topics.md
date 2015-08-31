---
layout: page
title: 话题
permalink: /topics.html
---

话题接口
========

|    接口名    | HTTP方法 |  权限  |                        URL                        |
| ------------ | -------- | ------ | ------------------------------------------------- |
| 发布话题     | POST     | user   | [/topics](#topics)                                |
| 修改话题     | PUT      | owner  | [/topics/:id](#topics-put)                        |
| 话题详情     | GET      | anyone | [/topics/:id](#topics-get)                        |
| 删除话题*    | DELETE   | owner  | [/topics/:id](#topics-delete)                     |
| 关注话题     | POST     | user   | [/topics/:id/follow](#topics-follow-post)         |
| 取消关注     | DELETE   | user   | [/topics/:id/follow](#topics-follow-delete)       |
| 添加分类     | POST     | owner  | [/topics/:id/tags](#topics-tags-post)             |
| 删除分类     | DELETE   | owner  | [/topics/:id/tags/:tag_id](#topics-tags-delete)   |
| 查看点赞用户 | GET      | anyone | [/topics/:id/thumbups](#topics-thumbups-get)      |
| 话题点赞     | POST     | user   | [/topics/:id/thumbups](#topics-thumbups-post)     |
| 取消点赞     | DELETE   | user   | [/topics/:id/thumbups](#topics-thumbups-delete)   |
| 查看话题回复 | GET      | anyone | [/topics/:id/replies](#topics-replies-get)        |
| 回复话题     | POST     | user   | [/topics/:id/replies](#topics-replies-post)       |
| 修改回复     | PUT      | owner  | [/replies/:id](#replies-put)                      |
| 删除回复*    | DELETE   | owner  | [/replies/:id](#replies-delete)                   |
| 回复点赞     | POST     | user   | [/replies/:id/thumbups](#replies-thumbups-post)   |
| 取消回复点赞 | DELETE   | user   | [/replies/:id/thumbups](#replies-thumbups-delete) |

<a name="topics"></a>

发布话题
-------

> 发布话题

#####URL

    POST /topics

#####参数列表

| 参数名  | 必要 |  类型  |  长度  | 描述 |
| ------- | ---- | ------ | ------ | ---- |
| tile    | true | string | 1~255  | 标题 |
| content | true | string | 1~4095 | 内容 |

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

<a name="topics-put"></a>

修改话题
-------

> 修改话题

#####URL

    PUT /topics/:id

#####参数列表

| 参数名  |  必要 |  类型  |  长度  |  描述  |
| ------- | ----- | ------ | ------ | ------ |
| :id     | true  | long   | 64bit  | 话题id |
| title   | false | string | 1~255  | 标题   |
| content | false | string | 1~4095 | 内容   |

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

<a name="topics-get"></a>

话题详情
-------

> 查看话题详情

#####URL

    GET /topics/:id

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 话题id |

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

#####备注

<a name="topics-delete"></a>

删除话题
-------

> 删除话题

#####URL

    DELETE /topics/:id

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 话题id |

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

<a name="topics-follow-post"></a>

关注话题
-------

> 关注话题

#####URL

    POST /topics/:id/follow

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 话题id |

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

<a name="topics-follow-delete"></a>

取消关注
-------

> 取消关注话题

#####URL

    DELETE /topics/:id/follow

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 话题id |

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

<a name="topics-tags-post"></a>

添加分类
-------

> 添加话题分类

#####URL

    POST /topics/:id/tags

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 话题id |

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

<a name="topics-tags-delete"></a>

删除分类
-------

> 删除话题的分类

#####URL

    DELETE /topics/:id/tags/:tag_id

#####参数列表

| 参数名  | 必要 | 类型 |  长度 |  描述  |
| ------- | ---- | ---- | ----- | ------ |
| :id     | true | long | 64bit | 话题id |
| :tag_id | true | long | 64bit | 分类id |

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

<a name="topics-thumbups-get"></a>

查看点赞用户
------------

> 查看为该话题点赞的用户

#####URL

    GET /topics/:id/thumbups

#####参数列表

| 参数名 |  必要 | 类型 |  长度 | 默认值 |       描述       |
| ------ | ----- | ---- | ----- | ------ | ---------------- |
| :id    | true  | long | 64bit |        | 话题id           |
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

#####备注

<a name="topics-thumbups-post"></a>

话题点赞
-------

> 为该话题点赞

#####URL

    POST/topics/:id/thumbups

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 话题id |

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

- 每个人对同一条话题只能点赞一次

<a name="topics-thumbups-delete"></a>

取消点赞
-------

> 取消对该话题点的赞

#####URL

    DELETE /topics/:id/thumbups

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 话题id |

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

<a name="topics-replies-post"></a>

回复话题
-------

> 回复话题

#####URL

    /topics/:id/replies

#####参数列表

| 参数名  | 必要 |  类型  |  长度  |   描述   |
| ------- | ---- | ------ | ------ | -------- |
| :id     | true | long   | 64bit  | 话题id   |
| content | true | string | 1~4095 | 回答内容 |

#####返回值

    {
        "code" : 0,
        "msg" : "success",
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |

#####备注

<a name="replies-put"></a>

修改回复
-------

> 修改话题回复

#####URL

    PUT /replies/:id

#####参数列表

| 参数名  |  必要 |  类型  |  长度  |  描述  |
| ------- | ----- | ------ | ------ | ------ |
| :id     | true  | long   | 64bit  | 回复id |
| content | false | string | 1~4095 | 回复内容       |

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

<a name="replies-delete"></a>

删除回复
-------

> 删除回复

#####URL

    DELETE /replies/:id

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 回复id |

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

<a name="replies-thumbups-post"></a>

回复点赞
-------

> 给回复点赞

#####URL

    POST /replies/:id/thumbups

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |

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

<a name="replies-thumbups-delete"></a>

取消回复点赞
-------

> 取消对回复的点赞

#####URL

    DELETE /replies/:id/thumbups

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 回复id |

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
