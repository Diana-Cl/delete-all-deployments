## Delete all Deployments

بعضی وقتا کلادفلر بهت اجازه نمیده یه pages که قبلا ساختی رو حذف کنی، میگه بخاطر اینکه تعداد دفعات خیلی زیادی دپلوی داشته، این وقتی پیش میاد که یه pages می‌سازیم از طریق اتصال کلادفلر به یه رپوی گیت‌هاب، بعد تازه شروع می‌کنیم به ادیت کردن کد توی گیت، هربار ادیت می‌کنیم و تهش کامیت می‌زنیم خب اینم هربار دپلوی میشه دیگه اتومات، وقتی تعداد این به ۱۰۰ دپلوی برسه دیگه نمی‌تونیم حذفش کنیم. <br/>  

<img width="1080" height="1939" alt="delete-project" src="https://github.com/user-attachments/assets/b1f5c3c6-7a47-43a8-99a1-28f66a5532fb" /> <br/>


### چندتا راه حل داریم:

۱. چک کن تعداد دپلوی‌هارو اگه نزدیک ۱۰۰ تا باشه (مثلا ۱۲۰ تا) اونوقت ۲۰ تا آخریو از همون داشبورد کلادفلر دستی delete deployment بزن بعد برو سراغ حذف pages.  <br/>   

<img width="1080" height="2340" alt="deployments" src="https://github.com/user-attachments/assets/168631bc-dc92-4479-8fdf-3808d0f9012f" /> <br/>  

۲. اگه رپو پابلیک نشده و خیلی‌ها از روش فورک نزدن و می‌تونی حذفش کنی راحت‌ترین کار همینه، حذف کن از روی گیت‌هاب بعد راحت از کلادفلر حذف میشه،  بعد میتونی از اول بسازی دوباره با همون اسم و وصلش کنی به اکانت کلادفلر خودت.

۳. از داخل ستینگ گیت‌هاب دسترسی کلادفلر رو لغو کنی، وقتی جدا بشه و دسترسی نداشته باشه راحت حذف میشه pages. فقط حواست باشه اینجوری پروژه‌های دیگه روی اون اکانت گیت‌هاب هم دسترسیشون قطع میشه و فرضا وقتی یکیشو ادیت می‌کنی دیگه اتومات اون پروژه pages روی کلادفلر دپلوی نمیشه باید دستی وصلش کنی بعدا.  

۴. اگه تعداد دپلوی ها خیلی بیشتر از صد، دویست تا هستش مث ماله من، و روش‌های بالارو نمی‌تونی پیش بری چون رپو رو خیلیا فورک زدن طبق دستورالعمل بالا پیش برو و راحت همه دپلوی‌عارو نیست و نابود کن.

<img width="1080" height="1877" alt="Termux" src="https://github.com/user-attachments/assets/eeab7b7d-9753-4491-9249-5acd7c7f7f28" />

<hr/><br/>

**Delete a Cloudflare pages project with a high number of deployments**  

You may not be able to delete your Pages project if it has a high number (over 100) of deployments. <br/>  

As a workaround, review the following steps to delete all deployments in your Pages project. After you delete your deployments, you will be able to delete your Pages project.

clone the delete-all-deployments.zip file by going to the following link and
Open your terminal and cd into the delete-all-deployments directory.
In the delete-all-deployments directory

```
git clone https://github.com/Diana-Cl/delete-all-deployments.git && cd delete-all-deployments
```

run `npm install` to install dependencies

```
npm install
```

<br/> 

Review the following commands to decide which deletion you would like to proceed with:

#### To delete all deployments
> Except for the live production deployment (excluding [aliased deploymens][1]):

```js
CF_API_TOKEN=<YOUR_CF_API_TOKEN> CF_ACCOUNT_ID=<ACCOUNT_ID> CF_PAGES_PROJECT_NAME=<PROJECT_NAME> npm start
```

<br/> 

#### To delete all deployments:
> except for the live production deployment (including [aliased deployments][1] for example, staging.example.pages.dev):

```js
CF_API_TOKEN=<YOUR_CF_API_TOKEN> CF_ACCOUNT_ID=<ACCOUNT_ID> CF_PAGES_PROJECT_NAME=<PROJECT_NAME> CF_DELETE_ALIASED_DEPLOYMENTS=true npm start
```

<br/> 

### To find your Cloudflare API token
[log in to the Cloudflare dashboard][2], select the user icon on the upper righthand side of your screen > go to My Profile > API Tokens.

To find your Account ID, refer to [Find your zone and account ID][3].

<br></br> 

#
## How to

### Install dependencies
```js
npm install
```

<br></br> 

### Delete all deployments
> except for the live production deployment  
> > excluding aliased deployments

```js
CF_API_TOKEN=xxx CF_ACCOUNT_ID=xxx CF_PAGES_PROJECT_NAME=xxx npm start
```

<br></br> 

### Delete all deployments
> except for the live production deployment  
> > INCLUDING aliased deployments, eg. my-branch.exampleproj.pages.dev

```js
CF_API_TOKEN=xxx CF_ACCOUNT_ID=xxx CF_PAGES_PROJECT_NAME=xxx CF_DELETE_ALIASED_DEPLOYMENTS=true npm start
```

<hr/><br/> 

[1]: https://developers.cloudflare.com/pages/configuration/preview-deployments/#preview-aliases
[2]: https://dash.cloudflare.com/
[3]: https://developers.cloudflare.com/fundamentals/account/find-account-and-zone-ids/
