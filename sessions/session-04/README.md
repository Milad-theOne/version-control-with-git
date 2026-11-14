
# جلسه ۴ — اتصال پروژه به GitHub و اولین Push

**GitHub & Remote Repository | Session 04**

در سه جلسه گذشته یاد گرفتیم چطور با Git تغییرات پروژه رو مدیریت کنیم، Commit بسازیم، History رو بررسی کنیم و با Branch و Merge کار کنیم.

اما تمام این فعالیت‌ها تا الان روی کامپیوتر خودمون انجام می‌شدن.

در این جلسه می‌خوایم پروژه محلی رو به GitHub متصل کنیم و برای اولین بار Commitهای پروژه رو روی GitHub منتشر کنیم.

---

## اهداف یادگیری

تا پایان این جلسه می‌تونیم:

- تفاوت Git و GitHub رو توضیح بدیم.
- با Local Repository و Remote Repository آشنا بشیم.
- یک Repository جدید در GitHub ایجاد کنیم.
- مفهوم `origin` رو درک کنیم.
- با `git remote` اتصال‌های پروژه رو مدیریت کنیم.
- با `git push` تغییرات ثبت‌شده رو به GitHub ارسال کنیم.
- پروژه منتشرشده رو در حساب GitHub خودمون مشاهده کنیم.

---

# ۱. Git و GitHub چه تفاوتی دارن؟

## Git چیست؟

**Git**

یک ابزار Version Control برای مدیریت تغییرات پروژه است.

با Git می‌تونیم:

- تغییرات فایل‌ها رو ثبت کنیم.
- History پروژه رو مشاهده کنیم.
- به نسخه‌های قبلی برگردیم.
- Branch جدید ایجاد کنیم.
- تغییرات Branchها رو Merge کنیم.

نکته مهم اینه که Git برای انجام فعالیت‌های محلی به اینترنت نیاز نداره.

برای مثال:

```powershell
git status
git add about-me.txt
git commit -m "Update profile"
```

این دستورها به‌صورت محلی اجرا می‌شن.

## GitHub چیست؟

**GitHub**

یک سرویس آنلاین برای میزبانی Repositoryهای Git و همکاری روی پروژه‌هاست.

با GitHub می‌تونیم:

- پروژه‌هامون رو آنلاین نگهداری کنیم.
- پروژه‌ها رو با دیگران به اشتراک بذاریم.
- از سیستم‌های مختلف به Repository دسترسی داشته باشیم.
- در آینده به‌صورت تیمی روی پروژه‌ها کار کنیم.

## تفاوت اصلی

| Git | GitHub |
|---|---|
| ابزار Version Control | سرویس میزبانی Repository |
| روی کامپیوتر اجرا می‌شه | از طریق اینترنت در دسترسه |
| برای Commit محلی اینترنت لازم نداره | برای ارتباط آنلاین به اینترنت نیاز داره |
| تغییرات و History رو مدیریت می‌کنه | امکان انتشار و همکاری روی پروژه رو فراهم می‌کنه |

### ⚡ سؤال سریع

اگر اینترنت قطع بشه، آیا می‌تونیم روی پروژه Commit ایجاد کنیم؟

<details>
<summary>نمایش پاسخ</summary>

بله.

چون `git commit` در Local Repository انجام می‌شه و به اینترنت نیاز نداره.

</details>

---

# ۲. Local Repository و Remote Repository

تا الان Repository پروژه روی کامپیوتر خودمون قرار داشت.

به چنین مخزنی می‌گیم:

**Local Repository**

حالا می‌خوایم یک Repository دیگه در GitHub داشته باشیم.

به مخزنی که از طریق شبکه به اون دسترسی داریم، می‌گیم:

**Remote Repository**

## ارتباط این دو مخزن

```text
+----------------------+
|   Local Repository   |
|                      |
|  Commits             |
|  Branches            |
|  History             |
+----------------------+
            |
            | git push
            v
+----------------------+
|  Remote Repository   |
|                      |
|       GitHub         |
|                      |
|  Commits             |
|  Branches            |
+----------------------+
```

