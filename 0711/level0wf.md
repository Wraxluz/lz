[1.查看文件类型]()

![](https://github.com/Wraxluz/lz/blob/master/level0/a.png)

[2.拖入ida查看，read 函数有缓冲区溢出漏洞]()

![](https://github.com/Wraxluz/lz/blob/master/level0/b.png)

[3.填充为0x80字节，rbp有8个字节]()

![](https://github.com/Wraxluz/lz/blob/master/level0/c.png)

![](https://github.com/Wraxluz/lz/blob/master/level0/d.png)

[4.然后在Ox400684有system("/bin/sh")执行shell,所以写出exp]()

![](https://github.com/Wraxluz/lz/blob/master/level0/e.png)
