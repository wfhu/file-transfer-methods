







使用rsync+ssh的方式，如果特别慢，有可能是因为SSH加密解密导致过渡使用CPU造成的（cpu intensive）

rsync -avz --progress -e 'ssh -p 3600 -l root' TableLog20150\* 10.64.169.53:/data/speedtest/

  


  


top中如果有以下显示：

Cpu8 

:100.0%us, 

0.0%sy, 

0.0%ni, 

0.0%id, 

0.0%wa, 

0.0%hi, 

0.0%si, 

0.0%st

  


 PID USER 

PR 

NI 

VIRT 

RES 

SHR S %CPU %MEM 

TIME+ 

COMMAND 

3415 root 

20 

 0 

111m 2188 1396 R 100.0 

0.0 

 0:59.32 rsync 

  


![](/assets/ssh.png)

  


  


这就说明传输的瓶颈在CPU这块了，可以从协议上进行优化，比如调整加密协议，去掉压缩等\(虽然改善程序非常有限\)

-c arcfour -o Compression=no

  


rsync -avz --progress -e 'ssh -p 3600 -l root -c arcfour -o Compression=no' TableLog20150\* 10.64.169.53:/data/speedtest/

  