در این جلسه فقط مسیر ارسال تغییرات از Local به Remote رو تمرین می‌کنیم.

## ارتباط با مدل سه‌مرحله‌ای Git

مدلی رو که از جلسه اول یاد گرفتیم به خاطر بیاریم:

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

**نکته مهم:**

این نمودار مسیر کلی آموزش رو نشون می‌ده.

دستور `git push` مستقیماً تغییرات ثبت‌نشده در Working Directory یا Staging Area رو ارسال نمی‌کنه؛ بلکه Commitها و اطلاعات مربوط به Branch رو به Remote منتقل می‌کنه.

پس برای ارسال یک تغییر جدید، ابتدا باید اون تغییر رو Commit کرده باشیم.

### 🧠 سؤال مفهومی

فرض کن فایل پروژه رو ویرایش کردیم، اما هنوز Commit نزدیم.

آیا با اجرای دستور زیر، ویرایش جدید در GitHub منتشر می‌شه؟

```powershell
git push
```

<details>
<summary>نمایش پاسخ</summary>

خیر.

چون تغییر جدید هنوز در یک Commit ثبت نشده.

ابتدا باید تغییر رو Stage و Commit کنیم.

</details>

---

# ۳. آماده‌سازی پروژه جلسات قبل

در Windows وارد پوشه پروژه‌ای شو که در جلسات قبلی ساختیم.

مسیر نمونه:

```text
Desktop/
└── Git-Class/
    └── git-first-project/
        └── about-me.txt
```

داخل پوشه پروژه، روی نوار آدرس File Explorer کلیک کن.

عبارت زیر رو بنویس و Enter بزن:

```text
powershell
```

حالا PowerShell در پوشه پروژه باز می‌شه.

## مرحله اول — بررسی مسیر

```powershell
Get-Location
```

## مرحله دوم — بررسی نصب Git

```powershell
git --version
```

## مرحله سوم — بررسی وضعیت Repository

```powershell
git status
```

اگر تغییر ثبت‌نشده‌ای وجود نداشته باشه، خروجی شبیه اینه:

```text
On branch main
nothing to commit, working tree clean
```

## مرحله چهارم — بررسی Branch فعلی

```powershell
git branch
```

خروجی نمونه:

```text
  feature-profile
* main
```

علامت `*` نشون می‌ده که الان روی Branch اصلی قرار داریم.

در این راهنما فرض می‌کنیم نام Branch اصلی `main` است.

اگر در سیستم تو نام اون `master` است، در دستورهای مربوط به Branch از نام واقعی استفاده کن.

## مرحله پنجم — بررسی History

```powershell
git log --oneline
```

خروجی نمونه:

```text
def5678 Add branching skill
abc1234 Add learning goal
123abcd Add my profile
```

شناسه Commitها در سیستم هر نفر متفاوته.

> ⚠️ قبل از ادامه، اگر تغییر ثبت‌نشده مهمی داری، ابتدا اون رو بررسی کن. هیچ تغییری رو بدون اطمینان حذف نکن.

---

# ۴. ساخت Repository در GitHub

حالا می‌خوایم یک Repository آنلاین برای پروژه ایجاد کنیم.

## مرحله اول — ورود به GitHub

وارد سایت زیر شو:

https://github.com

اگر حساب کاربری نداری، ابتدا حساب بساز.

در غیر این صورت وارد حساب خودت شو.

## مرحله دوم — ساخت Repository

از منوی ایجاد، گزینه زیر رو انتخاب کن:

**New repository**

## مرحله سوم — انتخاب نام

در قسمت نام Repository بنویس:

```text
my-first-remote
```

## مرحله چهارم — انتخاب نوع دسترسی

دو گزینه اصلی داریم:

**Public**

یعنی Repository برای عموم قابل مشاهده است.

**Private**

یعنی دسترسی به Repository محدود است.

