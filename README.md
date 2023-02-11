<div align="center"><img src="https://github.com/Eilllia/Saturn/blob/main/Saturn.png" height="250" textAlign="center"/></div>

<h1 align="center">Saturn</h1>
<h3 align="center">Saturn VPN - How to bypass filtering?</h3>

---




### آموزش قدم به قدم دور زدن فیلترینگ با وجود محدودیت های جدید اینترنت ایران
قبل از هر چیزی باید بدونیم [V2ray](https://www.v2ray.com) چیه؟ V2ray یک سرویسه با کلی امکانات که فعلا تنها راه نجات ایرانیا شناخته میشه چون رهگیری و فیلترش کار سختیه و میتونه یه کانکشن امن با پروتکل های Vless و Vmess و Http و Socks و Shadowsocks و trojan و docodemo-door واستون بسازه و باهاش به اینترنت بین الملل به راحتی متصل بشید

سرعت سرویس V2ray خوبه اما پینگ بالایی میده که خب هر چه کانفیگ سرورتون بهتر باشه پینگ بهینه تری دریافت میکنید

در حال حاضر دو پروتکل Vless و Vmess جوابگوی کاربران ایرانی هستند

تا مدتی پیش اتصال بدون tls و بدون رمزنگاری داده ها با یک certificate ممکن بود. اما هم اکنون کانکشن های بدون tls محدود شدند و تنها راه اتصال امن داشتن tls در کانفیگ هست

اما خب حالا سوال پیش میاد tls از کجامون بیاریم؟

یا حتی برخی عزیزان بنیادی تر میپرسن چطوری v2ray راه اندازی کنیم؟

اینجاست که میگم باید قدم به قدمم بیایید تا تنها راه نجات رو با هم طی کنیم

این آموزش به طور خلاصه راهنمای خرید سرور، هاست و دامنه و راه اندازی سرویس v2ray بر روی آن است.

بریم که داشته باشیم!

---

### قدم 1 | خرید سرور مجازی، هاست و دامین

در این آموزش پیش نیاز راه اندازی کامل و بدون مشکل سرویس وی پی ان جوابگو، داشتن یک سرور مجازی، یک هاست و یک دامین میباشد.

چنانچه استفاده شخصی دارید میتوانید هاست و دامین را از سایت های ایرانی و دامین .ir خریداری کنید، اما اگر برای استفاده عمومی میخواهید اقدام کنید برای جلوگیری از رهگیری اطلاعات فردی شما بهتر است دامین غیر ایرانی و هاست را از یک کارگزاری خارجی دریافت کنید.

خب بریم سراغ مراحل خریداری: اول از همه باید وارد سایت [Hetzner](https://www.hetzner.com/) بشید و یک اکانت درست کنید، صبر کنید! تا انتها بخونید، وقتی اکانت درست کردید باید برای تایید اکانت مدارک خود را ارسال کنید که به احتمال 90 درصد به علت تحریم ها موفق به ساخت اکانت نشوید، حتی اگر موفق هم شدید باید پرداخت دلاری انجام دهید که سایت ایرانیکارت میتواند به شما کمک کند، اما حالا اینجا دو دسته میشویم، کسانی که موفق به ساخت اکانت شدند و امکان پرداخت دلاری دارند، و دسته دوم شمایی که مثل من موفق به این کار نشدید! 

حالا بیایید با هم گریه کنیم...

شوخی کردم، اینجا لازم است که ما از یک کارگزاری ایرانی که سرور هاشو از [Hetzner](https://www.hetzner.com/) دریافت میکنه کمک بگیریم و همچنین برای هاست و دامین هم از یک سرویس میزبانی ایرانی استفاده کنیم. من اینجا بهتون دو تا آدرس میدم که سرور و هاست و دامینتون رو با مشخصاتی که میگم از اونجا بدون دردسر دریافت کنید:


یک هاست و یک دامین از سایت زیر دریافت کنید (برای ثبت دامینتون یکی دو روز معطل میشید): 

(کانفیگ هاست اهمیتی نداره فقط Cpanel باشه و نام دامنه هم به دلخواه خودتون باشه، آموزش خرید هم توی اینترنت ریخته، دیگه من که نباید بگم!)

[میهن وب هاست | mihanwebhost.com](https://mihanwebhost.com/)

و یک سرور مجازی از سایت زیر ترجیحا خریداری کنید (اینجا که میگم بهترین قیمت ها رو داره):

 (سرور حتما فنلاند باشه و سیستم عامل هم بگذارید روی اوبونتو و حداقل 2 گیگ رم و 2 گیگاهرتز سی پی یوش باشه)

[بلو سرور | blueserver.ir](https://blueserver.ir/)


حالا که سرور رو خریدید میتونید کارو شروع کنید تا وقتی که هاست و دامینتون اوکی بشه.

بریم برا مرحله بعدی!

---

### قدم 2 | راه اندازی V2ray روی سرور

حالا پا به پای من کد بزنید و بیاید جلو!

ترمینالتون رو وا کنید (cmd یا powershell) و کد زیر رو بنویسید:
```bash
ssh root@127.0.0.1
```
به جای 127.0.0.1 آدرس آیپی سرورتون رو که در پنل کاربریتون هست رو قرار بدید، با این کامند درخواست کنسول ssh رو روی پورت 22 به سرور ارسال میکنیم، اگر از بلو سرور دریافت کنید سرورتون رو پورت 22 بازه ولی اگر از جای دیگه دریافت کردید و پورت 22 فیلتر بود به پشتیبانی سایت تیکت بزنید.

حالا ازتون Password میخواد که اون هم در ناحیه کاربری پنلتون موجوده، ترجیحا در پنل قبل از اقدام پسوردتون رو ریست کنید چون ممکنه نتونید وصل بشید.

خب اگر موفق شدید به سرور کانکت بشید حالا میتونید با دسترسی root کامند هایی که میگیم رو بزنید.

نصب V2ray خیلی آسونه و به راحتی با چند خط کدی که میگم بزنید میتونید سرویس رو راه اندازی کنید.

خب بریم برای نصب V2ray

اول از همه باید سرورتون رو به روز کنید که با کامند های زیر میتونید اینکارو انجام بدید اول آپدیت:

```bash
sudo apt-get update
```
بعدشم آپگرید:
```bash
sudo apt-get upgrade
```

خب حالا سرورمون آماده نصب V2ray عه، بیاید با کامند های زیر فضا رو معطر به V2ray کنیم!
```bash
bash <(curl -Ls https://raw.githubusercontent.com/tshipenchko/x-ui-en/master/install.sh)
```

```bash
systemctl daemon-reload
```

```bash
systemctl enable x-ui
```

```bash
systemctl restart x-ui
```

این چهار خط کدی که زدیم بهینه ترین روش برای نصب V2ray عه، ولی حواستون باشه که همه تنظیمات رو روی حالت دیفالت قرار میده، برای مثال:

> Port: `54321`

> Admin Username: `admin`

> Admin Password: `admin`

اوکی خب پس حواستون به اینا باشه، اگه خواستید وارد پنل تحت کامند V2ray بشید کافیه توی کنسول بنویسید `x-ui` تا واستون کامند های قابل اجرا رو نشون بده.

توجه کنید: V2ray یک سرویس چینیه و پنلش هم چینیه میتونید نسخه انگلیسیشو نصب کنید ولی آپ تو دیت نیست همیشه پس خیلی پیشنهاد نمیکنم، همینو که گفتم بزنید رواله.

خب خب خب

الان میتونید با جستجوی آیپی سرورتون روی پورت 54321 وارد پنلتون بشید، خب برای اینکه ببینید موفق بودید یا نه آدرس رو به رو رو توی مرورگرتون سرچ کنید: `127.0.0.1:54321` فقط به جای 127.0.0.1 آیپی سرور خودتون رو بزنید تا صفحه ورود بیاد، حالا با همون یوزر نیم پسی که بالاتر نوشتم وارد پنل بشید!

خب تبریک میگم شما موفق به راه اندازی V2ray شدید!!! اما چه فایده وقتی کار نمیده؟

حالا بیاید دنبالم...

---

### قدم 3 | ثبت رکورد دامنه در Cpanel

خب اینجا باید هاست و دامینتون اوکی شده باشه! اگه ردیفه و کار میده ادامه رو بخونید، اگرنه میتونید بدون tls کانفیگ بسازید که فکر نکنم کار بده، پس حتما راهی که میگم رو برید!

طبق مراحل تصویری پیش بیایید:

1. وارد Cpanel بشید و روی گزینه Zone Editor بزنید:

<img src="https://github.com/Eilllia/Saturn/blob/main/cpanel-step1.png" width="400"/>

2. رو به روی نام دامینتون روی A Record بزنید:

<img src="https://github.com/Eilllia/Saturn/blob/main/cpanel-step2.png" width="400"/>

3. حالا در قسمت `Name` یک ساب دامین از دامین خودتون بنویسید مثلا `vps.xyz.com` ، توجه کنید حتما جای xyz.com نام دامنه خودتون رو بزارید و به جای vps نام ساب دامین دلخواهتون، این آدرس پنل و کانفیگ هاتون میشه  و در قسمت `Address` آدرس آیپی سرورتون رو وارد کنید و اد رکرود رو بزنید تا یک رکورد برای ساب دامین شما ایجاد بشه و شما رو مستقیم وصل کنه به سرور، این کار برای تنظیم tls ضروریه، تبی که باز میشه رو میتونید توی عکس ببینید:

<img src="https://github.com/Eilllia/Saturn/blob/main/cpanel-step3.png" width="400"/>

و تمام، الان باید آدرس ساب دامینتون رو که سرچ میکنید به همراه پورت پنلتون وا بشه برای مثال `vps.xyz.com:54321`  (جای vps.xyz.com آدرس ساب دامین خودتون رو بزارید) 



---

### قدم 3 | دریافت و نصب SSL Certificate

آقا سرتونو درد نیارم، قدم به قدم هر چی من میزنم شما هم بزنید، اوکی؟ بزن بریم:

```bash
apt update && apt upgrade -y
```

```bash
apt install curl socat -y
```

```bash
curl https://get.acme.sh | sh
```

```bash
~/.acme.sh/acme.sh --set-default-ca --server letsencrypt
```

اینجا به جای `xyz@abc.com` ایمیل خودتون رو وارد کنید:

```bash
~/.acme.sh/acme.sh --register-account -m xyz@abc.com
```

اینجا هم به جای `host.mydomain.com`  آدرس ساب دامین رکورد داده شدمون رو بنویسید:

```bash
~/.acme.sh/acme.sh --issue -d host.mydomain.com --standalone
```

اینا هم برای اینکه داشته باشید خوبه نیازی به نوشتن اینا نیست اینا اطلاعات سرتیفیکیت شماست (به جای `host.mydomain.com`  آدرس ساب دامین رکورد داده شده رو بزارید، البته نیازتون نمیشه صرفا جهت دونستن گذاشتم):

> Your cert is in: /root/.acme.sh/host.mydomain.com/host.mydomain.com.cer

> Your cert key is in: /root/.acme.sh/host.mydomain.com/host.mydomain.com.key

> The intermediate CA cert is in: /root/.acme.sh/host.mydomain.com/ca.cer

> And the full chain certs is there: /root/.acme.sh/host.mydomain.com/fullchain.cer

و در آخر این کد رو بزنید، به جای `host.mydomain.com` همون ساب دامین خودمون رو بزارید:

```bash
~/.acme.sh/acme.sh --installcert -d host.mydomain.com --key-file /root/private.key --fullchain-file /root/cert.crt
```

هوووف تموم شد! این کد سوسکی هم بزنید که V2ray یه ریست بشه بفهمه چی به چیه:

```bash
x-ui restart
```

---

### قدم 4 | تنظیم پنل V2ray

ول ول ول! حالا باید بریم تو پنل V2ray، چطوری؟ ایندفعه با دامینتون وارد میشید! بعله، اینجوری: `vps.xyz.com:54321` و خب میدونید دیگه به جای vps.xyz.com باید ساب دامین خودمون رو بزاریم، یوزر نیم `admin` و پسوورد `admin` رو میزنیم و وارد پنل میشیم

حالا خوب نگاه کنید! قدم به قدم این چیزی که میگم رو انجام بدید:

وارد قسمت تنظیمات پنل بشید، از روی آیکونش مشخصه ولی عکسش هم اینجا گذاشتم براتون:

<img src="https://github.com/Eilllia/Saturn/blob/main/v2ray-Step1.png" width="250"/>

خب حالا توی فیلد های مشخص شده دوتا مقدار زیر رو به ترتیب در فیلد های سومی و چهارمی وارد کنید:

```
/root/cert.crt
```
```
/root/private.key
```

<img src="https://github.com/Eilllia/Saturn/blob/main/v2ray-Step2.png" width="550"/>

---

### قدم 5 | ساخت کانفیگ Vless و Vmess

همونطوری که گفتم فقط Vlass و Vmess جوابگوعه، اونم فقط با tls خب بریم برا ساختن کانفیگ:

روی دکمه + آبی بزنید توی پنل، تا صفحه زیر واستون وا بشه، دقیقا مواردی که با کادر بنفش مشخص شده رو عین من وارد کنید

(گزینه remark رو اسم دلخواهتون برای کانفیگ بگذارید)

(برای vless هم کافیه بخش انتخاب vmess رو vless بزارید)

(پورت برای هر کانفیگ مجزا و به صورت رندوم تولید میشه، البته قابل تغییر دستیه)

(در بخش tls فیلد های مشخص شده رو همون دو تا آدرس بالا وارد کنید)

<img src="https://github.com/Eilllia/Saturn/blob/main/v2ray-Step3.png" width="550"/>

توجه کنید! برای اندروید و آی او اس vmess پیشنهاد میشه و برای ویندوز و غیره vless پیشنهاد میشه!

حالا روی اون دکمه آبی چینی پینی بزنید تا کانفیگ ساخته بشه

تبریییییک میگم! تموم شد! حالا میتونید استفاده کنید، کافیه روی نوار اسم کانفیگ روی گزینه آبی آخر بزنید تا صفحه بارکد واستون وا بشه، میتونید با زدن روی اون دکمه آبیه کانفیگ رو برای ارسال کپی کنید.

<img src="https://github.com/Eilllia/Saturn/blob/main/v2ray-Step4.png" width="550"/>

اگه هم متوجه نمیشید چی به چیه کلیک راست کنید رو صفحه و ترنسلیت رو بزنید تا صفحه پنل واستون ترجمه بشه

و تمام حالا کافیه کلاینت مخصوص دیوایس خودتون رو دانلود کنید و کانفیگ رو توش قرار بدید، نحوه استفاده رو تو کانال تلگرامم گذاشتم میتونید [از اینجا ببینید و عضو کانال بشید](https://t.me/Saturn_VPN/11)

---

> نوشته شده با عشق توسط ایلیا ویستور | Written with love by Eilia Vistor
