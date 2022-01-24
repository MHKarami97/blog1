---
title: "پاس دادن Enum به عنوان ورودی به HTTP GET"
date: 2022-01-23T09:00:00-00:00
categories:
  - Net
tags:
  - net
  - enum
  - httpget
  - required
---

در صورتی که می‌خواهید یک Enum را به یکی API که بصورت HTTPGET است، پاس بدهید، حواستان باشد که بصورت پیش فرض معتبر بودن ورودی آن بررسی نمی‌شود.  
بطور مثال کد زیر را درنظر بگیرد:  

```c#
[HttpGet]
public async Task<ApiResult<List<ResultVm>>> GetPublicWatchItems(MyEnum watch)
```

```c#
public enum MyEnum
{
	[Description("بیشترین تاثیر")]
	MaxIndexAffect = 1,

	[Description("بیشترین حجم")]
	MaxVolumeAmount = 2,
}
```

در صورتی که مقادیر زیر را به آن پاس بدهید که در حالت اول نام اشتباه است و در حالت دوم مقدار معتبر نیست، با خطا مواجه نمی‌شوید و برنامه به کار خود ادامه می‌دهد.  

```c#
api/MyController/GetPublicWatchItems?id=2
api/MyController/GetPublicWatchItems?watch=0
```

پس یا باید مقدار آن را بررسی کنید و یا از `[Required]` استفاده کنید.  

```c#
[HttpGet]
public async Task<ApiResult<List<ResultVm>>> GetPublicWatchItems([Required] MyEnum watch)
```

روش دوم:  

```c#
[HttpGet("{watch}")]
public async Task<ApiResult<List<ResultVm>>> GetPublicWatchItems(MyEnum watch)
```

که در این حالت ورودی باید بصورت زیر باشد که اگر مقدار آن داده نشود با خطا مواجه می‌شوید.  

```c#
api/MyController/GetPublicWatchItems/2
```