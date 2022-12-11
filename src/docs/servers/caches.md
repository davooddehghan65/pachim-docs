---
title : "کش در سرور"
---

# کش

### جدول محتوا

## بررسی اجمالی

زمانی که شما یک [اپلیکیشن سرور](/servers/types#سرور-اپلیکیشن) یا [کش سرور](/servers/types#سرور-کش) راه اندازی می‌کنید، پَچیم به شکل اتوماتیک [memcache](https://www.memcached.org/) و [redis](https://redis.io/) را بر روی سرور شما نصب می‌کند. به شکلی پیش فرض هیچ کدام از این دو سرویس از طریق خارج از سرور قابل دسترس نیستند و تنها از داخل خود سرور به آن‌ها می‌توانید دسترسی داشته باشید به غیر از اینکه [تنظیمات شبکه سرور](/servers/network) راه از طریق پنل پَچیم تغییر دهید.

## اتصال به redis

هم Redis و هم Memcache هر دو از طریق IP داخلی 127.0.0.1 و پورت‌های خودشان در دسترس شما قرار میگیرند.

```shell
MEMCACHED_HOST=127.0.0.1
MEMCACHED_PORT=11211

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379
```

:::note{.tip}

::title[قرار دادن پسورد برای Redis]

شما می‌توانید برای Redis پسورد قرار دهید تا امنیت آن را افزایش دهید، برای انجام این کار می‌توانید وارد مدیریت دیتابیس‌ها در پنل سرور پَچیم و وارد مدیریت دیتابیس Redis شوید. در یک باکس با عنوان پسور Redis می‌توانید این پسورد را مدیریت کنید.
:::


:::note{.warning}

::title[اتصال به سرور کش]

در سرور کش به شکل پیش فرض redis و memcache از خارج از سرور در دسترس نیستند، شما می‌توانید وارد قسمت [`مدیریت شبکه سرور`](/servers/network) خود شوید و از بخش ارتباط بین سرورها امکان دسترسی سرورهای دیگر به این سرور کش را به وجود آورید.

:::



## اتصال به redis از خارج سرور

شما همانند اتصال به دیتابیس‌های خود از خارج از سرور و از طریق نرم افزارهای گرافیکی همچون TablePlus می‌توانید حالا به Redis هم از طریق این نرم افزار متصل شده و اطلاعات آن را مشاهده یا مدیریت کنید.

دقت کنید برای اتصال به redis نیاز به دسترسی SSH دارید. اگر هنوز کلید SSH خود را به کلید‌های SSH که به سرور دسترسی دارند اضافه نکرده‌اید، پشنهاد می‌کنیم در ابتدا حتما اینکار را از طریق [مدیریت SSH Key](#) در پَچیم انجام دهید. 

![اتصال به redis](/img/redis.png)

در تصویر بالا در ایجاد Redis Connection به یک سری اطلاعات نیازمند هستید که در زیر آنها رو به شما توضیح خواهیم داد :


- **Name** : این یک نام شخصی سازی شده است و هر چه که مایل باشید می‌توانید وارد کنید.
- **Host** : این مقدار باید معادل `127.0.0.1` باشد و مقدار دیگری قرار ندهید.
- **User** : نام کاربری را خالی بگذارید، به شکل پیش فرض به آن نیاز نداریم.
- **Password** : اگر از طریق پنل کاربری پَچیم برای دیتابیس Redis پسورد قرار داده‌اید آن پسورد را این قسمت وارد کنید.
- **Over SSH** : اتصال به دیتابیس تنها از طریق SSH انجام می‌شود، بنابراین تیک این گزینه را فعال کنید.
- **Server** : آی پی سرور خود را در این قسمت قرار دهید
- **Port** : پورت SSH در این قسمت به شکل پیش فرض 22 است اگر پورت دیگری دارید در این قسمت اعمال کنید.
- **Use SSH Key** : برای احرازهویت با کلید SSH تیک این گزینه را فعال کنید
- **SSH private Key** : روی این گزینه کلیک کنید و کلید private مربوط به SSH سیستم خود را انتخاب کنید، دقت کنید کلید خصوصی و نه کلید عمومی.