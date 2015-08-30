---
layout: page
title: 用户
permalink: /users.html
---
用户接口
========

|        接口名        | HTTP方法 |  权限  |                           URL                           |
| -------------------- | -------- | ------ | ------------------------------------------------------- |
| 用户登录             | POST     | anyone | [/users/login](#users-login)                            |
| 用户注册             | POST     | anyone | [/users/register](#users-register)                      |
| 短信验证请求         | GET      | anyone | [/users/verify_cellphone](#users-verify-cellphone-get)  |
| 短信验证             | POST     | anyone | [/users/verify_cellphone](#users-verify-cellphone-post) |
| 重置密码请求         | GET      | anyone | [/users/reset_password](#users-reset-password-get)      |
| 重置密码             | POST     | anyone | [/users/reset_password](#users-reset-password-post)     |
| 获取用户资料         | GET      | anyone | [/users/:id](#users-get)                                |
| 获取用户关注         | GET      | anyone | [/users/:id/follows](#users-follows)                    |
| 获取用户粉丝         | GET      | anyone | [/users/:id/followers](#users-followers)                |
| 获取用户发布的分享   | GET      | anyone | [/users/:id/broadcasts](#users-broadcasts)              |
| 获取用户分享评论     | GET      | anyone | [/users/:id/comments](#users-comments)                  |
| 获取用户发布的话题   | GET      | anyone | [/users/:id/topics](#users-topics)                      |
| 获取用户关注的话题   | GET      | anyone | [/users/:id/topics/followed](#users-topics-followed)    |
| 获取用户回复过的话题 | GET      | anyone | [/users/:id/topics/replied](#users-topics-replied)      |
| 修改用户资料         | PUT      | user   | [/users](#users-put)                                    |
| 关注用户             | POST     | user   | [/users/follow](#users-follow)                          |
| 取消关注             | POST     | user   | [/users/unfollow](#users-unfollow)                      |
| 获取时间线           | GET      | user   | [/users/time_line](#users-timeline)                     |
| 添加教育经历         | POST     | user   | [/users/education](#users-education-post)               |
| 删除教育经历         | DELETE   | user   | [/users/education/:id](#users-education-delete)         |
| 添加工作经历         | POST     | user   | [/users/work_history](#users-work-history-post)     |
| 删除工作经历         | DELETE   | user   | [/users/work_history/:id](#users-work-history-delete)   |
| 添加用户标签         | POST     | user   | [/users/tags](#users-tags-post)                     |
| 删除用户标签         | DELETE   | user   | [/users/tags/:id](#users-tags-delete)                   |

<a name="users-login"></a>

用户登录
-------

> 用于验证用户名和密码 并设置session

#####URL

    POST /users/login

#####参数列表

|  参数名  | 必要 |  类型  | 长度 |  描述  |
| -------- | ---- | ------ | ---- | ------ |
| username | true | string | 4~60 | 用户名 |
| password | true | string | 4~60 | 密码   |

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

<a name="users-register"></a>

用户注册
-------

> 用于用户注册

#####URL

    POST /users/register

#####参数列表

|  参数名  | 必要 |  类型  | 长度 |  描述  |
| -------- | ---- | ------ | ---- | ------ |
| username | true | string | 4~60 | 用户名 |
| password | true | string | 4~60 | 密码   |
| nickname | true | string | 4~60 | 昵称   |

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


<a name="users-verify-cellphone-get"></a>

短信验证请求
------------

> 请求发送短信验证码

#####URL

    GET /users/verify_cellphone

#####参数列表

|  参数名   | 必要 |  类型  | 长度 |   描述   |
| --------- | ---- | ------ | ---- | -------- |
| cellphone | true | string |   11 | 手机号码 |

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

- 该接口同一IP或者同一号码每分钟只能发送一次


<a name="users-verify-cellphone-post"></a>

短信验证
--------

> 验证用户收到的短信验证码

#####URL

    POST /users/verify_cellphone

#####参数列表

| 参数名 | 必要 |  类型  | 长度 |     描述     |
| ------ | ---- | ------ | ---- | ------------ |
| code   | true | string |    6 | 收到的验证码 |

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

- 3次错误则失效


<a name="users-reset-password-get"></a>

重置密码请求
-----------

> 请求重置密码

#####URL

    GET /users/reset_password

#####参数列表

|  参数名  | 必要 |  类型  | 长度 |       描述       |
| -------- | ---- | ------ | ---- | ---------------- |
| username | true | string | 4~60 | 重置密码的用户名 |

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

- 同IP或用户名每60秒只能请求一次

<a name="users-reset-password-post"></a>

重置密码
--------

> 验证重置密码的验证码

#####URL

    POST /users/reset_password

#####参数列表

| 参数名 | 必要 |  类型  | 长度 |     描述     |
| ------ | ---- | ------ | ---- | ------------ |
| code   | true | string |    6 | 收到的验证码 |

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

- 重试3次验证码无效

<a name="users-get"></a>

获取用户资料
-------------

> 获取用户详细资料

#####URL

    GET /users/:id

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 用户id |

#####返回值

    {
        "code" : 0,
        "msg" : "success",
        "result" : {
            "id" : 123456789,
            "gender" : 1,
            "avatar" : "http://s11.album.sina.com.cn/pic_3/4c543a9d020017zm",
            "location" : "北京市 朝阳区",
            "nickname" : "毛主席",
            "education" : [{
                "id" : 123456789,
                "institution" : "湖南省立第四师范",
                "first_year" : "1913",
                "department" : "政治系"
            }],
            "work_history" : [{
                "id" : 123456789,
                "company" : "CCP",
                "position" : "总书记",
                "location" : "北京",
                "start_date" : "1930",
                "end_date" : "1976"
            }]
        }
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |
| result | object | 响应内容 |

#####备注

<a name="users-follows"></a>

获取用户关注
------------

> 获取用户已关注的人的列表

#####URL

    GET /users/:id/follows

#####参数列表

| 参数名 |  必要 | 类型 |  长度 | 默认值 |       描述       |
| ------ | ----- | ---- | ----- | ------ | ---------------- |
| :id    | true  | long | 64bit |        | 用户ID           |
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

<a name="users-followers"></a>

获取用户粉丝
------------

> 获取用户的粉丝列表

#####URL

    GET /users/:id/followers

#####参数列表

| 参数名 |  必要 | 类型 |  长度 | 默认值 |       描述       |
| ------ | ----- | ---- | ----- | ------ | ---------------- |
| :id    | true  | long | 64bit |        | 用户id           |
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
            "cellphone" : "13800138000",
            "location" : "北京市 朝阳区",
            "nickname" : "王二小"
        }]
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |
| result | array  | 响应内容 |

#####备注

<a name="users-broadcasts"></a>

获取用户发布的分享
------------

> 获取用户发布的分享

#####URL

    GET /users/:id/broadcasts

#####参数列表

| 参数名 |  必要 | 类型 |  长度 | 默认值 |       描述       |
| ------ | ----- | ---- | ----- | ------ | ---------------- |
| :id    | true  | long | 64bit |        | 用户id           |
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
| result | array  | 响应内容 |

#####备注

<a name="users-comments"></a>

获取用户分享评论
------------

> 获取用户分享评论

#####URL

    GET /users/:id/comments

#####参数列表

| 参数名 |  必要 | 类型 |  长度 | 默认值 |       描述       |
| ------ | ----- | ---- | ----- | ------ | ---------------- |
| :id    | true  | long | 64bit |        | 用户id           |
| pager  | false | int  | 32bit |     20 | 每页所含条目数量 |
| page   | false | int  | 32bit |      0 | 页码             |

#####返回值

    {
        "code" : 0,
        "msg" : "success",
        "result" : [{
            "id" : 123456789,
            "broadcast_id" : 123456789,
            "user_id" : 123456789,
            "content" : "呵呵 不错",
            "created" : 1440569734957,
            "thumbups_cnt" : 323
        }]
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |
| result | array  | 响应内容 |

#####备注

<a name="users-topics"></a>

获取用户发布的话题
------------

> 获取用户发布的话题

#####URL

    GET /users/:id/topics

#####参数列表

| 参数名 |  必要 | 类型 |  长度 | 默认值 |       描述       |
| ------ | ----- | ---- | ----- | ------ | ---------------- |
| :id    | true  | long | 64bit |        | 用户id           |
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
                "title" : "请问一切反动派都是纸老虎吗？",
                "content" : "是不是呀是不是呀？",
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
| result | array  | 响应内容 |

#####备注

<a name="users-topics-followed"></a>

获取用户关注的话题
------------

> 获取用户关注的话题

#####URL

    GET /users/:id/topics/followed

#####参数列表

| 参数名 |  必要 | 类型 |  长度 | 默认值 |       描述       |
| ------ | ----- | ---- | ----- | ------ | ---------------- |
| :id    | true  | long | 64bit |        | 用户id           |
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
| result | array  | 响应内容 |

#####备注

<a name="users-topics-replied"></a>

获取用户回复的话题
------------

> 获取用户回复的话题

#####URL

    GET /users/:id/topics/replied

#####参数列表

| 参数名 |  必要 | 类型 |  长度 | 默认值 |       描述       |
| ------ | ----- | ---- | ----- | ------ | ---------------- |
| :id    | true  | long | 64bit |        | 用户id           |
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
                    "nickname" : "王二小"
                },
                "title" : "请问羊一天放养多少小时合适？？",
                "content" : "一天几小时才是合理的",
                "created" : 1440569734957,
                "views" : 567,
                "replies_cnt" : 200,
                "thumbups_cnt" : 700,
                "replies" : [{
                    "id" : 123456789,
                    "user" : {
                        "id" : 123456789,
                        "gender" : 1,
                        "avatar" : "http://s11.album.sina.com.cn/pic_3/4c543a9d020017zm",
                        "location" : "甘肃省 兰州市",
                        "nickname" : "张教授",
                        "content" : "根据我的经验，常见的山羊应该保证至少4个小时",
                        "created" : 1440569754957
                    }
                }]
            }]
    }

#####返回字段说明

| 字段名 |  类型  |   描述   |
| ------ | ------ | -------- |
| code   | int    | 响应代码 |
| msg    | string | 响应消息 |
| result | array  | 响应内容 |

#####备注

<a name="users-put"></a>

修改用户资料
-------------

> 修改用户详细资料

#####URL

    PUT /users

#####参数列表

|   参数名    |  必要 |  类型  |  长度  |   描述   |
| ----------- | ----- | ------ | ------ | -------- |
| firstname   | false | string | 1~30   | 姓氏     |
| lastname    | false | string | 1~30   | 名字     |
| nickname    | false | string | 4~60   | 昵称     |
| gender      | false | int    | 32bit  | 性别     |
| avatar      | false | string | 0~2083 | 头像地址 |
| location_id | false | int    | 32bit  | 地区     |
| bio         | false | string | 0~2047 | 简介     |

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

- 未提交的参数对应的字段在数据库中不做修改


<a name="users-follow"></a>

关注用户
----

> 关注用户 接收对方发出的分享

#####URL

    POST /users/follow

#####参数列表

| 参数名  | 必要 | 类型 |  长度 |     描述     |
| ------- | ---- | ---- | ----- | ------------ |
| user_id | true | long | 64bit | 关注的用户ID |

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

<a name="users-unfollow"></a>

取消关注
----

> 取消关注用户

#####URL

    POST /users/unfollow

#####参数列表

| 参数名  | 必要 | 类型 |  长度 |       描述       |
| ------- | ---- | ---- | ----- | ---------------- |
| user_id | true | long | 64bit | 取消关注的用户ID |

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

- 需要验证是否已有关注关系

<a name="users-timeline"></a>

获取用户时间线
-------------

> 获取用户的时间线 即其所关注用户所发送的最近若干条分享

#####URL

    GET /users/time_line

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

<a name="users-education-post"></a>

添加教育经历
------------

> 添加教育经历

#####URL

    POST /users/education

#####参数列表

|   参数名    |  必要 |  类型  |  长度 |   描述   |
| ----------- | ----- | ------ | ----- | -------- |
| institution | true  | string | 1~255 | 学校名称 |
| first_year  | false | string | 4     | 入学时间 |
| department  | false | string | 0~255 | 院系     |

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

<a name="users-education-delete"></a>

删除教育经历
------------

> 删除教育经历

#####URL

    DELETE /users/education/:id

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |    描述    |
| ------ | ---- | ---- | ----- | ---------- |
| :id    | true | long | 64bit | 教育经历id |

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

- 需要验证教育经历id与用户的关联的有效性


<a name="users-work-history-post"></a>

添加工作经历
------------

> 添加工作经历

#####URL

    POST /users/work_history

#####参数列表

|   参数名   |  必要 |  类型  |  长度 |   描述   |
| ---------- | ----- | ------ | ----- | -------- |
| company    | true  | string | 1~255 | 公司名称 |
| position   | true  | string | 1~255 | 职位     |
| location   | false | string | 0~255 | 地点     |
| start_date | false | date   | 10    | 开始日期 |
| end_date   | false | date   | 10    | 结束日期 |

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

<a name="users-work-history-delete"></a>

删除工作经历
------------

> 删除工作经历

#####URL

    DELETE /users/work_history/:id

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |    描述    |
| ------ | ---- | ---- | ----- | ---------- |
| :id    | true | long | 64bit | 工作经历id |

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

- 需要验证工作经历id与用户关联的有效性

<a name="users-tags-post"></a>

添加用户标签
------------

> 添加用户标签

#####URL

    POST /users/tags

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| tag_id | true | long | 64bit | 标签id |

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

<a name="users-tags-delete"></a>

删除用户标签
------------

> 删除用户标签

#####URL

    DELETE /users/tags/:id

#####参数列表

| 参数名 | 必要 | 类型 |  长度 |  描述  |
| ------ | ---- | ---- | ----- | ------ |
| :id    | true | long | 64bit | 标签id |

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
