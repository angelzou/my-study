>@author angelzou    
>@time 2015-04-27    
>virtuoso opensource install on window    

####virtuoso安装的英文文档：[http://virtuoso.openlinksw.com/dataspace/doc/dav/wiki/Main/VOSUsageWindows](http://virtuoso.openlinksw.com/dataspace/doc/dav/wiki/Main/VOSUsageWindows)    

##Virtuoso中文安装文档
1. 下载virtuoso pre-built版本   
virtuoso open source edition下载链接：       
[http://sourceforge.net/projects/virtuoso/files/](http://sourceforge.net/projects/virtuoso/files/)  
[http://virtuoso.openlinksw.com/dataspace/doc/dav/wiki/Main/VOSDownload](http://virtuoso.openlinksw.com/dataspace/doc/dav/wiki/Main/VOSDownload)

2. 在Window上面运行6.1.4到7.1.0版本需要`Microsoft Visual C++ 2010 Redistributable Package`；         
   运行7.2.0版本以上需要`Microsoft Visual C++ 2012 Redistributable Package`。          

3. 设置环境              
1) 英文文档推荐将下载下来的virtuoso解压后的文件放到`C:/Program Files/`（或者`C:/Program Files(x86)/`，对于32bit的virtuoso在64bit的Window系统里）。             
   本人的地址为：             
`C:\Program Files\virtuoso-opensource `         
2) 右键电脑——》属性——》高级系统设置——》环境变量——》新建，新建变量，名为：`VIRTUOSO_HOME`，值为：`C:/Program Files/virtuoso-opensource   `        
3) 编辑PATH变量，添加 `;%VIRTUOSO_HOME%/bin;%VIRTUOSO_HOME%/lib	` ,点击确认并退出               
4. 创建运行实例             
1）以管理员的身份运行命令提示符cmd。（不以管理员身份运行，在创建实例的时候会报错：`Unable to open the service control manager  > (5).`）              
2）验证virtuoso二进制，在cmd中运行命令：`virtuoso-t -?      `         
3）运行以下命令，进入`C:\Program Files\virtuoso-opensource\database`：       
         
		cd %VIRTUOSO_HOME%/database                  
4）创建一个新的window服务实例，通过以下命令：  
                  
		virtuoso-t +service create +instance "New Instance Name" +configfile virtuoso.ini               
如果存在一个virtuoso服务，上面的命令会覆盖先的实例。可以重新创建一个新的实例，通过下面的命令，即将create换为screate：   
         
		virtuoso-t +service screate +instance "New Instance Name" +configfile virtuoso.ini               
5. list/start/stop/delete命令  
             
		virtuoso-t +service list                  
		virtuoso-t +instance "Instance Name" +service start                
		virtuoso-t +instance "Instance Name" +service stop                
		virtuoso-t +instance "Instance Name" +service delete             

####(启动实例之后，在网页上面输入：http://localhost:8890/conductor/  进入管理页面)                
![virtuoso admin page img](/img/virtuoso-main.jpg)    


###说明：             
>默认管理员账户密码为：dba/dba                 
>服务器管理界面默认端口为：8890                   
>sql实例访问端口为：1111                


###参考：             
1. [http://parklize.blogspot.com/2014/08/virtuoso-triple-store-database-for.html](http://parklize.blogspot.com/2014/08/virtuoso-triple-store-database-for.html)                     
2. [http://blog.sciencenet.cn/blog-794010-636257.html](http://blog.sciencenet.cn/blog-794010-636257.html)                
