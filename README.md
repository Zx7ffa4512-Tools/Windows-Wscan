Windows-Wscan
=============

扫网站目录
-------------------------------
    usage: wscan <-Vb> <-h host> <-f hostfile> <-p pathfile> <-t maxthread>
             <-e ext> <-c flag> <-s suffix> <-F [FIXED]@@@@> <-S startblock>
             <-r statuscode> <-l logfile> <from-len> <to-len> [charset]
       -b  is brute-forcing used custom charset
       -h  is host to scan
       -f  is path file
       -t  is max thread default is 20
       -e  is custom extend name (php)
       -c  is custom page not find(404) flag
       -s  is suffix to add scan file (.bak)
       -F  is specify a pattern, eg: @@god@@@@
       -S  is specify the starting string, eg: 03god22fs
       -r  is display the custom status code
       -l  is logfile to record
       -V  is display version info
    
    
    
    
    用10个线程扫描www.abc.com, 并记录到文件result.txt中
    wscan /h www.abc.com /p admin.txt /t 10 /l result.txt
    
    自定义扫描文件的扩展名为php,程序自动在扫描时替换
    wscan /h www.abc.com /p admin.txt /e php
    
    添加扫描后缀.bak,程序在扫描时全部追加到URL后面
    wscan /h www.abc.com /p admin.txt /s .bak
    
    自定义文件找不到时的关键字为"error", 这时线程数最好少一点
    wscan /h www.abc.com /p admin.txt /c error /t 10
    
    返加指定状态码为200的URL
    wscan /h www.abc.com /p admin.txt /r 200
    
    注: 暴力猜解必须得加上/b选项
    
    暴力猜解www.abc.com的目录,线程数为默认的20,最小长度为1,最大长度为3 默认字符集为abcdefghijklmnopqrstuvwxyz
    wscan /bh www.abc.com 1 3
    
    
    for /r %a in (*.txt) do wscan /h xdiyer.cn /p %a /l c:\result.txt
    暴力猜解www.abc.com的目录,线程数为默认的20,最小长度为1,最大长度为3 字符集为012345
    wscan /bh www.abc.com 1 3 012345
    
    也可以指定线程数
    wscan /bh www.abc.com /t 10 1 3
    
    指定填充猜解, @将被字符集填充,如果不指定最大长度,最小长度=最大长度
    wscan /bh www.abc.com /t 10 /F admin@@@ 8
    
    指定开始位置从xx字符开始，更加灵活
    wscan /bh www.abc.com /S xx 2
    
    显示版权信息
    
    wscan /V
