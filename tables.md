---
layout: page
title: 表结构
permalink: /tables.html
---

Superloop数据库表结构
=====================
- 带*项目为外键
- 带!项目为主键
- 带(U)项目为UNIQUE索引

users表
-------

> 用户数据表

|    字段名    |             类型            |   说明   |
| ------------ | --------------------------- | -------- |
| id!          | INT                         | 用户id   |
| username(U)  | VARCHAR(255)                | 用户名   |
| password     | VARCHAR(255)                | 密码     |
| firstname    | VARCHAR(255)                | 姓氏     |
| lastname     | VARCHAR(255)                | 名字     |
| nickname     | VARCHAR(255)                | 昵称     |
| gender       | TINYINT                     | 性别     |
| avatar       | VARCHAR(2083)               | 头像URL  |
| cellphone(U) | VARCHAR(11)                 | 手机号码 |
| location_id* | INT                         | 地点id   |
| bio          | VARCHAR(2047)               | 简介     |
| role         | ENUM('user','admin','root') | 用户角色 |
| created      | TIMESTAMP                   | 注册时间 |

注：HTTP URL最长长度为2083

用户角色：

- user 普通用户
- admin 管理员
- root 超级管理员

user_tags表
-----------------

> 用户标签表

|  字段名   | 类型 |  说明  |
| --------- | ---- | ------ |
| user_id*! | INT  | 用户id |
| tag_id*   | INT  | 标签id |

education表
-------------------

> 教育经历表

|   字段名    |     类型     |    说明    |
| ----------- | ------------ | ---------- |
| id!         | INT          | 教育经历id |
| user_id*    | INT          | 用户id     |
| institution | VARCHAR(255) | 学校名称   |
| first_year  | YEAR         | 入学时间   |
| department  | VARCHAR(255) | 院系       |

work_history表
--------------

> 工作经历表

|   字段名   |     类型     |    说明    |
| ---------- | ------------ | ---------- |
| id!        | INT          | 工作经历id |
| user_id    | INT          | 用户id     |
| company    | VARCHAR(255) | 公司名称   |
| position   | VARCHAR(255) | 部门/职位  |
| location   | VARCHAR(255) | 所在地     |
| start_date | DATE         | 开始时间   |
| end_date   | DATE         | 结束时间   |

broadcasts表
------------

> 分享表

|  字段名  |     类型     |   说明   |
| -------- | ------------ | -------- |
| id!      | INT          | 分享id   |
| user_id* | INT          | 发表人id |
| content  | VARCHAR(600) | 分享内容 |
| created  | TIMESTAMP    | 创建时间 |

broadcast_attachments表
-----------------------

> 分享附件表

|     字段名      |      类型     |   说明   |
| --------------- | ------------- | -------- |
| id!             | INT           | 附件id   |
| broadcast_id*   | INT           | 分享id   |
| attachment_url  | VARCHAR(2083) | 附件URL  |
| attachment_type | VARCHAR(10)   | 附件类型 |


broadcast_comments表
--------------------

> 分享评论表

|    字段名     |     类型     |   说明   |
| ------------- | ------------ | -------- |
| id!           | INT          | 评论id   |
| broadcast_id* | INT          | 分享id   |
| user_id*      | INT          | 发表人id |
| content       | VARCHAR(600) | 评论内容 |
| created       | TIMESTAMP    | 发表时间 |

broadcast_thumbups表
--------------------

> 分享点赞表

|     字段名     | 类型 |  说明  |
| -------------- | ---- | ------ |
| user_id*!      | INT  | 用户id |
| broadcast_id*! | INT  | 分享id |

broadcast_comment_thumbups表
----------------------------

> 分享评论点赞表

|         字段名         | 类型 |    说明    |
| ---------------------- | ---- | ---------- |
| user_id*!              | INT  | 用户id     |
| broadcast_comment_id*! | INT  | 分享评论id |

topics表
--------

> 话题表

