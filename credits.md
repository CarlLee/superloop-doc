---
layout: page
title: 支付
permalink: /credits.html
---

充值/支付接口
=============

|    接口名    | HTTP方法 |                  URL                   |
| ------------ | -------- | -------------------------------------- |
| 充值请求     | POST     | [/credits/charge](#credits-charge)     |
| 提现请求     | POST     | [/credits/withdraw](#credits-withdraw) |
| 设置限额     | PUT      | [/credits/limits](#credits-limit)      |
| 打赏!        | POST     | [/credits/reward](#credits-reward)     |
| 获取收支记录 | GET      | [/credits/history](#credits-history)   |
| 查看余额     | GET      | [/credits](#credits)                   |
|              |          |                                        |

<a name="#credits-reward"></a>

打赏
----

> 用于打赏现金给其他用户 可以附带打赏的资源URL

#####URL

    POST /credits/reward

#####参数列表

|    参数名    |  必要 |  类型  |  长度 |         描述        |
| ------------ | ----- | ------ | ----- | ------------------- |
| amount       | true  | int    | 32bit | 打赏金额            |
| to_user      | true  | long   | 64bit | 被打赏的用户ID      |
| resource_url | false | string | 0~128 | 与打赏相关的资源URL |

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

- 资源URL用于记录用户打赏的位置和原因

例如用户打赏话题作者时 资源URL为：/topics/1876887

用户打赏话题回复者时 资源URL为：/topics/1876887/comments/234523452

- 不需要验证资源URL的有效性

主要考虑的因素有

1. 资源有可能会失效

2. 不一定所有打赏都需要和某个资源关联 方便以后扩展功能

- 参见[资源URL格式](index.html#resource-url)
