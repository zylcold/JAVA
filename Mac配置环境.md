# Mac配置环境

<!-- create time: 2014-09-18 21:13:17  -->

##nginx搭建

 1. 下载[安装包](http://nginx.org/en/download.html)
 2. 解压压缩包，并进入
 3. 终端运行 ./configure --without-http_rewrite_module
 4. make && make install
 5. sudo /usr/local/nginx/sbin/nginx
 6. 浏览器访问 localhost
 
 打开nginx sudo /usr/local/nginx/sbin/nginx
 
 重新加载|重启|停止|退出 nginx sudo /usr/local/nginx/sbin/nginx -s reload|reopen|stop|quit
 
 
 打开nginx后，默认的访问端口 80，如果要改为常用端口，则要修改 “/usr/local/etc/nginx/nginx.conf” 下监听(listen)端口值。
默认的文件访问目录(root)是 “/usr/local/nginx/html”。                 


##配置Apache服务器

* 启动
sudo apachectl -k start
* 重新启动
sudo apachectl -k restart

启动成功后，直接通过浏览器，输入localhost就可以访问默认设置文件夹。

* 修改Apache的配置文件

cd /etc/apache2/   //进入Apache配置文件所在文件夹

sudo vim httpd.conf   //使用vim编辑器打开配置文件

/DocumentRoot  //查找DocumentRoot标签，修改其中的路径文件。路径文件最好在~/文件夹下，设置~/xxx/下的路径，访问时提示，无权限访问


##配置PHP支持

* 修改Apache的配置文件

cd /etc/apache2/

sudo vim httpd.conf

/php    //使用vim找到php的标签，并打开php服务

* 修改保存后复制php.ini

cd /ect/

sudo cp php.ini.default php.ini  //将php.ini.default拷贝一份到php.ini
//如果有其他php.ini.default-xxx-文件，拷贝这个文件。

* 重启Apache服务。
 
 



