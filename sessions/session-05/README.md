
# جلسه ۵ — دریافت پروژه از GitHub

**Git Clone & Download ZIP | Session 05**

در جلسه چهارم یاد گرفتیم چطور پروژه محلی خودمون رو به GitHub متصل کنیم و تغییرات ثبت‌شده رو به مخزن راه دور ارسال کنیم.

در این جلسه یاد می‌گیریم چطور یک پروژه موجود در GitHub رو همراه با تاریخچه تغییراتش روی کامپیوتر خودمون دریافت کنیم.

---

## اهداف جلسه

در پایان این جلسه می‌تونیم:

- مفهوم Clone رو توضیح بدیم.
- یک Repository موجود رو دریافت کنیم.
- نام پوشه مقصد رو مشخص کنیم.
- تاریخچه مخزن دریافت‌شده رو بررسی کنیم.
- اتصال Remote رو مشاهده کنیم.
- تفاوت Clone و Download ZIP رو توضیح بدیم.

---

# ۱. مرور جلسه قبل

در جلسه چهارم مسیر زیر رو یاد گرفتیم:

```text
Working Directory
        |
        | git add
        v
   Staging Area
        |
        | git commit
        v
 Local Repository
        |
        | git push
        v
Remote Repository
     (GitHub)
```

اما فرض کنید:

- لپ‌تاپ خودمون رو عوض کردیم.
- می‌خوایم پروژه رو روی کامپیوتر دیگری ادامه بدیم.
- می‌خوایم پروژه یکی از دوستانمون رو دریافت کنیم.
- می‌خوایم روی یک پروژه موجود کار کنیم.

چطور می‌تونیم پروژه رو همراه با تاریخچه تغییراتش دریافت کنیم؟

برای این کار از دستور زیر استفاده می‌کنیم:

```powershell
git clone
```

---

# ۲. مفهوم Clone

```text
Clone
```

این عملیات یک نسخه محلی از یک مخزن موجود ایجاد می‌کنه.

در حالت معمول، علاوه بر فایل‌های پروژه، تاریخچه تغییرات و اطلاعات مربوط به مخزن هم دریافت می‌شن.

```text
Remote Repository
     (GitHub)
        |
        | git clone
        v
 Local Repository
        +
Working Directory
```

با این روش می‌تونیم:

- فایل‌های پروژه رو دریافت کنیم.
- تاریخچه تغییرات رو مشاهده کنیم.
- Commitهای قبلی رو بررسی کنیم.
- توسعه پروژه رو ادامه بدیم.

## تفاوت Push و Clone

ارسال تغییرات ثبت‌شده:

```text
Local Repository
        |
        | git push
        v
Remote Repository
```

دریافت یک نسخه محلی جدید:

```text
Remote Repository
        |
        | git clone
        v
New Local Repository
```

---

# ۳. دریافت آدرس مخزن

ابتدا وارد سایت GitHub شوید:

https://github.com

مخزنی رو که در جلسه چهارم ایجاد کردید باز کنید.

نام نمونه:

```text
my-first-remote
```

روی گزینه زیر کلیک کنید:

```text
Code
```

روش اتصال زیر رو انتخاب کنید:

```text
HTTPS
```

سپس آدرس مخزن رو کپی کنید.

نمونه:

```text
https://github.com/USERNAME/my-first-remote.git
```

به‌جای عبارت زیر، نام کاربری واقعی شما قرار می‌گیره:

```text
USERNAME
```

---

# ۴. آماده‌سازی مسیر دریافت پروژه

ابتدا از پوشه پروژه قبلی خارج می‌شیم.

برای مثال، به Desktop می‌ریم.

```powershell
cd $HOME\Desktop
```

برای بررسی مسیر فعلی:

```powershell
Get-Location
```

برای مشاهده فایل‌ها و پوشه‌ها:

```powershell
Get-ChildItem -Name
```

اگر مسیر Desktop در سیستم شما متفاوت بود، می‌تونید از طریق File Explorer وارد پوشه موردنظر بشید و در نوار آدرس عبارت زیر رو بنویسید:

```text
powershell
```

---

# ۵. اجرای Clone

