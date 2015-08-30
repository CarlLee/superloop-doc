---
layout: page
title: 首页
permalink: /index.html
---

Superloop API 文档
==================
> P.S. 带*项目为未确定项目

协议格式
--------
- RESTful Web Service
- 数据格式为JSON
- 为防止session hijacking 强制使用https协议

验证方式*
---------

###方式一：cookie + session：

使用cookie和session保存登录状态、用户名、用户信息，用于各接口鉴权。

使用[`/login`](users.html#users-login)接口获取并设置`session id`

###方式二: [Basic Auth](https://en.wikipedia.org/wiki/Basic_access_authentication)

使用`Authorization`请求头附带Base64编码的`用户名:密码`的字符串在所有需要鉴权的接口


目录
---

###[用户接口](users.html)

|        接口名        | HTTP方法 |  权限  |                           URL                           |
| -------------------- | -------- | ------ | ------------------------------------------------------- |
| 用户登录             | POST     | anyone | [/users/login](users.html#users-login)                            |
| 用户注册             | POST     | anyone | [/users/register](users.html#users-register)                      |
| 短信验证请求         | GET      | anyone | [/users/verify_cellphone](users.html#users-verify-cellphone-get)  |
| 短信验证             | POST     | anyone | [/users/verify_cellphone](users.html#users-verify-cellphone-post) |
| 重置密码请求         | GET      | anyone | [/users/reset_password](users.html#users-reset-password-get)      |
| 重置密码             | POST     | anyone | [/users/reset_password](users.html#users-reset-password-post)     |
| 获取用户资料         | GET      | anyone | [/users/:id](users.html#users-get)                                |
| 获取用户关注         | GET      | anyone | [/users/:id/follows](users.html#users-follows)                    |
| 获取用户粉丝         | GET      | anyone | [/users/:id/followers](users.html#users-followers)                |
| 获取用户发布的分享   | GET      | anyone | [/users/:id/broadcasts](users.html#users-broadcasts)              |
| 获取用户分享评论     | GET      | anyone | [/users/:id/comments](users.html#users-comments)                  |
| 获取用户发布的话题   | GET      | anyone | [/users/:id/topics](users.html#users-topics)                      |
| 获取用户关注的话题   | GET      | anyone | [/users/:id/topics/followed](users.html#users-topics-followed)    |
| 获取用户回复过的话题 | GET      | anyone | [/users/:id/topics/replied](users.html#users-topics-replied)      |
| 修改用户资料         | PUT      | user   | [/users](users.html#users-put)                                    |
| 关注用户             | POST     | user   | [/users/follow](users.html#users-follow)                          |
| 取消关注             | POST     | user   | [/users/unfollow](users.html#users-unfollow)                      |
| 获取时间线           | GET      | user   | [/users/time_line](users.html#users-timeline)                     |
| 添加教育经历         | POST     | user   | [/users/education](users.html#users-education-post)               |
| 删除教育经历         | DELETE   | user   | [/users/education/:id](users.html#users-education-delete)         |
| 添加工作经历         | POST     | user   | [/users/work_history](users.html#users-work-history-post)         |
| 删除工作经历         | DELETE   | user   | [/users/work_history/:id](users.html#users-work-history-delete)   |
| 添加用户标签         | POST     | user   | [/users/tags](users.html#users-tags-post)                         |
| 删除用户标签         | DELETE   | user   | [/users/tags/:id](users.html#users-tags-delete)                   |


###分享接口

|    接口名    | HTTP方法 |  权限  |                           URL                           |
| ------------ | -------- | ------ | ------------------------------------------------------- |
| 发布分享     | POST     | user   | [/broadcasts](broadcast.html#broadcasts-post)                         |
| 分享详情     | GET      | anyone | [/broadcasts/:id](broadcast.html#broadcasts-get)                      |
| 删除分享     | DELETE   | owner  | [/broadcasts/:id](broadcast.html#broadcasts-delete)                   |
| 查看点赞用户 | GET      | anyone | [/broadcasts/:id/thumbups](broadcast.html#broadcasts-thumbups-get)    |
| 分享点赞     | POST     | user   | [/broadcasts/:id/thumbups](broadcast.html#broadcasts-thumbups-post)   |
| 取消点赞     | DELETE   | user   | [/broadcasts/:id/thumbups](broadcast.html#broadcasts-thumbups-delete) |
| 评论分享     | POST     | user   | [/broadcasts/:id/comments](broadcast.html#broadcasts-comments-post)   |
| 查看评论     | GET      | anyone | [/broadcasts/:id/comments](broadcast.html#broadcasts-comments-get)    |
| 删除分享     | DELETE   | owner  | [/comments/:id](broadcast.html#broadcasts-comments-delete)            |
| 评论点赞     | POST     | user   | [/comments/:id/thumbups](broadcast.html#comments-thumbups-post)       |
| 取消评论点赞 | DELETE   | owner  | [/comments/:id/thumbups](broadcast.html#comments-thumbups-delete)     |

###话题接口

|    接口名    | HTTP方法 |  权限  |                        URL                        |
| ------------ | -------- | ------ | ------------------------------------------------- |
| 发布话题     | POST     | user   | [/topics](topics.html#topics)                                |
| 修改话题     | PUT      | owner  | [/topics/:id](topics.html#topics-put)                        |
| 话题详情     | GET      | anyone | [/topics/:id](topics.html#topics-get)                        |
| 删除话题*    | DELETE   | owner  | [/topics/:id](topics.html#topics-delete)                     |
| 关注话题     | POST     | user   | [/topics/:id/follow](topics.html#topics-follow-post)         |
| 取消关注     | DELETE   | user   | [/topics/:id/follow](topics.html#topics-follow-delete)       |
| 添加分类     | POST     | owner  | [/topics/:id/tags](topics.html#topics-tags-post)             |
| 删除分类     | DELETE   | owner  | [/topics/:id/tags/:tag_id](topics.html#topics-tags-delete)   |
| 查看点赞用户 | GET      | anyone | [/topics/:id/thumbups](topics.html#topics-thumups-get)       |
| 话题点赞     | POST     | user   | [/topics/:id/thumbups](topics.html#topics-thumbups-post)     |
| 取消点赞     | DELETE   | user   | [/topics/:id/thumbups](topics.html#topics-thumbups-delete)   |
| 回复话题     | POST     | user   | [/topics/:id/replies](topics.html#topics-replies-post)       |
| 修改回复     | PUT      | owner  | [/replies/:id](topics.html#replies-put)                      |
| 删除回复*    | DELETE   | owner  | [/replies/:id](topics.html#replies-delete)                   |
| 回复点赞     | POST     | user   | [/replies/:id/thumbups](topics.html#replies-thumbups-post)   |
| 取消回复点赞 | DELETE   | user   | [/replies/:id/thumbups](topics.html#replies-thumbups-delete) |

###收藏接口

|  接口名  | HTTP方法 | 权限 |                       URL                        |
| -------- | -------- | ---- | ------------------------------------------------ |
| 收藏分享 | POST     | user | [/favourites/broadcasts](#favourites-broadcasts) |
| 收藏话题 | POST     | user | [/favourites/topics](#favourites-topics)         |


###搜索接口

|  接口名  | HTTP方法 |  权限  |                   URL                    |
| -------- | -------- | ------ | ---------------------------------------- |
| 搜索用户 | GET      | anyone | [/search/users](#search-users)           |
| 搜索分享 | GET      | anyone | [/search/broadcasts](#search-broadcasts) |
| 搜索话题 | GET      | anyone | [/search/topics](#search-topics)         |

###充值/支付接口

|    接口名    | HTTP方法 | 权限 |                  URL                   |
| ------------ | -------- | ---- | -------------------------------------- |
| 充值请求     | POST     | user | [/credits/charge](credits.html#credits-charge)     |
| 提现请求     | POST     | user | [/credits/withdraw](credits.html#credits-withdraw) |
| 设置限额     | PUT      | user | [/credits/limits](credits.html#credits-limit)      |
| 打赏!        | POST     | user | [/credits/reward](credits.html#credits-reward)     |
| 获取收支记录 | GET      | user | [/credits/history](credits.html#credits-history)   |
| 查看余额     | GET      | user | [/credits](credits.html#credits)                   |

###杂项

|    接口名    | HTTP方法 |  权限  |              URL               |
| ------------ | -------- | ------ | ------------------------------ |
| 获取地区列表 | GET      | anyone | [/locations](#locations-get)   |
| 获取分类列表 | GET      | anyone | [/categories](#categories-get) |


###举报接口

| 接口名 | HTTP方法 |  权限  |            URL            |
| ------ | -------- | ------ | ------------------------- |
| 举报!  | POST     | anyone | [/reports](reports.html#reports-post) |

###运维接口

|  接口名  | HTTP方法 |  权限 |                   URL                    |
| -------- | -------- | ----- | ---------------------------------------- |
| 获取举报 | GET      | admin | [/reports](#reports-get)                 |
| 接受举报 | PUT      | admin | [/reports/:id](#reports-put)             |
| 处理举报 | POST     | admin | [/reports/:id/process](#reports-process) |
| 添加地区 | POST     | admin | [/locations](#locations-post)            |
| 更新地区 | PUT      | admin | [/locations/:id](#locations-put)         |
| 删除地区 | DELETE   | admin | [/locations/:id](#locations-delete)      |
| 添加分类 | POST     | admin | [/categories](#categories-post)          |
| 修改分类 | PUT      | admin | [/categories/:id](#categories-put)       |
| 删除分类 | DELETE   | admin | [/categories/:id](#categories-delete)    |

权限类型解释
------------
- anyone 所有人都可以访问该接口
- user 注册用户可以访问该接口 

    > 该接口所操作的资源关联的用户为访问该接口的用户

- owner 该资源的所有者可以访问该接口
- admin 管理员可以访问该接口

<a name="resource-url"></a>

资源URL规则
-----------
#### 格式

    /:resourse_name/:resource_id(/:sub_resource_name/:sub_resource_id)*

####注释

|      变量名       |  类型  |   描述   |
| ----------------- | ------ | -------- |
| resource_name     | string | 资源名称 |
| resource_id       | long   | 资源ID   |
| sub_resource_name | string | 子资源名 |
| sub_resource_id   | long   | 子资源ID |

####例子

    /broadcasts/1102357/comments/2795654

<a name="field-rules"></a>

字段规则
--------
####日期(date)
    YYYY-mm-dd

####用户名(username)
    [a-zA-Z0-9@._-]{4,60}

####密码(password)
    [a-zA-Z0-9@._-]{4,60}

####真实姓名(name)
    TODO

####昵称(nickname)
    /^[a-z0-9_À-ÖØ-öø-ÿĀ-ɏɓ-ɔɖ-ɗəɛɣɨɯɲʉʋʻ̀-ͯḀ-ỿЀ-ӿԀ-ԧⷠ-ⷿꙀ-֑ꚟ-ֿׁ-ׂׄ-ׇׅא-תװ-״﬒-ﬨשׁ-זּטּ-לּמּנּ-סּףּ-פּצּ-ﭏؐ-ؚؠ-ٟٮ-ۓە-ۜ۞-۪ۨ-ۯۺ-ۼۿݐ-ݿࢠࢢ-ࢬࣤ-ࣾﭐ-ﮱﯓ-ﴽﵐ-ﶏﶒ-ﷇﷰ-ﷻﹰ-ﹴﹶ-ﻼ‌ก-ฺเ-๎ᄀ-ᇿ㄰-ㆅꥠ-꥿가-힯ힰ-퟿ﾡ-ￜァ-ヺー-ヾｦ-ﾟｰ０-９Ａ-Ｚａ-ｚぁ-ゖ゙-ゞ㐀-䶿一-鿿꜀-뜿띀-렟-﨟〃々〻]*[a-z_À-ÖØ-öø-ÿĀ-ɏɓ-ɔɖ-ɗəɛɣɨɯɲʉʋʻ̀-ͯḀ-ỿЀ-ӿԀ-ԧⷠ-ⷿꙀ-֑ꚟ-ֿׁ-ׂׄ-ׇׅא-תװ-״﬒-ﬨשׁ-זּטּ-לּמּנּ-סּףּ-פּצּ-ﭏؐ-ؚؠ-ٟٮ-ۓە-ۜ۞-۪ۨ-ۯۺ-ۼۿݐ-ݿࢠࢢ-ࢬࣤ-ࣾﭐ-ﮱﯓ-ﴽﵐ-ﶏﶒ-ﷇﷰ-ﷻﹰ-ﹴﹶ-ﻼ‌ก-ฺเ-๎ᄀ-ᇿ㄰-ㆅꥠ-꥿가-힯ힰ-퟿ﾡ-ￜァ-ヺー-ヾｦ-ﾟｰ０-９Ａ-Ｚａ-ｚぁ-ゖ゙-ゞ㐀-䶿一-鿿꜀-뜿띀-렟-﨟〃々〻][a-z0-9_À-ÖØ-öø-ÿĀ-ɏɓ-ɔɖ-ɗəɛɣɨɯɲʉʋʻ̀-ͯḀ-ỿЀ-ӿԀ-ԧⷠ-ⷿꙀ-֑ꚟ-ֿׁ-ׂׄ-ׇׅא-תװ-״﬒-ﬨשׁ-זּטּ-לּמּנּ-סּףּ-פּצּ-ﭏؐ-ؚؠ-ٟٮ-ۓە-ۜ۞-۪ۨ-ۯۺ-ۼۿݐ-ݿࢠࢢ-ࢬࣤ-ࣾﭐ-ﮱﯓ-ﴽﵐ-ﶏﶒ-ﷇﷰ-ﷻﹰ-ﹴﹶ-ﻼ‌ก-ฺเ-๎ᄀ-ᇿ㄰-ㆅꥠ-꥿가-힯ힰ-퟿ﾡ-ￜァ-ヺー-ヾｦ-ﾟｰ０-９Ａ-Ｚａ-ｚぁ-ゖ゙-ゞ㐀-䶿一-鿿꜀-뜿띀-렟-﨟〃々〻]+$/

####手机号码(cellphone)
    [0-9]{11}

<a name="result-codes"></a>

响应代码
--------

| 代码 |         原因         |                    消息                    |
| ---- | -------------------- | ------------------------------------------ |
|    0 | 请求成功             | success                                    |
|      | 参数格式错误         | invalid parameters                         |
|      | 缺少必填字段         | required field missing                     |
|      | 请求的id不存在       | requested id does not exist                |
|      | 没有权限             | no authorization                           |
|      | 用户未激活           | user not yet activated                     |
|      | 用户名或密码错误     | username or password is wrong              |
|      | 用户名被占用         | username in use                            |
|      | 用户不存在           | user does not exist                        |
|      | 手机号码被占用       | cellphone in use                           |
|      | 验证码错误或过期     | verification code is wrong or have expired |
|      | 已达到频率限制       | rate limit reached                         |
|      | 每个项目只能点赞一次 | only one thumbup is allowed per item       |


