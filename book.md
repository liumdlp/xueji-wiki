## 书籍(book)

### isbn添加

uri: app1/book/add_book

params:

| 变量   | 名称    | 必填   | 类型      | 描述   |
| ---- | ----- | ---- | ------- | ---- |
| isbn | ISBN码 | 是    | int(13) | 默认：0 |

请求示例：http://47.52.101.29/app1/book/add_book?isbn=9787020033430

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "id": 39,
        "title": "哈利·波特与魔法石",
        "isbn": 9787020033430,
        "cover_img": "https://img3.doubanio.com/mpic/s1990480.jpg",
        "author_first": "[英] J. K. 罗琳",
        "author_all": "[\"[\\u82f1] J. K. \\u7f57\\u7433\"]",
        "publisher": "人民文学出版社",
        "pubdate": "2000-9",
        "douban_id": 1041007
    }
}
```

response 说明：

| 字段                | 名称    | 说明                  |
| ----------------- | ----- | ------------------- |
| code              | 状态码   | 0:正常,333201:书籍不存在   |
| msg               | 消息    | 请求正常为"ok",否则为详细错误信息 |
| data.id           | 书籍id  |                     |
| data.title        | 书名    |                     |
| data.isbn         | ISBN码 |                     |
| data.cover_img    | 封面    | 封面URL地址             |
| data.author_first | 作者    | 多作者情况下，取第一位作者       |
| data.author_all   | 作者    | 全部作者，json格式         |
| data.publisher    | 出版社   |                     |
| data.pubdate      | 出版时间  |                     |
| data.douban_id    | 豆瓣id  | 对应豆瓣api的ID          |



### TODO：自定义添加

uri: app1/book/add_custom

params:

| 变量   | 名称   | 必填   | 类型   | 描述   |
| ---- | ---- | ---- | ---- | ---- |
|      |      |      |      |      |

请求示例：

response:

```json
{
}
```

response 说明：

| 字段   | 名称   | 说明   |
| ---- | ---- | ---- |
|      |      |      |



