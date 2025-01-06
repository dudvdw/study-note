### 启动Nginx出现这个错误
nginx: [error] open() "/usr/local/var/run/nginx.pid" failed (2: No such file or directory)

// 运行
sudo nginx -c /usr/local/etc/nginx/nginx.conf

// 再运行
nginx -s reload

### mac 解决Nginx出现403 forbidden的方法

在 Nginx + PHP-fpm File not found.问题解决记录 过程中，遇到Nginx出现403 forbidden的问题，

403 就是权限问题，

在

/opt/local/etc/nginx/nginx.conf

开始加一行
user root;

没用报

nginx: [emerg] getgrnam("root") failed in xxx:1

继续搜索发现有人这样做在/usr/local/nginx/conf/nginx.conf开始加一行

user root root;还是报错nginx: [emerg] getgrnam("root") failed in /usr/local/nginx/conf/nginx.conf:1

最后

发现应该加 user root owner;

重新加载配置文件

nginx -s reload


### Can't restart nginx
check which port is occupied, then kill it:

``` shell
kill $(lsof -t -i:80)
```