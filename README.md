## Delete all Deployments

<br/> 

بعضی وقتا کلادفلر بهت اجازه نمیده یه pages که قبلا ساختی رو حذف کنی، میگه بخاطر اینکه تعداد دفعات خیلی زیادی دپلوی داشته، این وقتی پیش میاد که یه pages می‌سازیم از طریق اتصال کلادفلر به یه رپوی گیت‌هاب، بعد تازه شروع می‌کنیم به ادیت کردن کد توی گیت، هربار ادیت می‌کنیم و تهش کامیت می‌زنیم خب اینم هربار دپلوی میشه دیگه اتومات، وقتی تعداد این به ۱۰۰ دپلوی برسه دیگه نمی‌تونیم حذفش کنیم. <br/>  

<img width="1080" height="1939" alt="delete-project" src="https://github.com/user-attachments/assets/b1f5c3c6-7a47-43a8-99a1-28f66a5532fb" /> <br/>


### چندتا راه حل داریم:

**۱. حذف دستی**  
چک کن تعداد دپلوی‌هارو اگه نزدیک ۱۰۰ تا باشه (مثلا ۱۲۰ تا) اونوقت ۲۰ تا آخریو از همون داشبورد کلادفلر دستی delete deployment بزن بعد برو سراغ حذف pages.  <br/>   

<img width="1080" height="2340" alt="deployments" src="https://github.com/user-attachments/assets/168631bc-dc92-4479-8fdf-3808d0f9012f" /> <br/>  

**۲. حذف مخزن گیت‌هاب**  
اگه رپو پابلیک نشده و خیلی‌ها از روش فورک نزدن و می‌تونی حذفش کنی راحت‌ترین کار همینه، حذف کن از روی گیت‌هاب بعد راحت از کلادفلر حذف میشه،  بعد میتونی از اول بسازی دوباره با همون اسم و وصلش کنی به اکانت کلادفلر خودت. <br/> 

**۳. لغو اتصال کلادفلر به گیت‌هاب**   
از داخل ستینگ گیت‌هاب دسترسی کلادفلر رو لغو کنی، وقتی جدا بشه و دسترسی نداشته باشه راحت حذف میشه pages. فقط حواست باشه اینجوری پروژه‌های دیگه روی اون اکانت گیت‌هاب هم دسترسیشون قطع میشه و فرضا وقتی یکیشو ادیت می‌کنی دیگه اتومات اون پروژه pages روی کلادفلر دپلوی نمیشه باید دستی وصلش کنی بعدا. <br/> 

**۴. حذف اتومات دپلوی‌ها با اسکریپت**  
اگه تعداد دپلوی ها خیلی بیشتر از صد، دویست تا هستش مث ماله من، و روش‌های بالارو نمی‌تونی پیش بری چون رپو رو خیلیا فورک زدن طبق دستورالعمل بالا پیش برو و راحت همه دپلوی‌عارو نیست و نابود کن. <br/> 

<img width="1080" height="1877" alt="Termux" src="https://github.com/user-attachments/assets/eeab7b7d-9753-4491-9249-5acd7c7f7f28" /> 

<br/><br/>

## راهنمای استفاده

### نصب ابزارها
برای شروع باید ابزار `git` واسه کلون کردن پروژه و `Node.js` واسه حذف دپلوی‌ها نصب شده باشن. با دستور زیر اینکارو انجام بدید، فرضا توی termux اندروید:

```shell
pkg install git nodejs
```

> **نکته**: اگه این دوتا ابزار از قبل روی سیستم شما نصب هستن این مرحله رو نادیده بگیرید.

<br/>

### دریافت پروژه
مخزن `delete-all-deployments` رو با دستور زیر کلون کرده و به دایرکتوری اون برید:

```POV-Ray SDL
git clone https://github.com/Diana-Cl/delete-all-deployments.git && cd delete-all-deployments
```

<br/> 

### نصب وابستگی‌ها
برای نصب وابستگی‌های پروژه، دستور زیر رو اجرا کنید:

```POV-Ray SDL
npm install
```

<br/>

### انتخاب نوع حذف
دستورات زیر را بررسی کنید تا تصمیم بگیرید کدام نوع حذف دیپلوی‌ها را می‌خواهید انجام دهید:

#### حذف تمام دپلوی‌ها
به جز دپلوی فعال (Production) بقیه حذف میشن.  
> بدون احتساب [دپلوی‌ها مستعار][1]

```POV-Ray SDL
CF_API_TOKEN=<YOUR_CF_API_TOKEN> CF_ACCOUNT_ID=<ACCOUNT_ID> CF_PAGES_PROJECT_NAME=<PROJECT_NAME> npm start
```

<br/> 

