# StackOverflow 接口

## 基本接口

### 通过ID获得User信息

* url:/api/stackoverflow/getUser?key=111
* 参数： key设置为一个整数，代表User的ID
* 返回示例：

```json
{"id":111,"creationDate":"2008-08-02T03:35:55.553","lastAccessDate":"2016-08-26T19:01:26.047","views":273,"aboutMe":"<p>Writer, Filmmaker, Programmer.</p>\n\n<p>Or something like that.</p>\n","websiteUrl":"http://www.saalonmuyo.com","upVotes":661,"downVotes":3,"profileImageUrl":"","displayName":"saalon","reputation":1652,"age":38,"location":"Pittsburgh, PA"}
```
### 通过ID获得Question信息

* url:/api/stackoverflow/getQuestion?id=81945
* 参数： id设置为一个整数，代表Question的ID
* 返回示例：

```json
{"id":81945,"acceptedAnswerId":81965,"title":"Hide google Toolbar by javascript","body":"<p>Is there a way to hide the google toolbar in my browser programmable?</p>\n","tags":"<javascript><browser><google-toolbar>","score":1,"answerCount":3,"commentCount":0,"favoriteCount":-32768,"ownerUserId":-32768,"lastEditorUserId":1647898,"ownerDisplayName":"reuven","lastEditorDisplayName":"","creationDate":"2008-09-17T10:47:31.517","communityOwnedDate":"","lastActivityDate":"2013-08-02T15:22:53.537","lastEditDate":"2013-08-02T15:22:53.537","closedDate":"","viewCount":1277}
```
### 通过ID获得Answer信息

* url:/api/stackoverflow/getAnswer?id=11111
* 参数： id设置为一个整数，代表Answer的ID
* 返回示例：

```json
{"id":11111,"parentId":10324,"creationDate":"2008-08-14T14:29:34.500","lastActivityDate":"2008-08-14T14:29:34.500","communityOwnedDate":"","lastEditDate":"","closedDate":"","body":"<p>For larger Hex strings like in the example I needed to use <a href=\"http://www.cplusplus.com/reference/clibrary/cstdlib/strtoul.html\" rel=\"nofollow\">strtoul</a>.</p>\n","viewCount":-32768,"lastEditorUserId":-32768,"ownerUserId":-32768,"score":1,"favoriteCount":-32768,"commentCount":0,"ownerDisplayName":"M","lastEditorDisplayName":""}
```

### 通过ID获得User中ability字段

* url :/api/stackoverflow/getAbility?id=120
* 参数： 通过`Id`确认User，从而返回其中ability
* 返回实例:

```json
{"Contributions":{"QuestionNum":4,"Reputation":904,"AnswerNum":14,"Badge":37},"Communication":{"Co_Commentor":31,"Commentor":8,"Co_Answerer":116,"Answerer":16,"Co_Editor":3,"Editor":16,"Asker":13},"Skills":[{"c#":39},{".net":21},{"excel":16},{"ms-office":16},{"rss":15},{"syndication-feed":14},{"syndication-item":14},{"windows":12},{"utilities":12},{"filesystems":12},{"file":12},{"oracle":5},{"sqlite":5},{"visual-studio":5},{"mysql":5},{"user-interface":3},{"multithreading":3},{"msbuild":2},{"svn":2},{"cruisecontrol.net":2},{"frameworks":1},{"performance":1},{"optimization":1}]}
```

### 通过用户id获得用户提问的问题列表

* url: /api/stackoverflow/getQuestionBaseUser?Id=254&pageId=1&pageSize=2

* 参数：Id：通过Id指定用户，pageSize表示每页显示的数量，pageId表示要返回的页码。后两个参数可以缺少，默认`pageId=1&pageSize=10`。

