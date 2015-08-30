---
layout: page
title: 举报
permalink: /reports.html
---

举报接口
========

| 接口名 | HTTP方法 |            URL            |
| ------ | -------- | ------------------------- |
| 举报!  | POST     | [/reports](#reports-post) |

<a name="reports"></a>

举报
----

> 举报违规资源

#####URL

    POST /reports

#####参数列表

|    参数名    |  类型  |  长度 |       描述      |
| ------------ | ------ | ----- | --------------- |
| resource_url | string | 0~128 | 被举报的资源URL |
| cause        | string | 0~255 | 举报原因        |

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

- 被举报的资源URL需要验证有效性 以便运维人员处理
