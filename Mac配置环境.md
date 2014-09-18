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