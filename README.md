## xueji-wiki

### 方法列表

| 类别 |                              方法名                              |              uri              |   说明   |
| ---- | ---------------------------------------------------------------- | ----------------------------- | -------- |
| 分类 | \-                                                               | \-                            | \-       |
| \-   | [列表](/liumdlp/xueji-wiki/blob/master/category.md#列表)         | ```/app1/category/list```     |          |
| \-   | [添加](/liumdlp/xueji-wiki/blob/master/category.md#添加)         | ```/app1/category/add```      |          |
| \-   | [列表](/liumdlp/xueji-wiki/blob/master/category.md#列表)         | ```/app1/category/upd_book``` | *已废弃* |
| \-   | [排序](/liumdlp/xueji-wiki/blob/master/category.md#排序)         | ```/app1/category/sort```     |          |
| 书籍 | \-                                                               | \-                            | \-       |
| \-   | [isbn添加](/liumdlp/xueji-wiki/blob/master/book.md#isbn添加)     | ```/app1/book/add```          |          |
| \-   | [自定义添加](/liumdlp/xueji-wiki/blob/master/book.md#自定义添加) | ```/app1/book/add_custom```   |          |
| \-   | [详情](/liumdlp/xueji-wiki/blob/master/book.md#详情)             | ```/app1/book/detail```       |          |
| 用户 | \-                                                               | \-                            | \-       |
| \-   | [登录](/liumdlp/xueji-wiki/blob/master/user.md#登录)             | ```/app1/user/```             |          |
| \-   | [登出(TODO)](/liumdlp/xueji-wiki/blob/master/user.md#todo登出)   | ```/app1/user/```                       ||
| \-   | [静默注册](/liumdlp/xueji-wiki/blob/master/user.md#静默注册)     | ```/app1/user/```                       ||
| \-   | [详情](/liumdlp/xueji-wiki/blob/master/user.md#详情)             | ```/app1/user/```                       ||
| \-   | [设置](/liumdlp/xueji-wiki/blob/master/user.md#设置)             | ```/app1/user/```                       ||
|      |                                                                  |                               |          |





### 响应状态码表

|  code  |        说明        |
| ------ | ------------------ |
| 333101 | 列表不存在         |
| 333102 | 书籍查找错误       |
| 333103 | 分类排序失败       |
| 333104 | 无新数据           |
| 333201 | 书籍不存在         |
| 333202 | 分类不存在         |
| 333203 | 自定义书籍添加失败 |
| 333204 | 加入分类失败       |
| 333001 | 用户不存在         |
| 333002 | 用户校验失败       |
| 333003 | 图片验证码错误     |
| 333004 | 手机号格式错误     |
| 333005 | 忘记设置性别啦～   |
| 333006 | 注册失败           |
| 333007 | token添加失败      |
| 333008 | 手机验证码错误     |
| 333009 | 防打扰时间非法     |
| 333010 | 设置失败           |
