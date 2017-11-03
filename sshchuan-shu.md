使用rsync+ssh的方式，

rsync -avz --progress -e 'ssh -p 3600 -l root' TableLog20150\* 10.64.169.53:/data/speedtest/



![](/assets/ssh.png)

这就说明传输的瓶颈在CPU这块了，可以从协议上进行优化，比如调整加密协议，去掉压缩等\(虽然改善程序非常有限\)

-c arcfour -o Compression=no

rsync -avz --progress -e 'ssh -p 3600 -l root -c arcfour -o Compression=no' TableLog20150\* 10.64.169.53:/data/speedtest/

