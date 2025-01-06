### linux 查看文件大小

du [参数]...[文件]...

-a：显示目录中所有文件大小，还显示其下目录和文件占用磁盘空间的大小
-h：以易读方式显示文件大小
-s：显示目录占用磁盘空间大小，不显示其下子目录和文件占用的磁盘空间大小


### find 全盘搜索命令
find / -name [file]

## Check the port

``` shell
sudo lsof -i -P | grep LISTEN | grep :$PORT

sudo lsof -n -i -P | grep TCP
```