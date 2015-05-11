##禁用默认的SPARQL终端  

   
###方法1. 使用Conductor UI界面
1. 在浏览器输入http://cname:port/conductor
2. 输入dba用户认证进入Conductor UI界面
3. 选择Web Application Sever——>Virtual Domains & Directories
4. 找到“/sparql”逻辑路径，在Action一列中，点击Edit按钮
![img](../img/virtual-domains-directories.jpg)
5. 将VSP User的值改为“nobody”   
![disable](../img/disable-sparql-endpoint.jpg)
6. 点击“Save Changes”
7. 默认的SPARQL终端即被禁用了

###方法2. 使用iSQL
1. 禁用/sparql,执行
 
		DB.DBA.VHOST_REMOVE (lpath=>'/sparql');

2. 通过PL添加终端，执行：

		DB.DBA.VHOST_DEFINE (lpath=>'/sparql/', ppath => '/!sparql/', is_dav => 1, vsp_user => 'dba', opts => vector('noinherit', 1));
   
    

####英文文档：    
[16.2.3.4.7. Disable Default SPARQL Endpoint](http://docs.openlinksw.com/virtuoso/rdfsparql.html#rdfsparqlprotocolendpoint)