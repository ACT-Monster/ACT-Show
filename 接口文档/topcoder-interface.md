# TopCoder 接口

## 基本接口

### 根据User的handle 或者userId获得User信息

* url:/api/topcoder/getUser?key=-meko-&isId=0

  或者 /api/topcoder/getUser?key=36901&isId=1

* 参数：isId=0，表示用handle查询用户。isId=1，表示用userId查询。isId可以缺省，缺省值为0.

* 返回示例：

```json
{"handle":"-meko-","competitionNums":1,"memberSince":"2015-11-06T10:58:00.000-05:00","country":"United States","quote":"","winNums":0,"submissionNums":0,"photoLink":"","skill":["Geometry","Machine Learning","Compression","Brute Force","Sorting","User Experience (Ux)","User Interface (Ui)","Python","User Testing","Search","SQL Server","Recursion","Mobile Design","String Manipulation","MySql","String Parsing","Responsive Design","Graph Theory","Dynamic Programming","Website Design","Graphic Design","Greedy","Photoshop","Java","Simple Math","Advanced Math","JavaScript","Simulation","PostgreSQL","Android"]}
```
### 根据Challenge的challengeName获得Challenge信息

* url:/api/topcoder/getChallengeItem?challengeName=11
* 参数：challengeName为一个字符串代表challenge的name 
* 返回示例：

```json
{"challengeName":"11","challengeType":"Web Design","numRegistrants":0,"reliabilityBonus":0,"numSubmissions":0,"duration":1,"prize":"1","postingDate":"2009-02-12T20:00:00.000-05:00","registrationEndDate":"2009-02-13T20:00:00.000-05:00","submissionEndDate":"2009-02-13T20:00:00.000-05:00","appealsEndDate":"2009-02-14T20:00:00.000-05:00","finalFixEndDate":"","technology":[""],"currentStatus":"Deleted","language":[""]} 
```

### 根据userId获得User的ability字段

* url: /api/topcoder/getAbility?userId=773
* 参数： userId是用户id。返回的skill字段是有序的。
* 示例：

```json
{"contribution":{"SubNum":2,"WinNum":0,"RegNum":10},"communication":[{"hzieemin":"2:0","sin_hu":"1:0","billthu":"1:0"},{"iSpartan":6,"hanshuai":6,"AleaActaEst":4,"sampath01":32,"jol":2,"gjw99":4,"sdgun":4,"zhangtengji":2,"freegod":10,"Indemar":16,"moulyg":2,"maroosh":2,"monopoly":4,"NormalGeek":14,"Seamlyit":2,"mastraho":4,"selvamanoharan":2,"faeton":4,"delight":2,"gabyja":22,"kaygee":34,"dileepa":4,"hzieemin":4,"YiiBryan":4,"morehappiness":2,"j3_guile":70,"tanke":4,"sin_hu":3,"argolite":16,"slavik990":2,"billthu":7,"yyne":2,"liumei":2,"seeef":20,"vivekagarwal":2,"AE-86":6,"sare":6,"monumahiya":2,"AjJi":2,"moming":2,"zsudraco":2,"babyfox":4}],"skill":[{"javascript":2.0864},{"css":1.9594},{"html":1.9594}]}
```

### 根据userId获得用户注册的challenge列表

* url: /api/topcoder/getChallengeBaseUser?userId=33609&pageId=1&pageSize=5

* 参数: userId：通过Id指定用户，pageSize表示每页显示的数量，pageId表示要返回的页码。后两个参数可以缺少，默认`pageId=1&pageSize=10`。

* 返回示例

  ```json
  {"challenges":[{"challengeName":"NASA Free Flying Robot Mission Patch and Naming Challenge","challengeType":"Logo Design","numRegistrants":818,"reliabilityBonus":0,"numSubmissions":0,"duration":16,"prize":"1,000,500,250,250","postingDate":"2014-10-11T09:00:00.000-04:00","registrationEndDate":"2014-10-24T11:27:00.000-04:00","submissionEndDate":"2014-10-27T09:09:00.000-04:00","appealsEndDate":"2014-10-31T05:19:00.000-04:00","finalFixEndDate":"2014-10-31T18:46:00.000-04:00","technology":[""],"currentStatus":"Completed","language":[""]}],"numChallenges":1,"numPages":1}	
  ```

  ​

## 统计接口

### 获得User随时间分布情况

* url:/api/topcoder/getNumberofUser
* 静态地址(建议使用):/data/topcoder/NumberofUser.json
* 参数 : 无

### 获得ChallengeItem随时间分布情况

* url:/api/topcoder/getNumberofChallenge
* 静态地址(建议使用):/data/topcoder/NumberofChallenge.json
* 参数 : 无

