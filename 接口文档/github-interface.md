# GitHub 接口

## 基本接口

### 通过login获得User信息

* url:/api/github/getUser?key=luckcul&isId=0

  或者 /api/github/getUser?key=1110&isId=1

* 参数： isId=0,表示通过用户名获得user。isId=1,表示通过userId获得user。isId可以缺省，缺省值为0.

* 返回示例：

```json
{"country":"\\N","city":"\\N","created_at":"2015-01-01 13:52:46","login":"luckcul","type":"USR","country_code":"\\N","company":"\\N","language":["\\N","CSS","HTML","C++","Python"]}
```

### 通过Project的url获取Project信息

* url: /api/github/getProject?url=https://api.github.com/repos/dionyziz/canvas-tetris
* 参数: url，项目的唯一标识
* 返回示例

```json
{"name":"canvas-tetris","language":"JavaScript","created_at":"2012-05-22 18:31:39","updated_at":"2016-02-13 21:01:59","descriptor":"A 2D tetris game in HTML5 canvas","url":"https://api.github.com/repos/dionyziz/canvas-tetris"}
```



### 获得两个User的Follow关系

* url:/api/github/follow?user1=cxlove&user2=rolight
* 参数: user1为一个User的login，user2为另一个User的login
* 返回示例：

```json
{"user1":"cxlove","user2":"rolight","created_at":"2014-11-18 06:08:43"}
```

### 某人的社交关系（一层）

* url: /api/github/subGraph?user=winter&depth=1&width=4
* 参数说明：

 user: 用户的ID
 depth: 以用户为中心扩展的层数
 width: 每个用户扩展的follow数
* 返回示例: 可以实时查询，参数建议 depth=2&width=4

```json
{"nodes":[{"category":0,"name":"winter","value":3},{"category":1,"name":"free1","value":3},{"category":1,"name":"ahmetabdi","value":3}],"links":[{"source":0,"target":1,"weight":2},{"source":0,"target":2,"weight":2},{"source":2,"target":1,"weight":2}]}
```
### 根据userId获得用户拥有的Project

* url: /api/github/getProjectBaseUser?userId=111&pageId=1&pageSize=3

* 参数：userId：通过Id指定用户，pageSize表示每页显示的数量，pageId表示要返回的页码。后两个参数可以缺少，默认`pageId=1&pageSize=10`。

* 返回示例

  ```json
  {"projects":[{"name":"opencv_wiki","language":"\\N","created_at":"2016-03-09 15:11:51","updated_at":"0000-00-00 00:00:00","descriptor":"Separate repository for OpenCV wiki","url":"https://api.github.com/repos/Itseez/opencv_wiki"},{"name":"jetson-screencasts-sources","language":"C++","created_at":"2015-10-13 10:10:29","updated_at":"2016-02-20 20:12:55","descriptor":"","url":"https://api.github.com/repos/Itseez/jetson-screencasts-sources"},{"name":"opencv_3rdparty","language":"\\N","created_at":"2015-07-01 14:32:58","updated_at":"2016-02-20 20:12:55","descriptor":"OpenCV - 3rdparty","url":"https://api.github.com/repos/Itseez/opencv_3rdparty"}],"numProjects":9,"numPages":3}
  ```

  ​

## 统计接口

### GitHub开发者数量

* url: /api/github/getNumberofUser
* 静态地址：/data/github/NumberofUser.json
* 参数说明：
* 当前返回:

```json
 {"2009":43150,"2008":3,"2017":13914686,"2016":10980910,"2015":7467859,"2014":4986857,"2013":3081612,"2012":1266731,"2011":523398,"2010":170312}
```

### GitHub项目数量

*　url: /api/github/getNumberofProject
*　静态地址：/data/github/NumberofProject.json
*　参数说明：
*　当前返回:

```json
{"2009":30720,"2008":3,"2017":37728657,"2016":25873158,"2015":13721490,"2014":7628934,"2013":2967190,"2012":1126821,"2011":466524,"2010":158557}
```

### Github开发者国家分布

* url: 无
* 静态地址：/data/github/NumberofCountry.json
* 参数说明： 无

### 常用编程语言(全部项目的语言统计 )

* url:
* 静态地址:/data/github/langStatics.json
* 参数说明：