برای تمرین می‌تونی یکی از این دو حالت رو انتخاب کنی.

> ⚠️ در Repository عمومی اطلاعات حساس مثل رمز عبور، Token یا کلیدهای خصوصی قرار نده.

## مرحله پنجم — خالی نگه داشتن Repository

برای این تمرین، گزینه‌های زیر رو فعال نکن:

```text
Add a README file
Add .gitignore
Choose a license
```

چرا؟

چون پروژه محلی ما از قبل Commit داره.

اگر Repository آنلاین هم تاریخچه مستقلی داشته باشه، ممکنه اولین Push با مشکل مواجه بشه.

پس برای این تمرین، یک Repository خالی می‌سازیم.

## مرحله ششم — ایجاد Repository

روی گزینه زیر کلیک کن:

**Create repository**

حالا Repository آنلاین ساخته شده.

اما هنوز فایل‌های پروژه محلی ما داخل اون نیستن.

### ⚡ سؤال سریع

آیا ساخت Repository در سایت GitHub باعث می‌شه فایل‌های کامپیوترمون خودکار داخل اون قرار بگیرن؟

<details>
<summary>نمایش پاسخ</summary>

خیر.

باید Local Repository رو به Remote Repository متصل کنیم و Commitها رو ارسال کنیم.

</details>

---

# ۵. دریافت آدرس Repository

بعد از ساخت Repository، آدرس اتصال اون رو از GitHub کپی کن.

برای این تمرین از روش زیر استفاده می‌کنیم:

**HTTPS**

آدرس معمولاً ساختاری شبیه این داره:

```text
https://github.com/USERNAME/my-first-remote.git
```

در این آدرس:

- `USERNAME` نام کاربری GitHub تو است.
- `my-first-remote` نام Repository است.
- `.git` پسوند رایج آدرس مخزن Git است.

**نکته:**

در دستورهای بعدی باید آدرس واقعی Repository خودت رو جایگزین آدرس نمونه کنی.

---

# ۶. Remote چیست؟

برای اینکه Git بدونه Repository آنلاین پروژه کجاست، باید آدرس اون رو ثبت کنیم.

این اتصال با مفهوم زیر مدیریت می‌شه:

**Remote**

یک Repository محلی می‌تونه یک یا چند Remote داشته باشه.

## دستور مشاهده Remoteها

```powershell
git remote -v
```

اگر تا الان Remote تعریف نکرده باشیم، معمولاً خروجی خالیه.

این موضوع خطا نیست.

یعنی هنوز هیچ Remote برای پروژه ثبت نشده.

## origin چیست؟

در Git معمولاً اولین Remote رو با نام زیر ثبت می‌کنیم:

`origin`

این نام فقط یک قرارداد رایجه.

می‌تونیم نام دیگری هم انتخاب کنیم، اما استفاده از `origin` بسیار متداوله.

### 🧠 سؤال مفهومی

آیا `origin` نام اجباری GitHub است؟

<details>
<summary>نمایش پاسخ</summary>

خیر.

`origin` نامی قراردادی برای یک Remote است و می‌توان نام دیگری انتخاب کرد.

</details>

---

# ۷. اتصال Local Repository به GitHub

حالا می‌خوایم آدرس Repository آنلاین رو به پروژه محلی معرفی کنیم.

## دستور اضافه کردن Remote

```powershell
git remote add origin https://github.com/USERNAME/my-first-remote.git
```

به‌جای `USERNAME` نام کاربری واقعی خودت رو قرار بده.

## توضیح دستور

### git remote

برای مدیریت Remoteهای پروژه استفاده می‌شه.

### add

یک Remote جدید اضافه می‌کنه.

### origin

نامی است که برای Remote انتخاب کردیم.

### Repository URL

آدرس Repository آنلاین است.

## نکته مهم

اجرای این دستور هنوز هیچ فایلی رو به GitHub ارسال نمی‌کنه.

فقط آدرس اتصال رو ثبت می‌کنه.

---

# ۸. بررسی اتصال Remote

