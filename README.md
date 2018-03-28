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
| \-   | [isbn添加](book.md#isbn添加)                                       | ```/app1/book/add```               |      |
| \-   | [自定义添加](book.md#自定义添加)                                   | ```/app1/book/add_custom```        |      |
| \-   | [详情](book.md#详情)                                               | ```/app1/book/detail```            |      |
| 用户 | [user](user.md)                                                    | \-                                 |      |
| \-   | [登录](user.md#登录)                                               | ```/app1/user/login```             |      |
| \-   | [登出(TODO)](user.md#todo登出)                                     | ```/app1/user/logout```            |      |
| \-   | [静默注册](user.md#静默注册)                                       | ```/app1/user/ssign_up```          |      |
| \-   | [详情](user.md#详情)                                               | ```/app1/user/profile```           |      |
| \-   | [设置](user.md#设置)                                               | ```/app1/user/setting```           |      |
| 学习 | [learn](learn.md)                                                  | \-                                 |      |
| \-   | [记录](learn.md#记录)                                              | ```/app1/learn/log```              |      |
| \-   | [设置周目标](learn.md#设置周目标)                                  | ```/app1/learn/week_goal```        |      |
| 主页 | [main](main.md)                                                    | \-                                 |      |
| \-   | [主页](main.md#主页)                                               | ```/app1/main/index```             |      |
| 传图 | [upload](upload.md)                                                | \-                                 |      |
| \-   | [传图](upload.md#传图)                                             | ```/app1/upload/index```           |      |
| 复习 | [review](review.md)                                                | \-                                 |      |
| \-   | [详情](review.md#详情)                                             | ```/app1/review/detail```          |      |
| \-   | [列表(指定天数)](review.md#列表指定天数)                           | ```/app1/review/range```           |      |
| 统计 | [report](report.md)                                                | \-                                 |      |
| \-   | [连续学习时间周目标完成情况](report.md#连续学习时间周目标完成情况) | ```/app1/report/continuous_days``` |      |
| \-   | [合计(书籍)](report.md#合计书籍)                                   | ```/app1/report/all_by_book```     |      |
| \-   | [周目标达成情况](report.md#周目标达成情况)                         | ```/app1/report/week_report```     |      |

[返回顶部](#index)

### 响应状态码表

|  code  |              说明              |
| ------ | ------------------------------ |
| 333101 | 列表不存在                     |
| 333102 | 书籍查找错误                   |
| 333103 | 分类排序失败                   |
| 333104 | 无新数据                       |
| 333201 | 书籍不存在                     |
| 333202 | 分类不存在                     |
| 333203 | 自定义书籍添加失败             |
| 333204 | 加入分类失败                   |
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
| 333401 | 书籍不存在                     |
| 333402 | 记录失败                       |
| 333403 | 起止页码非法                   |
| 333404 | 复习计划创建失败               |
| 333405 | 学习时间和页数目标不可同时为空 |
| 333406 | 设置周目标失败                 |
| 333407 | 连续学习天数纪录失败           |
| 333601 | 图片上传失败                   |

[返回顶部](#index)