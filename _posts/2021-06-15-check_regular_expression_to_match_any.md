---
title: "جستجوی بین دو کاراکتر توسط Regex"
date: 2021-06-15T15:31:00-00:00
categories:
  - Regex
tags:
  - regex
  - search
  - regular_expression
---

گاهی مواقع به پاک سازی یا پیدا کردن آیتم های خاصی در یک فایل نیاز هست  
بطور مثال میخواید تمام style ها رو از یک فایل html پاک کنید.  
اگه فایل هم حجم زیادی داشته باشه، پیدا کردن و پاک کردن همه اون آیتم ها وقت زیادی میخواد.  
  
راحت ترین راه برای این کار استفاده از Regex هست. برای این کار کافی هست در قسمت جستجو ادیتور خودتون متن زیر رو در حالتی که ریجکس روشن هست جستجو کنید :  

```c#
style="([^]*)"
```

در متن بالا:  
کلمه `style="` متن شروع هست و هرچی میتونه باشه  
قسمت مهم بخش `([^*])` هست. این بخش بصورت کلی به معنی هر کاراکتر معنی میشه و باعث میشه تمام کاراکترهای بین دو " و " صرف نظر بشن

برای تست آنلاین ریجکس میتونید از سایت زیر استفاده کنید:  

[regexr](https://regexr.com/)  

برای یاد گرفتن ریجکس هم سایت زیر مفید هستش:  

[learn-regex](https://github.com/ziishaned/learn-regex)  