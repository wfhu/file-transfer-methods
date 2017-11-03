客户端和服务端，都需要安装java



yum install java



需求：大文件需要从A.B.C.159传送到X.Y.Z.164

X.Y.Z.164 在任意目录启动服务：

`    java -jar fdt.jar -S`



A.B.C.159 开始传送文件：

`java  -jar fdt.jar -c X.Y.Z.164 -d /data/json ./23testfile`

（将A.B.C.159本地的23testfile传送到X.Y.Z.164的/data/json目录下）（2017-04-27用过，很好用，比scp快100倍以上）





加上限速：

`java  -jar fdt.jar -limit 150M  -c X.Y.Z.164 -d /data/json ./dnqf.sql.gz `





传目录：

`java  -jar fdt.jar   -c X.Y.Z.164 -d /data/json -r /export/scripts/`

（把本机的/export/scripts/目录，传送到X.Y.Z.164的/data/json目录下）

