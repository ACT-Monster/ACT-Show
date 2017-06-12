# 跨平台相关API

## 搜索

### 跨平台搜索user

* url: /api/searchUser?type=1&content=java&platform=2&pageId=1&pageSize=3

* 参数：

  * type为0表示以profile搜索，content为搜索内容
  * platform表示搜索的平台。默认为-1，表示全平台。或者指定0-3分别代表只搜索github, statckoverflow, topcoder , csdn。
  * type为1表示按skills搜索，content以空格或者`,`隔开
  * pageId pageSize分别表示第几页，每页显示多少。可以缺省，默认为pageId=1&pageSize=10

* 返回示例

  ```json
  {"users":[{"profile":{"name":"slimani.idriss","url":"https://www.topcoder.com/members/slimani.idriss/","country":"France","joinDate":"2015-09-17","address":"","mail":"","belongTo":2},"skills":{"tag":{"pl":[],"others":[]}},"collaborations":{"loseNum":0,"collaborNum":0,"winNum":0},"userID":20634,"contributions":{"SubNum":0,"RegNum":2,"WinNum":0}},{"profile":{"name":"fastprogrammer","url":"https://www.topcoder.com/members/fastprogrammer/","country":"India","joinDate":"2005-03-07","address":"","mail":"","belongTo":2},"skills":{"tag":{"pl":["css","java","xml","html","javascript","http"],"others":["jface","servlet","jsp","custom tag","javabean","ajax","java application","oracle 10g","spring","swt","j2ee","mysql","jpa","eclipse plugin","ejb","ejb 3","swing","struts","jsf"]}},"collaborations":{"loseNum":41,"collaborNum":362,"winNum":14},"userID":7445,"contributions":{"SubNum":25,"RegNum":403,"WinNum":12}},{"profile":{"name":"jclee","url":"https://www.topcoder.com/members/jclee/","country":"Australia","joinDate":"2014-08-15","address":"","mail":"","belongTo":2},"skills":{"tag":{"pl":[],"others":[]}},"collaborations":{"loseNum":0,"collaborNum":0,"winNum":0},"userID":10394,"contributions":{"SubNum":2,"RegNum":4,"WinNum":1}}],"numPages":1951,"numUsers":5851}
  ```



### 从ES中获取某User信息

* url: /api/getUser?userId=36901&belongTo=2

* 参数: belongTo表示要获取的平台，userId是要用户ID，该ID和neo4j中每个平台的userId一致。

* 返回实例

  ```json
  {"skills":{"tag":{"pl":[],"others":[]}},"contributions":{"SubNum":0,"WinNum":0,"RegNum":1},"collaborations":{"winNum":0,"collaborNum":0,"loseNum":0},"profile":{"country":"China","joinDate":"2011-09-06","address":"","mail":"","name":"mmmmmjjjuuu","belongTo":2,"url":"https://www.topcoder.com/members/mmmmmjjjuuu/"},"userID":36901}
  ```

  ​