دستور زیر رو اجرا کنید:

```powershell
git clone https://github.com/USERNAME/my-first-remote.git
```

دقت کنید که باید آدرس واقعی مخزن خودتون رو جایگزین آدرس نمونه کنید.

## توضیح اجزای دستور

### بخش اول

```powershell
git clone
```

برای ایجاد یک نسخه محلی از مخزن موجود استفاده می‌شه.

### بخش دوم

```text
https://github.com/USERNAME/my-first-remote.git
```

آدرس مخزنی است که می‌خوایم دریافت کنیم.

## خروجی احتمالی

```text
Cloning into 'my-first-remote'...
remote: Enumerating objects: ...
Receiving objects: 100% ...
```

بعد از اجرای موفق دستور، یک پوشه جدید ایجاد می‌شه.

ساختار نمونه:

```text
Desktop/
└── my-first-remote/
    ├── .git/
    └── about-me.txt
```

پروژه قبلی همچنان وجود داره و این پوشه یک نسخه محلی جدید از مخزن راه دور است.

برای ورود به پوشه جدید:

```powershell
cd my-first-remote
```

---

# ۶. تعیین نام پوشه مقصد

به‌صورت پیش‌فرض، نام پوشه ایجادشده معمولاً با نام مخزن یکسان است.

اما می‌تونیم نام پوشه مقصد رو خودمون مشخص کنیم.

فرم کلی دستور:

```powershell
git clone URL folder-name
```

مثال:

```powershell
git clone https://github.com/USERNAME/my-first-remote.git cloned-git-project
```

نام پوشه جدید:

```text
cloned-git-project
```

برای ورود به پوشه جدید:

```powershell
cd cloned-git-project
```

**نکته:**

این مثال رو از خارج پوشه مخزن قبلی اجرا کنید.

اگر پوشه مقصد از قبل وجود داشته باشه و خالی نباشه، می‌تونیم نام دیگری برای پوشه مقصد انتخاب کنیم.

---

# ۷. بررسی مخزن دریافت‌شده

بعد از ورود به پوشه جدید، دستورات زیر رو اجرا می‌کنیم.

## مشاهده فایل‌های پروژه

```powershell
Get-ChildItem -Name
```

## مشاهده محتوای فایل

```powershell
Get-Content .\about-me.txt
```

## بررسی وضعیت مخزن

```powershell
git status
```

خروجی احتمالی:

```text
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

## مشاهده تاریخچه تغییرات

```powershell
git log --oneline
```

خروجی نمونه:

```text
def5678 Add branching skill
abc1234 Add learning goal
123abcd Add my profile
```

شناسه‌ها و پیام‌های ثبت تغییرات در پروژه هر دانشجو ممکنه متفاوت باشن.

نکته مهم اینه که تاریخچه قبلی پروژه هم دریافت شده.

## مشاهده اتصال راه دور

```powershell
git remote -v
```

خروجی نمونه:

```text
origin  https://github.com/USERNAME/my-first-remote.git (fetch)
origin  https://github.com/USERNAME/my-first-remote.git (push)
```

هنگام دریافت مخزن، اتصال راه دور به‌صورت پیش‌فرض با نام زیر ایجاد می‌شه:

```text
origin
```

بنابراین نیازی نیست دوباره دستور زیر رو اجرا کنیم:

```powershell
git remote add origin URL
```

---

# ۸. آیا بعد از Clone به git init نیاز داریم؟

در جلسه اول برای ایجاد یک مخزن جدید از دستور زیر استفاده کردیم:

```powershell
git init
```

اما بعد از اجرای دستور دریافت مخزن، نیازی به اجرای مجدد این دستور نداریم.

چرا؟

چون مخزن دریافت‌شده از قبل شامل اطلاعات مربوط به Git است.

برای مشاهده فایل‌ها و پوشه‌های مخفی:

```powershell
Get-ChildItem -Force -Name
```

خروجی نمونه:

```text
.git
about-me.txt
```

پوشه زیر اطلاعات داخلی مخزن رو نگهداری می‌کنه:

```text
.git
```

این اطلاعات شامل مواردی مانند تاریخچه تغییرات، شاخه‌ها و تنظیمات مخزن است.

**نکته مهم:**

نباید بدون آگاهی فایل‌های داخلی این پوشه رو تغییر بدیم یا حذف کنیم.

---

# ۹. دانلود پروژه به‌صورت ZIP

روش دیگری هم برای دریافت فایل‌های یک پروژه وجود داره.

```text
Download ZIP
```

## مراحل دانلود

۱. وارد صفحه مخزن در GitHub شوید.

۲. روی گزینه زیر کلیک کنید:

```text
Code
```

۳. گزینه زیر رو انتخاب کنید:

```text
Download ZIP
```

۴. فایل فشرده رو دانلود کنید.

۵. فایل فشرده رو استخراج کنید.

در این روش، فایل‌های نسخه انتخاب‌شده پروژه دریافت می‌شن، اما اطلاعات داخلی مخزن و تاریخچه تغییرات همراه اون‌ها دریافت نمی‌شن.

ساختار نمونه:

```text
my-first-remote-main/
└── about-me.txt
```

---

# ۱۰. تفاوت Clone و Download ZIP

## Clone

```powershell
git clone URL
```

ساختار نمونه:

```text
cloned-git-project/
├── .git/
└── about-me.txt
```

ویژگی‌ها:

- دریافت فایل‌های پروژه
- دریافت تاریخچه تغییرات
- وجود اطلاعات داخلی مخزن
- تنظیم خودکار اتصال راه دور
- امکان ادامه توسعه با حفظ تاریخچه قبلی

## Download ZIP

```text
Download ZIP
```

ساختار نمونه:

```text
my-first-remote-main/
└── about-me.txt
```

ویژگی‌ها:

- دریافت فایل‌های پروژه
- دریافت نشدن تاریخچه تغییرات
- نبود اطلاعات داخلی مخزن
- تنظیم نشدن اتصال راه دور

## جدول مقایسه

| ویژگی | Clone | Download ZIP |
|---|---|---|
| دریافت فایل‌های پروژه | بله | بله |
| دریافت تاریخچه تغییرات | بله | خیر |
| وجود پوشه `.git` | بله | خیر |
| تنظیم خودکار Remote | بله | خیر |
| ادامه توسعه با تاریخچه قبلی | بله | خیر |
| نیاز به نصب Git برای دریافت | بله | خیر |

## نمودار مقایسه

```text
          GitHub Repository
                  |
         +--------+--------+
         |                 |
     git clone        Download ZIP
         |                 |
         v                 v
  +--------------+   +--------------+
  | Project Files|   | Project Files|
  | Git History  |   |              |
  | .git         |   | No History   |
  | Remote       |   | No Remote    |
  +--------------+   +--------------+
