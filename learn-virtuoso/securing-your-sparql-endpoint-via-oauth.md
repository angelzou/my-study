##通过OAuth来确保SPARQL终端的安全性

###步骤
1. 在浏览器中输入http://<cname>:<port>/conductor, (<cname>:<port>更改为你本地的服务器值)
2. 以dba或者其它的拥有DBA权限的用户名登陆
3. 安装需要的包。System Admin——>Packages。安装  [ods _ framework_dav.vad](http://s3.amazonaws.com/opldownload/uda/vad-packages/6.1/virtuoso/ods_framework_dav.vad)
4. 添加用户账户。System Admin——>User Accounts——>Create New Account
	
		Acount name: demo1
		User Login: demo1
		Password: ****
		Confirm Password: ****
		User type: SQL/ODBC and WebDAV
		Acount Roles: SPARQL_UPDATE

	填入上列信息后，点击保存。

5. 在浏览器中输入http://<cname>:<port>/oauth/
6. 点击OAthuh keys链接，已demo1用户名登陆，进入OAuth应用注册表单页面。
7. Application name列表中，选择SPARQL，然后点击Generate Keys。SPARQL客户端秘钥将会生成。
8. 点击Back to main menu链接，返回主页面.
9. 点击Protected SPARQL Endpoint链接，进入OpenLink Virtuoso SPARQL Query表单页面
10. 在Query text中输入查询语句；在OAuth token处填入步骤7中生成的Token值；最后点击Run Query按钮。
11. 进入OAuth Authorization Service表单页面，输入demo1及密码，点击登录按钮，然后authorize这个查询请求。如果查询语句正确，则会显示查询结果。   

   
####英文文档：    
[Securing your SPARQL Endpoint via OAuth](http://virtuoso.openlinksw.com/dataspace/doc/dav/wiki/Main/VirtOAuthSPARQL)  
[16.2.3.4 Service Endpoint Security](http://docs.openlinksw.com/virtuoso/rdfsparql.html#rdfsparqlprotocolendpoint)   
   

####开源的SPARQL HTTP Client：   
[BorderCloud](https://github.com/BorderCloud/SPARQL) (可以写接口访问Virtuoso)