### commit 活跃度统计

* url: 无
* 静态地址:/data/github/commitDateStatistics.json
* 参数: 无

## 搜索接口

### 根据用户名搜索users

#### SearchUser1(完全基于自己数据库)

* url: /api/github/SearchUser1?name=vczh&pageId=1&pageSize=2
* 参数：name搜索的用户关键词,pageSize表示每页显示的数量，pageId表示要返回的页码。后两个参数可以缺少，默认`pageId=1&pageSize=10`。
* 特点：优点，没次数限制。缺点：速度有时候比较慢，photoLink字段为空，出于效率考虑language字段也为空。
* 返回示例

```json
{"users":[{"country":"Seattle, WA, USA","city":"Seattle","created_at":"2011-05-07 06:30:48","login":"vczh","type":"USR","country_code":"us","company":"\\N","photoLink":null,"language":null},{"country":"hangzhou","city":"杭州市","created_at":"2014-07-05 06:42:11","login":"vczhfan","type":"USR","country_code":"cn","company":"zju","photoLink":null,"language":null}],"hasMore":true}
```

#### SearchUser2(基于官方API和自己数据库)

* url: /api/github/SearchUser2?name=vczh&pageId=1&pageSize=2
* 参数选项同上
* 特点：优点：速度可以，有photoLink、language字段。缺点：速度限制30/min,每页返回的结果可能少于预定的pageSize
* 返回示例

```json
{"users":[{"country":"Seattle, WA, USA","city":"Seattle","created_at":"2011-05-07 06:30:48","login":"vczh","type":"USR","country_code":"us","company":"\\N","photoLink":"https://avatars0.githubusercontent.com/u/773569?v=3","language":["C++","JavaScript","C#","Go","\\N"]}],"hasMore":true}
```



### 根据项目名搜索项目

#### SearchProject1(完全基于自己数据库)

* url : /api/github/SearchProject1?name=good&pageId=1&pageSize=2
* 参数：name为搜索的项目关键词，pageSize表示每页显示的数量，pageId表示要返回的页码。后两个参数可以缺少，默认`pageId=1&pageSize=10`。
* 特点：优点：没有访问次数限制。缺点：可能比较慢
* 返回实例

```json
{"projects":[{"name":"gooddata-python","language":"Python","created_at":"2011-02-12 13:46:02","updated_at":"2016-02-11 11:19:55","descriptor":"GoodData client library written in python.","url":"https://api.github.com/repos/comoga/gooddata-python"},{"name":"gooddata-python","language":"Python","created_at":"2012-09-19 04:42:11","updated_at":"2016-02-28 12:31:24","descriptor":"GoodData client library written in python.","url":"https://api.github.com/repos/mjhea0/gooddata-python"}],"hasMore":true}
```

#### SearchProject2(基于官方API和自己数据库内容)

* url: /api/github/SearchProject2?name=good&pageId=1&pageSize=2
* 参数同上
* 特点：优点：速度比较稳定的快。缺点，有速度限制30/min，每页返回结果可能少于预定的pageSize
* 返回示例

```json
{"projects":[{"name":"good","language":"JavaScript","created_at":"2012-12-10 19:57:30","updated_at":"2016-02-18 13:16:34","descriptor":"Hapi process monitoring","url":"https://api.github.com/repos/hapijs/good"},{"name":"good","language":"\\N","created_at":"2013-09-11 22:08:29","updated_at":"2016-02-15 06:47:24","descriptor":"The short list.","url":"https://api.github.com/repos/ElDragonRojo/good"}],"hasMore":true}
```



### Github官方搜索API

#### search user

* reference： https://developer.github.com/v3/search/#search-users
* example: https://api.github.com/search/users?q=tom&page=2&per_page=5

#### search repositories

* reference: https://developer.github.com/v3/search/#search-repositories
* example:  https://api.github.com/search/repositories?q=tetris&sort=stars&order=desc&page=2&per_page=5


#### 关于认证

* reference : https://developer.github.com/v3/#authentication
* **完成了认证**。目前建议使用OAuth2 Key/Secret方式。 在github api后面加上`&client_id=8c77acd5ff3d574eb164&client_secret=d6977df80b8becda3b335d9a77f28c3d961c95ae`
* 目前rate limit: 30/min, 5000/h