|  字段名  |      类型     |   说明   |
| -------- | ------------- | -------- |
| id!      | INT           | 话题id   |
| user_id* | INT           | 用户id   |
| title    | VARCHAR(255)  | 话题标题 |
| content  | VARCHAR(4095) | 话题内容 |
| views    | INT           | 查看计数 |
| created  | TIMESTAMP     | 发表时间 |

topic_thumbups表
------------------------

> 话题点赞表

|   字段名   | 类型 |  说明  |
| ---------- | ---- | ------ |
| topic_id*! | INT  | 话题id |
| user_id*!  | INT  | 用户id |

topic_replies表
---------------

> 话题回复表

|  字段名   |      类型     |   说明   |
| --------- | ------------- | -------- |
| id!       | INT           | 回复id   |
| topic_id* | INT           | 话题id   |
| user_id*  | INT           | 用户id   |
| content   | VARCHAR(4095) | 回复内容 |
| created   | TIMESTAMP     | 发表时间 |

topic_replies_thumbups表
------------------------

> 话题回复点赞表

|      字段名      | 类型 |    说明    |
| ---------------- | ---- | ---------- |
| topic_reply_id*! | INT  | 话题回复id |
| user_id*!        | INT  | 用户id     |

topic_tags表
------------------

> 话题分类表

|   字段名   | 类型 |  说明  |
| ---------- | ---- | ------ |
| topic_id*! | INT  | 话题id |
| tag_id*!   | INT  | 分类id |


topic_follows表
---------------

> 话题关注表

|   字段名   | 类型 |  说明  |
| ---------- | ---- | ------ |
| topic_id*! | INT  | 话题id |
| user_id*!  | INT  | 用户id |

fovourite_broadcasts表
----------------------

> 分享收藏表

|     字段名     | 类型 |  说明  |
| -------------- | ---- | ------ |
| broadcast_id*! | INT  | 分享id |
| user_id*!      | INT  | 用户id |

fovourite_topics表
----------------------

> 分享收藏表

|   字段名   | 类型 |  说明  |
| ---------- | ---- | ------ |
| topic_id*! | INT  | 话题id |
| user_id*!  | INT  | 用户id |

credits表
--------

> 用户余额表

|  字段名   | 类型 |    说明    |
| --------- | ---- | ---------- |
| user_id*! | INT  | 用户id     |
| balance   | INT  | 余额（分） |

**！注：余额的单位为分**

transactions表
--------------

> 收支记录表

|  字段名  |     类型    |      说明      |
| -------- | ----------- | -------------- |
| id!      | INT         | 收支id         |
| user_id* | INT         | 用户id         |
| type     | VARCHAR(10) | 收支类型       |
| amount   | INT         | 收支数量（分） |
| created  | TIMESTAMP   | 发生时间       |

**！注：余额的单位为分**

locations表
-----------

> 地点表

|  字段名   |     类型     |    说明    |
| --------- | ------------ | ---------- |
| id!       | INT          | 地点id     |
| parent_id | INT          | 父级地点id |
| name      | VARCHAR(255) | 地名       |

tags表
------

> 标签表

|  字段名   |     类型     |   说明   |
| --------- | ------------ | -------- |
| id!       | INT          | 标签id   |
| parent_id | INT          | 父标签id |
| name      | VARCHAR(255) | 标签名   |

reports表
--------

> 举报表

|    字段名    |                  类型                 |        说明        |
| ------------ | ------------------------------------- | ------------------ |
| id!          | INT                                   | 举报id             |
| user_id*     | INT                                   | 举报用户id         |
| admin_id*    | INT                                   | 处理举报的管理员id |
| resource_url | VARCHAR(255)                          | 被举报的资源URL    |
| cause        | VARCHAR(4095)                         | 举报原因           |
| state        | ENUM('new','processing','proccessed') | 状态               |

举报状态：

- new 新举报
- processing 举报处理中
- processed 举报处理完成