* 返回示例

  ```json
  {"questions":[{"id":2425577,"acceptedAnswerId":2425837,"title":"Example of SimpleModal with ASP.NET webforms project","body":"<p>I'm looking for a example or article that demonstrates using SimpleModal in an ASP.NET webforms project.  </p>\n\n<p>Ideally the article would show creates and edits of a grid row using simplemodal.</p>\n","tags":"<asp.net><simplemodal><webforms>","score":2,"answerCount":2,"commentCount":2,"favoriteCount":-32768,"ownerUserId":254,"lastEditorUserId":254,"ownerDisplayName":"","lastEditorDisplayName":"","creationDate":"2010-03-11T14:13:52.043","communityOwnedDate":"","lastActivityDate":"2010-03-12T09:33:28.193","lastEditDate":"2010-03-12T09:33:28.193","closedDate":"","viewCount":1808},{"id":368154,"acceptedAnswerId":-32768,"title":"I require a MSI Custom action that copies a file from the MSI source directory","body":"<p>I'm creating a installer for a c# windows project using VS 2008. I'm trying to write a custom action that copies a settings file from the source directory of the MSI file stored on a file server (e.g. \\server\\fileshare\\myappinstaller\\mysetting.xml) to the target directory on the computer on which my application is been installed (e.g. C:\\Program Files\\My App). </p>\n\n<p>The settings file can't be added in to the installer as it will contain settings with will be unique to the customer installing the app. </p>\n\n<p>Does anyone have code (preferably C# or VB.NET) for such a custom action? Alternately does anyone know how to get the MSI source location (e.g. \\server\\fileshare\\myappinstaller) within a custom action.</p>\n\n<p>Many thanks</p>\n","tags":"<c#><installer><windows-installer><custom-action>","score":5,"answerCount":4,"commentCount":0,"favoriteCount":2,"ownerUserId":254,"lastEditorUserId":254,"ownerDisplayName":"","lastEditorDisplayName":"","creationDate":"2008-12-15T12:00:00.827","communityOwnedDate":"","lastActivityDate":"2010-01-19T15:40:50.963","lastEditDate":"2008-12-15T14:49:54.137","closedDate":"","viewCount":6126}],"numQuestions":18,"numPages":9}
  ```

  ​

## 统计接口

### User随时间分布

* url:/api/stackoverflow/getNumberofUser
* 静态地址(建议使用):/data/stackoverflow/NumberofUser.json
* 参数： 无

### Answer随时间分布

* url:/api/stackoverflow/getNumberofAnswer
* 静态地址(建议使用):/data/stackoverflow/NumberofAnswer.json
* 参数： 无

### Question随时间分布

* url:/api/stackoverflow/getNumberofQuestion
* 静态地址(建议使用):/data/stackoverflow/NumberofQuestion.json
* 参数： 无

### Comment随时间分布

* url:/api/stackoverflow/getNumberofComment
* 静态地址(建议使用):/data/stackoverflow/NumberofComment.json
* 参数: 无

### 获得Top k的流行Tags的内容和问题数目

* url:/api/stackoverflow/getPopularTags?topk=10
* 参数: topk设置一个整数代表需要的前topk个流行Tag
* 返回示例：

```json
{"javascript":"1206351","java":"1128845","c#":"997482","php":"969729","android":"887040","jquery":"770022","python":"624031","html":"572569","c++":"467189","ios":"457184"}
```
### 获得开发者活跃时间段，统计一周七天的回答数

* url(静态): /data/stackoverflow/NumberofWeek.json

## 搜索接口

### 搜索User

#### SearchUser1

* url :/api/stackoverflow/SearchUser1?name=victoria&pageId=1&pageSize=2
* 参数：name搜索用户关键字。pageSize表示每页显示的数量，pageId表示要返回的页码。后两个参数可以缺少，默认`pageId=1&pageSize=10`。
* 特点：速度可能慢。没有频度限制
* 返回示例

```json
{"users":[{"id":37014,"creationDate":"2008-11-12T17:28:30.043","lastAccessDate":"2016-05-18T20:52:20.337","views":218,"aboutMe":"<p>wondering.</p>\n","websiteUrl":"http://none","upVotes":129,"downVotes":58,"profileImageUrl":"","displayName":"victoriah","reputation":1175,"age":27,"location":"Sweden"},{"id":117889,"creationDate":"2009-06-05T09:56:48.127","lastAccessDate":"2016-09-02T16:14:38.733","views":41,"aboutMe":"","websiteUrl":"http://www.victoriac.net","upVotes":9,"downVotes":0,"profileImageUrl":"","displayName":"VictoriaChan","reputation":171,"age":-32768,"location":"Oxford, United Kingdom"}],"hasMore":true}
```

#### SearchUser2(结合官方API和自己数据库)

* url: /api/stackoverflow/SearchUser2?name=victoria&pageId=1&pageSize=3
* 参数同上
* 特点:速度比较稳定。但是可能每页内容少于pageSize，有频度限制。
* 返回示例