دوباره دستور زیر رو اجرا کن:

```powershell
git remote -v
```

خروجی نمونه:

```text
origin  https://github.com/USERNAME/my-first-remote.git (fetch)
origin  https://github.com/USERNAME/my-first-remote.git (push)
```

## معنی خروجی

**fetch**

آدرسی که Git برای دریافت اطلاعات از اون استفاده می‌کنه.

**push**

آدرسی که Git برای ارسال تغییرات به اون استفاده می‌کنه.

این دو سطر الزاماً به معنی وجود دو Repository جدا نیستن.

در مثال ما هر دو به یک Repository اشاره می‌کنن.

### ⚡ سؤال سریع

اگر دستور زیر رو اجرا کنیم:

```powershell
git remote add origin https://github.com/USERNAME/my-first-remote.git
```

آیا فایل‌های پروژه در GitHub ظاهر می‌شن؟

<details>
<summary>نمایش پاسخ</summary>

خیر.

این دستور فقط اتصال رو ایجاد می‌کنه.

برای انتشار Commitها باید از `git push` استفاده کنیم.

</details>

---

# ۹. اولین Push

حالا به مهم‌ترین بخش جلسه رسیدیم.

می‌خوایم Commitهایی رو که در Local Repository ثبت کردیم، به GitHub ارسال کنیم.

## دستور اولین Push

اگر Branch اصلی پروژه `main` است:

```powershell
git push -u origin main
```

اگر Branch اصلی `master` است:

```powershell
git push -u origin master
```

## توضیح دستور

### git push

Commitهای موردنیاز و اطلاعات Branch رو به Remote ارسال می‌کنه.

### origin

نام Remote مقصد است.

### main

نام Branch محلی موردنظر برای ارسال است.

### -u

ارتباط بالادستی Branch محلی رو با Branch مربوط در Remote تنظیم می‌کنه.

این ارتباط با اصطلاح زیر شناخته می‌شه:

**Upstream**

## Upstream چه کاربردی داره؟

وقتی Upstream تنظیم شده باشه، Git می‌دونه Branch محلی معمولاً با کدوم Branch راه دور در ارتباطه.

به همین دلیل، برای Pushهای بعدی در شرایط معمول می‌تونیم دستور کوتاه‌تر زیر رو اجرا کنیم:

```powershell
git push
```

---

# ۱۰. خروجی اولین Push

خروجی ممکنه شبیه نمونه زیر باشه:

```text
To https://github.com/USERNAME/my-first-remote.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

## معنی خروجی

- Branch موردنظر به Remote ارسال شده.
- Branch متناظر در GitHub ایجاد شده.
- ارتباط Upstream تنظیم شده.

شناسه‌ها و جزئیات خروجی ممکنه در سیستم هر نفر متفاوت باشن.

## نکته درباره احراز هویت

ممکنه هنگام اولین Push، Git ازت بخواد وارد حساب GitHub بشی.

در Windows معمولاً می‌تونی با استفاده از پنجره احراز هویت و مرورگر وارد حساب خودت بشی.

اگر پنجره ورود باز شد، مراحل رسمی ورود رو دنبال کن.

> ⚠️ رمز عبور و Token حساب GitHub رو با دیگران به اشتراک نذار.

---

# ۱۱. مشاهده پروژه در GitHub

حالا به مرورگر برگرد.

صفحه Repository رو باز کن و Refresh بزن.

اگر Push موفق بوده باشه، باید بتونی موارد زیر رو مشاهده کنی:

- فایل‌های پروژه
- Commitهای ثبت‌شده
- Branch ارسال‌شده
- تاریخچه تغییرات پروژه

برای مثال، فایل زیر باید در Repository قابل مشاهده باشه:

`about-me.txt`

## بررسی وضعیت محلی

به PowerShell برگرد و اجرا کن:

```powershell
git status
```

سپس:

```powershell
git branch -vv
```

دستور دوم می‌تونه ارتباط Branch محلی با Upstream اون رو نمایش بده.

## بررسی History

```powershell
git log --oneline --graph --all --decorate
```

این دستور نمای خلاصه‌ای از History و محل اشاره‌گرهای Branch رو نمایش می‌ده.

### 🧠 سؤال مفهومی

آیا Push موفق باعث حذف Commitهای محلی می‌شه؟

<details>
<summary>نمایش پاسخ</summary>

خیر.

Commitهای محلی باقی می‌مونن و Commitهای موردنیاز به Remote هم ارسال می‌شن.

</details>

---

# ۱۲. تمرین عملی جلسه چهارم

در این تمرین باید پروژه جلسات قبلی رو روی GitHub منتشر کنی.

## مرحله ۱ — بررسی پروژه

```powershell
git status
git branch
git log --oneline
```

## مرحله ۲ — ساخت Repository آنلاین

در GitHub یک Repository خالی با نام زیر بساز:

```text
my-first-remote
```

## مرحله ۳ — بررسی Remote

```powershell
git remote -v
```

## مرحله ۴ — اضافه کردن Remote

اگر Remote موردنظر از قبل وجود نداره:

```powershell
git remote add origin https://github.com/USERNAME/my-first-remote.git
```

## مرحله ۵ — بررسی اتصال

```powershell
git remote -v
```

## مرحله ۶ — اولین Push

برای Branch اصلی `main`:

```powershell
git push -u origin main
```

## مرحله ۷ — مشاهده نتیجه

صفحه Repository رو در GitHub باز کن.

بررسی کن که فایل‌ها و Commitها نمایش داده می‌شن.

## مرحله ۸ — بررسی نهایی

```powershell
git status
git branch -vv
git log --oneline
```

### نتیجه مورد انتظار

در پایان تمرین باید:

- یک Repository در GitHub داشته باشی.
- پروژه محلی به اون متصل شده باشه.
- Commitهای پروژه در GitHub نمایش داده بشن.
- اولین Push با موفقیت انجام شده باشه.

---

# ۱۳. Challenge — بدون نگاه به راهنما

این چالش رو با یک Repository تمرینی جدید انجام بده.

۱. یک پوشه جدید بساز.

۲. داخل اون یک Repository محلی ایجاد کن.

۳. یک فایل متنی با اطلاعات دلخواه بساز.

۴. فایل رو Stage کن.

۵. اولین Commit رو ایجاد کن.

۶. یک Repository خالی در GitHub بساز.

۷. آدرس Remote رو ثبت کن.

۸. اولین Push رو انجام بده.

۹. مطمئن شو فایل در GitHub نمایش داده می‌شه.

<details>
<summary>نمایش راهنمای پاسخ</summary>

### ساخت پوشه تمرینی

```powershell
mkdir git-remote-challenge
cd git-remote-challenge
```

### ساخت Repository

```powershell
git init -b main
```

### ایجاد فایل

```powershell
notepad about-me.txt
```

اگر Notepad پرسید فایل جدید ساخته بشه، تأیید کن.

چند خط داخل فایل بنویس و ذخیره کن.

### ثبت تغییر

```powershell
git add about-me.txt
git commit -m "Add my profile"
```

### بررسی History

```powershell
git log --oneline
```

### ساخت Remote

در GitHub یک Repository خالی بساز.

سپس آدرس واقعی اون رو در دستور زیر جایگزین کن:

```powershell
git remote add origin https://github.com/USERNAME/git-remote-challenge.git
```

### اولین Push

```powershell
git push -u origin main
```

### بررسی نهایی

```powershell
git remote -v
git status
git branch -vv
```

در پایان، فایل رو در GitHub مشاهده کن.

</details>

---

# ۱۴. مشکلات رایج

## خطای not a git repository

پیام نمونه:

```text
fatal: not a git repository
```

احتمالاً داخل پوشه درست پروژه نیستی.

مسیر رو بررسی کن:

```powershell
Get-Location
```

---

## خطای remote origin already exists

پیام:

```text
error: remote origin already exists
```

این خطا یعنی Remote با نام `origin` از قبل وجود داره.

ابتدا بررسی کن:

```powershell
git remote -v
```

اگر آدرس اشتباه بود، بعد از اطمینان می‌تونی اصلاحش کنی:

```powershell
git remote set-url origin https://github.com/USERNAME/my-first-remote.git
```

---

## خطای src refspec main does not match any

پیام:

```text
src refspec main does not match any
```

دو علت احتمالی:

- نام Branch اصلی `main` نیست.
- هنوز هیچ Commit ایجاد نشده.

برای بررسی:

```powershell
git branch
git log --oneline
```

---

## خطای Repository not found

پیام نمونه:

```text
Repository not found
```

موارد زیر رو بررسی کن:

- آدرس Repository درست باشه.
- نام کاربری صحیح باشه.
- Repository واقعاً ایجاد شده باشه.
- به Repository دسترسی داشته باشی.

---

## خطای Authentication failed

پیام نمونه:

```text
Authentication failed
```

ممکنه ورود به حساب GitHub یا مجوز دسترسی مشکل داشته باشه.

از روش رسمی احراز هویت GitHub استفاده کن.

---

## خطای rejected یا non-fast-forward

پیام نمونه:

```text
failed to push some refs
```

ممکنه Remote دارای Commitهایی باشه که در Local Repository وجود ندارن.

برای تمرین این جلسه، بهتره Repository آنلاین رو از ابتدا خالی بسازی.

**هشدار:**

برای رفع سریع این خطا بدون آگاهی از نتیجه، از دستور زیر استفاده نکن:

`git push --force`

چون ممکنه تاریخچه Branch راه دور رو بازنویسی کنه.

---

# ۱۵. خلاصه دستورات جلسه

## بررسی وضعیت

```powershell
git status
```

## مشاهده Branchها

```powershell
git branch
```

## مشاهده History

```powershell
git log --oneline
```

## مشاهده Remoteها

```powershell
git remote -v
```

## اضافه کردن Remote

```powershell
git remote add origin URL
```

## اصلاح آدرس Remote

```powershell
git remote set-url origin URL
```

## اولین Push

```powershell
git push -u origin main
```

## Pushهای بعدی

```powershell
git push
```

## بررسی Upstream

```powershell
git branch -vv
```

## مشاهده نمودار History

```powershell
git log --oneline --graph --all --decorate
```

---

# ۱۶. جمع‌بندی جلسه

در این جلسه یاد گرفتیم که Git و GitHub دو مفهوم متفاوت هستن.

با مفهوم Repository محلی و Repository راه دور آشنا شدیم.

یاد گرفتیم چطور در GitHub یک Repository ایجاد کنیم و اون رو به پروژه محلی خودمون متصل کنیم.

همچنین با دستور زیر، Commitهای پروژه رو برای اولین بار به GitHub ارسال کردیم:

```powershell
git push -u origin main
```

**نتیجه نهایی:**

حالا می‌تونیم پروژه‌ای رو که روی کامپیوتر خودمون ساختیم، در GitHub هم منتشر کنیم.

---

# ۱۷. جلسه بعد چه چیزی یاد می‌گیریم؟

در جلسه آینده یاد می‌گیریم چطور یک Repository موجود رو از GitHub روی سیستم خودمون دریافت کنیم.

همچنین بررسی می‌کنیم چطور تغییرات جدید مخزن راه دور رو دریافت و با پروژه محلی هماهنگ کنیم.

موضوعات آینده:

- Clone
- Fetch
- Pull
- Collaboration

---

# منابع معتبر

## کتاب Pro Git

Working with Remotes

https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes

## مستندات رسمی Git

git-remote

https://git-scm.com/docs/git-remote

git-push

https://git-scm.com/docs/git-push

## راهنمای رسمی GitHub

Adding a local repository to GitHub

https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github

---

**Version Control with Git & GitHub**

مطالب آموزشی دوره:

https://github.com/Milad-theOne/version-control-with-git