```

---

# ۱۱. آزمایش عملی تفاوت Clone و ZIP

برای درک بهتر تفاوت این دو روش، آزمایش زیر رو انجام می‌دیم.

## آزمایش اول — پوشه Clone شده

وارد پوشه دریافت‌شده با Git شوید و دستورات زیر رو اجرا کنید:

```powershell
git status
git log --oneline
git remote -v
Get-ChildItem -Force -Name
```

در این پوشه، اطلاعات و تاریخچه مخزن در دسترس هستند.

## آزمایش دوم — پوشه استخراج‌شده از ZIP

وارد پوشه استخراج‌شده شوید.

مطمئن شوید که این پوشه داخل مخزن Git دیگری قرار نگرفته باشد.

دستور زیر رو اجرا کنید:

```powershell
git status
```

خروجی مورد انتظار:

```text
fatal: not a git repository
```

### چرا این خطا نمایش داده می‌شه؟

چون پوشه استخراج‌شده از فایل ZIP به‌صورت معمول یک مخزن Git نیست.

برای مشاهده پوشه‌های مخفی:

```powershell
Get-ChildItem -Force -Name
```

پوشه زیر در فایل ZIP معمولی GitHub وجود نداره:

```text
.git
```

## نتیجه آزمایش

با اینکه فایل‌های پروژه در هر دو پوشه وجود دارن، فقط نسخه دریافت‌شده با Clone شامل تاریخچه و اطلاعات داخلی مخزن است.

---

# ۱۲. چه زمانی از هر روش استفاده کنیم؟

## Clone

زمانی مناسب است که:

- بخوایم توسعه پروژه رو ادامه بدیم.
- بخوایم تاریخچه تغییرات رو بررسی کنیم.
- بخوایم با افراد دیگر روی پروژه همکاری کنیم.
- بخوایم تغییرات آینده رو با حفظ تاریخچه قبلی ثبت کنیم.

## Download ZIP

زمانی مناسب است که:

- فقط به فایل‌های پروژه نیاز داشته باشیم.
- بخوایم کدهای پروژه رو مطالعه کنیم.
- نیازی به تاریخچه تغییرات نداشته باشیم.

**نکته:**

هیچ‌کدوم از این دو روش ذاتاً اشتباه نیستند.

انتخاب روش مناسب به هدف ما بستگی داره.

---

# ۱۳. پرسش‌های مفهومی

## سؤال اول

آیا Clone فقط فایل‌های پروژه رو دریافت می‌کنه؟

<details>
<summary>نمایش پاسخ</summary>

خیر. در حالت معمول، تاریخچه تغییرات و اطلاعات مخزن هم دریافت می‌شن.

</details>

## سؤال دوم

آیا بعد از Clone باید دستور زیر رو اجرا کنیم؟

```powershell
git init
```

<details>
<summary>نمایش پاسخ</summary>

خیر. Clone خودش یک مخزن محلی ایجاد می‌کنه.

</details>

## سؤال سوم

چرا بعد از دریافت مخزن، اتصال راه دور از قبل وجود داره؟

<details>
<summary>نمایش پاسخ</summary>

چون Git هنگام Clone کردن به‌صورت پیش‌فرض اتصال راه دور رو با نام origin ایجاد می‌کنه.

</details>

## سؤال چهارم

آیا فایل ZIP شامل تاریخچه تغییرات مخزن است؟

<details>
<summary>نمایش پاسخ</summary>

خیر. فایل ZIP معمولی GitHub فقط شامل فایل‌های نسخه انتخاب‌شده پروژه است.

</details>

## سؤال پنجم

اگر یک مخزن رو دریافت کنیم و فرد دیگری بعداً تغییر جدیدی در GitHub ایجاد کنه، آیا فایل‌های کامپیوتر ما به‌صورت خودکار تغییر می‌کنن؟

<details>
<summary>نمایش پاسخ</summary>

خیر. برای دریافت تغییرات جدید باید از دستورات دیگری استفاده کنیم که در جلسه آینده یاد می‌گیریم.

</details>

---

# ۱۴. تمرین عملی

مخزنی رو که در جلسه چهارم ایجاد کردید، در یک پوشه جدید دریافت کنید.

## مرحله اول

آدرس HTTPS مخزن رو کپی کنید.

## مرحله دوم

به Desktop بروید.

```powershell
cd $HOME\Desktop
```

## مرحله سوم

مخزن رو با نام مقصد دلخواه دریافت کنید.

```powershell
git clone https://github.com/USERNAME/my-first-remote.git git-clone-practice
```

## مرحله چهارم

وارد پوشه جدید شوید.

```powershell
cd git-clone-practice
```

## مرحله پنجم

وضعیت مخزن رو بررسی کنید.

```powershell
git status
```

## مرحله ششم

تاریخچه تغییرات رو مشاهده کنید.

```powershell
git log --oneline
```

## مرحله هفتم

اتصال راه دور رو بررسی کنید.

```powershell
git remote -v
```

## مرحله هشتم

فایل‌ها و پوشه‌های مخفی رو مشاهده کنید.

```powershell
Get-ChildItem -Force -Name
```

## نتیجه مورد انتظار

- پروژه در یک پوشه جدید دریافت شده باشد.
- فایل‌های پروژه قابل مشاهده باشند.
- تاریخچه تغییرات وجود داشته باشد.
- اتصال راه دور تنظیم شده باشد.
- اطلاعات داخلی مخزن وجود داشته باشند.

---

# ۱۵. Challenge

بدون نگاه کردن به جزوه، یک مخزن عمومی دلخواه در GitHub انتخاب کنید.

مراحل زیر رو انجام بدید:

۱. آدرس HTTPS مخزن رو پیدا کنید.

۲. مخزن رو در یک پوشه جدید دریافت کنید.

۳. وارد پوشه جدید شوید.

۴. فایل‌های پروژه رو مشاهده کنید.

۵. سه Commit آخر رو نمایش بدید.

۶. اتصال راه دور رو بررسی کنید.

۷. همون مخزن رو به‌صورت ZIP دانلود کنید.

۸. تفاوت دو پوشه رو بررسی کنید.

<details>
<summary>نمایش راهنمای پاسخ</summary>

```powershell
git clone URL challenge-project
cd challenge-project
Get-ChildItem -Name
git status
git log --oneline -3
git remote -v
Get-ChildItem -Force -Name
```

به‌جای URL، آدرس واقعی مخزن انتخاب‌شده رو قرار بدید.

</details>

---

# ۱۶. خطاهای رایج

## وجود پوشه مقصد

```text
fatal: destination path already exists and is not an empty directory
```

علت:

پوشه مقصد از قبل وجود داره و خالی نیست.

راه‌حل:

یک نام جدید برای پوشه مقصد انتخاب کنید.

```powershell
git clone URL another-project
```

---

## پیدا نشدن مخزن

```text
Repository not found
```

موارد قابل بررسی:

- آدرس مخزن صحیح باشد.
- مخزن موردنظر وجود داشته باشد.
- مجوز دسترسی به مخزن وجود داشته باشد.

---

## نبودن در مخزن Git

```text
fatal: not a git repository
```

ابتدا مسیر فعلی رو بررسی کنید.

```powershell
Get-Location
```

سپس وارد پوشه صحیح شوید.

اگر پروژه رو به‌صورت ZIP دریافت کرده باشید و داخل مخزن دیگری نباشید، مشاهده این پیام طبیعی است.

---

# ۱۷. خلاصه دستورات جلسه

## دریافت مخزن

```powershell
git clone URL
```

## دریافت مخزن با نام مقصد دلخواه

```powershell
git clone URL folder-name
```

## بررسی مسیر فعلی

```powershell
Get-Location
```

## مشاهده فایل‌ها

```powershell
Get-ChildItem -Name
```

## مشاهده فایل‌ها و پوشه‌های مخفی

```powershell
Get-ChildItem -Force -Name
```

## بررسی وضعیت مخزن

```powershell
git status
```

## مشاهده تاریخچه

```powershell
git log --oneline
```

## مشاهده اتصال راه دور

```powershell
git remote -v
```

---

# ۱۸. جمع‌بندی جلسه

در این جلسه یاد گرفتیم چطور یک مخزن موجود رو از GitHub دریافت کنیم و تفاوت دریافت مخزن با دانلود فایل فشرده رو بررسی کردیم.

مسیر یادگیری ما تا اینجا:

```text
Version Control
       |
       v
      Git
       |
       v
Repository & Commit
       |
       v
History & Diff
       |
       v
Branch & Merge
       |
       v
GitHub & Remote
       |
       v
    git push
       |
       v
    git clone
```

حالا می‌تونیم پروژه خودمون رو در GitHub منتشر کنیم و یک نسخه محلی جدید از اون دریافت کنیم.

---

# جلسه آینده

فرض کنید یک پروژه رو دریافت کردیم.

بعد از مدتی یکی از اعضای تیم تغییر جدیدی در مخزن راه دور ثبت می‌کنه.

چطور می‌تونیم این تغییر رو بدون دریافت دوباره کل پروژه روی سیستم خودمون داشته باشیم؟

در جلسه آینده با دستورات زیر آشنا می‌شیم:

```powershell
git fetch
git pull
```

---

# منابع معتبر

## Pro Git

Getting a Git Repository

https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository

## Git Documentation

git-clone

https://git-scm.com/docs/git-clone

## GitHub Documentation

Cloning a repository

https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository

---

[بازگشت به صفحه اصلی دوره](../../README.md)