```json
{"users":[{"id":37014,"creationDate":"2008-11-12T17:28:30.043","lastAccessDate":"2016-05-18T20:52:20.337","views":218,"aboutMe":"<p>wondering.</p>\n","websiteUrl":"http://none","upVotes":129,"downVotes":58,"profileImageUrl":"","displayName":"victoriah","reputation":1175,"age":27,"location":"Sweden"},{"id":1342581,"creationDate":"2012-04-18T21:50:51.580","lastAccessDate":"2016-08-29T21:18:15.630","views":217,"aboutMe":"","websiteUrl":"http://www.6vstudio.com","upVotes":178,"downVotes":15,"profileImageUrl":"https://i.stack.imgur.com/3UuMS.jpg","displayName":"vic3685","reputation":756,"age":-32768,"location":""},{"id":1267404,"creationDate":"2012-03-13T19:58:17.267","lastAccessDate":"2016-09-01T14:23:04.690","views":191,"aboutMe":"","websiteUrl":"","upVotes":211,"downVotes":4,"profileImageUrl":"","displayName":"Agafonova Victoria","reputation":741,"age":29,"location":"Moscow, Russia"}],"hasMore":true}
```

### 搜索Question

* url: /api/stackoverflow/SearchQuestion?content=i%20find%20bug&pageId=1&pageSize=1
* 参数：content为搜索内容。pageSize表示每页显示的数量，pageId表示要返回的页码。后两个参数可以缺少，默认`pageId=1&pageSize=10`。
* 返回示例

```json
{"questions":[{"id":11394712,"acceptedAnswerId":-32768,"title":"libv4l2: error turning on stream: No space left on device","body":"<p>I try to get stereo pair for opencv. I connect Logitech B910 and Logitech C910 webcams to usb. But have this error. I played with quirks parametrs and set <code>outfmt=mjpeg</code> in mplayer, but have this error again.</p>\n\n<p>Where can I find bug in uvcvideo or usb drivers? What monitoring or debuging tools I should use?</p>\n","tags":"<linux><usb><webcam>","score":6,"answerCount":5,"commentCount":3,"favoriteCount":1,"ownerUserId":891699,"lastEditorUserId":891699,"ownerDisplayName":"","lastEditorDisplayName":"","creationDate":"2012-07-09T12:08:48.393","communityOwnedDate":"","lastActivityDate":"2015-03-05T09:09:59.303","lastEditDate":"2015-03-03T18:39:20.860","closedDate":"","viewCount":9153}],"hasMore":true}
```



### SO官方搜索API

#### search user

* reference: https://api.stackexchange.com/docs/users
* example: https://api.stackexchange.com/2.2/users?page=1&pagesize=2&order=desc&sort=reputation&inname=tom&site=stackoverflow

#### search problems

* reference: http://api.stackexchange.com/docs/advanced-search
* example: http://api.stackexchange.com/2.2/search/advanced?page=1&pagesize=3&order=desc&sort=activity&body=change&title=cpp&site=stackoverflow

#### 关于认证

* 不认证的情况下，30/s  10,000/day per ip。**已经能满足需求**，而且认证的话，速度限制不变，只是不是依照IP限制，而是依照每个用户ID。

## 筛选接口

### 通过tag能力，返回值高的user

* url: `/api/stackoverflow/OrderByAbility?tag=cpp&pageId=1&pageSize=10`

* 参数: `tag`现在一共可选的36个，分别是：`javascript`, `java`, `c#`, `php`, `android`, `jquery`, `python`, `html`, `c++`, `ios`, `css`, `mysql`, `sql`, `asp.net`, `objective-c`, `ruby-on-rails`, `.net`, `c`, `angularjs`, `arrays`, `iphone`, `sql-server`, `json`, `ruby`, `r`, `node.js`, `ajax`, `regex`, `xml`, `asp.net-mvc`, `linux`, `swift`, `django`, `wpf`, `database`, `excel`。pageId pageSize分别表示第几页，每页显示多少。可以缺省，默认为pageId=1&pageSize=10

* 返回：

  ```json
  [{"922184":28148},{"34509":10050},{"596781":8156},{"179910":8151},{"151292":7220},{"560648":7166},{"576911":7107},{"168288":7018},{"36565":6809},{"13005":6598}]
  ```

  ​