#### حذف تمام دپلوی‌ها
به جز دپلوی فعال (Production) بقیه حذف میشن.  
> شامل [دپلوی‌های مستعار][1]،  
>
> برای مثال: `staging.example.pages.dev`
> 

```POV-Ray SDL
CF_API_TOKEN=<YOUR_CF_API_TOKEN> CF_ACCOUNT_ID=<ACCOUNT_ID> CF_PAGES_PROJECT_NAME=<PROJECT_NAME> CF_DELETE_ALIASED_DEPLOYMENTS=true npm start
```

### راهنمایی بیشتر برای آماتورها
فرض کنیم می‌خوای همه دپلوی‌ها حذف بشن که بتونی pages رو کامل پاک کنی، باید یه api token و یه account id از کلادفلر کپی کنی و توی دستور جای‌گذاری کنی، حالت نهایی دستور این‌شکلی میشه:  

```ruby
CF_API_TOKEN=Xss0-fxPOMBDISxHtHY4LOX23l-aEAFDOIF2opqrst CF_ACCOUNT_ID=cf764dd49f39fc7e994f1b0f87685cb2 CF_PAGES_PROJECT_NAME=diana CF_DELETE_ALIASED_DEPLOYMENTS=true npm start
```

اینو گفتم چون بارها دیدم که خیلیا دلشون نمیاد اینارو `<>` حذف کنن و آیدی یا توکن رو میذارن داخل همینا.

اگه جایی به مشکل خوردی سوالت رو تو [این گروه][00] بپرس


<br/> 

### پیداکردن توکن API کلودفلر
برای دریافت توکن API کلودفلر، به [داشبورد کلادفلر][2] رفته و روی آیکون کاربر در گوشه بالا سمت راست کلیک کنید، سپس به بخش **My Profile > API Tokens** برید، و یا از قسمت جستجو عبارت **api** رو جستجو کرده و **api tokens** رو انتخاب کنید. یک توکن با دسترسی workers ایجاد کنید.

<br/> 

### پیداکردن شناسه حساب (Account ID)
برای پیدا کردن شناسه حساب اکانت کلادفلر خودتون به [مستندات یافتن شناسه زون و حساب][3] سر بزنید. تو صفحه‌ی **workers and pages** که لیست وورکر‌ها و پیج‌های شما قرار داره یکم که برید پایین‌تر **Account ID** رو خواهید دید. 

<hr/><br/> 

## English

**Delete a Cloudflare pages project with a high number of deployments**  

You may not be able to delete your Pages project if it has a high number (over 100) of deployments. <br/>  

As a workaround, review the following steps to delete all deployments in your Pages project. After you delete your deployments, you will be able to delete your Pages project.

<br/> 

### installing tools
To get started, you need to have `git` tools to clone project and `Node.js` to remove deployments. Do this with the following command, assuming you are using Android's Termux:

```POV-Ray SDL
pkg install git nodejs
```

> **Note**: If `Node.js` and `git` are already installed on your system, skip this step.

### clone  repository
Clone the `delete-all-deployments` repository with the following command and move to the same directory:

```POV-Ray SDL
git clone https://github.com/Diana-Cl/delete-all-deployments.git && cd delete-all-deployments
```

<br/>

### Install dependencies

run `npm install` to install dependencies:

```POV-Ray SDL
npm install
```

<br/> 

### Select the type of deployment deletion

Review the following commands to decide which deletion you would like to proceed with:

#### To delete all deployments
Except for the live production deployment.  
> Excluding [aliased deploymens][1]:

```POV-Ray SDL
CF_API_TOKEN=<YOUR_CF_API_TOKEN> CF_ACCOUNT_ID=<ACCOUNT_ID> CF_PAGES_PROJECT_NAME=<PROJECT_NAME> npm start
```

<br/> 

#### To delete all deployments
Except for the live production deployment.  
> including [aliased deployments][1]
>
> For example, (staging.example.pages.dev)

```POV-Ray SDL
CF_API_TOKEN=<YOUR_CF_API_TOKEN> CF_ACCOUNT_ID=<ACCOUNT_ID> CF_PAGES_PROJECT_NAME=<PROJECT_NAME> CF_DELETE_ALIASED_DEPLOYMENTS=true npm start
```

<br/> 

### To find your Cloudflare API token
[log in to the Cloudflare dashboard][2], select the user icon on the upper righthand side of your screen > go to My Profile > API Tokens.

### To find your Account ID
refer to [Find your zone and account ID][3].

<hr/><br/> 

[1]: https://developers.cloudflare.com/pages/configuration/preview-deployments/#preview-aliases
[2]: https://dash.cloudflare.com/
[3]: https://developers.cloudflare.com/fundamentals/account/find-account-and-zone-ids/
[00]: https://t.me/NiREvil_GP
