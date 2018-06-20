## xueji-wiki

### index
+ [方法列表](#方法列表)
+ [响应状态码表](#响应状态码表)

### 方法列表

| 类别 |                               方法名                               |                uri                 | 说明 |
| ---- | ------------------------------------------------------------------ | ---------------------------------- | ---- |
| 分类 | [category](category.md)                                            | \-                                 |      |
| \-   | [列表](category.md#列表)                                           | ```/app1/category/list```          |      |
| \-   | [添加](category.md#添加)                                           | ```/app1/category/add```           |      |
| \-   | [排序](category.md#排序)                                           | ```/app1/category/sort```          |      |
| 书籍 | [book](book.md)                                                    | \-                                 |      |
| \-   | [添加书籍](book.md#添加)                                         | ```/app1/book/add```               |       |
| \-   | [移除书籍](book.md#移除)                                          | ```/app1/book/remove```               |       |
| \-   | [详情](book.md#详情)                                               | ```/app1/book/detail```            |      |
| \-   | ~~[isbn添加](#)~~ **⚠️已废弃，功能并入 app1/book/add⚠️**            |                                    |      |
| \-   | ~~[自定义添加](#)~~ **⚠️️已废弃，功能并入 app1/book/add⚠️**          |                                    |      |
| 用户 | [user](user.md)                                                    | \-                                 |      |
| \-   | [登录](user.md#登录)                                               | ```/app1/user/login```             |      |
| \-   | [登出(TODO)](user.md#todo登出)                                     | ```/app1/user/logout```            |      |
| \-   | [静默注册](user.md#静默注册)                                       | ```/app1/user/ssign_up```          |      |
| \-   | [详情](user.md#详情)                                               | ```/app1/user/profile```           |      |
| \-   | [设置](user.md#设置)                                               | ```/app1/user/setting```           |      |
| 学习 | [learn](learn.md)                                                  | \-                                 |      |
| \-   | [记录](learn.md#记录)                                              | ```/app1/learn/log```              |      |
| \-   | [设置周目标](learn.md#设置周目标)                                  | ```/app1/learn/week_goal```        |      |
| 页面定制 | [main](main.md)                                                    | \-                          |      |
| \-   | [主页](main.md#主页)                                               | ```/app1/main/index```             |      |
| \-   | [我的](main.md#我的)                                               | ```/app1/main/my```             |      |
| 传图 | [upload](upload.md)                                                | \-                                 |      |
| \-   | [传图](upload.md#传图)                                             | ```/app1/upload/index```           |      |
| 复习 | [review](review.md)                                                | \-                                 |      |
| \-   | [详情](review.md#详情)                                             | ```/app1/review/detail```          |      |
| \-   | [列表(指定天数)](review.md#列表指定天数)                           | ```/app1/review/range```           |      |
| \-   | [标记复习完成](review.md#标记复习完成)                             | ```/app1/review/done```            |      |
| 统计 | [report](report.md)                                                | \-                                 |      |
| \-   | [连续学习时间周目标完成情况](report.md#连续学习时间周目标完成情况) | ```/app1/report/continuous_days``` |      |
| \-   | [合计(书籍)](report.md#合计书籍)                                   | ```/app1/report/all_by_book```     |      |
| \-   | [周目标达成情况](report.md#周目标达成情况)                         | ```/app1/report/week_report```     |      |

[返回顶部](#index)

### 响应状态码表

|  code  |              说明              |
| ------ | ------------------------------ |
|      0 | success                        |
|      1 | 参数错误                       |
|      2 | 未登录                         |
| 333001 | 用户不存在                     |
| 333002 | 用户校验失败                   |
| 333003 | 图片验证码错误                 |
| 333004 | 手机号格式错误                 |
| 333005 | 忘记设置性别啦～               |
| 333006 | 注册失败                       |
| 333007 | token添加失败                  |
| 333008 | 手机验证码错误                 |
| 333009 | 防打扰时间非法                 |
| 333010 | 设置失败                       |
| 333101 | 列表不存在                     |
| 333102 | 书籍查找错误                   |
| 333103 | 分类排序失败                   |
| 333104 | 无新数据                       |
| 333201 | 书籍不存在                     |
| 333202 | 分类不存在                     |
| 333203 | 自定义书籍添加失败             |
| 333204 | 加入分类失败                   |
| 333205 | 书籍添加失败                   |
| 333206 | 书籍移除失败                   |
| 333401 | 书籍不存在                     |
| 333402 | 记录失败                       |
| 333403 | 起止页码非法                   |
| 333404 | 复习计划创建失败               |
| 333405 | 学习时间和页数目标不可同时为空 |
| 333406 | 设置周目标失败                 |
| 333407 | 连续学习天数纪录失败           |
| 333601 | 图片上传失败                   |
| 333701 | 复习计划不存在                 |
| 333702 | 时间格式错误                   |
| 333703 | 非法复习阶段                   |
| 333704 | 复习条目不存在                 |
| 333705 | 已经复习过该阶段               |
| 333706 | 复习信息记录失败               |
| 333801 | 用户无学习记录                 |

[返回顶部](#index)