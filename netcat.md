## 使用netcat/nc和pipe view/pv来测试网络传输速率

  


### 1、客户端从服务端拉取文件：

服务端配置：

`# cat TableLog20150210.MYD | pv -rb | nc -l 33333`

`1.83GiB [36.6MiB/s]`



客户端拉取：

`# nc 10.67.16.106 33333 | pv -rb > abc.txt`

`1.83GiB [ 112MiB/s]`



#### 可加上tar对文件夹传输进行压缩

服务端：

`tar -cf - . | pv -rb | nc -l 33333`



客户端：

`nc 192.168.0.71 33333 | pv -rb | tar -xvf -`



### 2、客户端将文件推送至服务端：

服务端配置：

`# nc -l 8888 | pv -rb > file.tar`

`1.83GiB [88.2MiB/s]`



客户端配置：

`# cat abc.txt | pv -rb | nc 10.67.16.106 8888`

`1.83GiB [ 112MiB/s]`