### 获得User的国家分布情况

* url:/api/topcoder/getNumberofCountry
* 静态地址:/data/topcoder/NumberofCountry.json
* 参数：无

### 获得编程语言包含的项目数

* url: /api/topcoder/getChallengeNumWithLanguages
* 静态地址:/data/topcoder/LanguagesWithCountry.json
* 参数：无

## 搜索接口

### 根据用户名搜索users
* url: /api/topcoder/SearchUser?handle=luck&pageId=1&pageSize=3
* 参数:handle表示用于搜索用户的关键词，pageSize表示每页显示的数量，pageId表示要返回的页码。后两个参数可以缺少，默认`pageId=1&pageSize=10`。
* 返回示例：


```json
{"users":[{"handle":"chloearluck","competitionNums":2,"memberSince":"2014-09-13T18:53:00.000-04:00","country":"United States","quote":"","winNums":0,"submissionNums":1,"photoLink":"","skill":[""]},{"handle":"jasoncluck","competitionNums":1,"memberSince":"2015-01-03T16:11:00.000-05:00","country":"United States","quote":"","winNums":0,"submissionNums":0,"photoLink":"","skill":[""]},{"handle":"luckeri20","competitionNums":2,"memberSince":"2015-04-06T10:13:00.000-04:00","country":"Ukraine","quote":"","winNums":0,"submissionNums":0,"photoLink":"https://topcoder-prod-media.s3.amazonaws.com/member/profile/luckeri20-1449221339364.jpeg","skill":["Geometry","String Manipulation","Brute Force","String Parsing","Math","Sorting","C++","Dynamic Programming","Graph Theory","Greedy","Search","Simple Math","Simulation"]}],"hasMore":true}
```



### 根据challenge名搜索challenges
* url: /api/topcoder/SearchChallenge?challengeName=good&pageId=1&pageSize=2
* 参数: challengeName表示要搜索用户的关键词,pageSize表示每页显示的数量，pageId表示要返回的页码。后两个参数可以缺少，默认`pageId=1&pageSize=10`。
* 返回示例: 


```json
{"challenges":[{"challengeName":"$500 Logo Design for Good Carrot","challengeType":"Logo Design","numRegistrants":43,"reliabilityBonus":0,"numSubmissions":0,"duration":7,"prize":"500,100","postingDate":"2010-05-24T00:00:00.000-04:00","registrationEndDate":"2010-05-31T00:00:00.000-04:00","submissionEndDate":"2010-05-31T00:00:00.000-04:00","appealsEndDate":"2010-06-14T20:00:00.000-04:00","finalFixEndDate":"","technology":[""],"currentStatus":"Completed","language":[""]},{"challengeName":"Pick me Im a good project","challengeType":"Copilot Posting","numRegistrants":0,"reliabilityBonus":30,"numSubmissions":0,"duration":3,"prize":"150,75","postingDate":"2013-03-04T22:00:00.000-05:00","registrationEndDate":"2013-03-06T22:00:00.000-05:00","submissionEndDate":"2013-03-07T22:05:00.000-05:00","appealsEndDate":"2013-03-09T22:05:00.000-05:00","finalFixEndDate":"","technology":[""],"currentStatus":"Draft","language":[""]}],"hasMore":true}
```

## 筛选接口

### 返回所有可供筛选的tag

* url： /api/topcoder/GetTags

* 返回示例：

  ```json
  ["java","ajax","aws","html","j2ee","javascript","jsp","servlet","spring","struts","xml",".net","c#",".net 2.0","android","rest","sql","sql server 2008","angular.js","bootstrap","css","html5","jquery","json","other","web services","ibm bluemix","node.js","nodejs","php","python","data science","hp haven","vertica","ejb 3","hpe haven ondemand","http","ios 6.0","ios 8.0","swift","api","mongodb","go","ios","android 2.2","ibm db2","ibm websphere application server","ibm websphere mq","ios 4.0","ios 5.0","javabean","jpa","custom tag","ejb","jsf","apex"]
  ```

  ​

### 通过tag能力，返回能力最高的top k

* url： `/api/topcoder/OrderByAbility?tag=c&pageId=1&pageSize=11`

* 参数：tag可选项为上面获得，共191个可选。pageId pageSize分别表示第几页，每页显示多少。可以缺省，默认为pageId=1&pageSize=10

* 返回示例：

  ```json
  ["hyy5159","Reflect","charango7","alkant","qiuosier","mpanga","IhRlaeh1","Alan.Brooks","lightmare","TheKingOfWrong","xiufei"]
  ```

  ​