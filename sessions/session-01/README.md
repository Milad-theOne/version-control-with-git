# جلسه ۱ — شروع کار با Git

```text
Version Control & Git Basics
```

---

## امروز قراره چی یاد بگیریم؟

تا پایان این جلسه می‌تونیم:

- بفهمیم چرا به Version Control نیاز داریم.
- تفاوت Git و GitHub رو بدونیم.
- اولین Repository خودمون رو بسازیم.
- وضعیت فایل‌های پروژه رو بررسی کنیم.
- مفهوم Working Directory و Staging Area رو درک کنیم.
- اولین Commit خودمون رو ایجاد کنیم.
- تاریخچه اولیه پروژه رو ببینیم.

---

# ۱. یک مشکل واقعی

فرض کنید سه روز روی یک پروژه برنامه‌نویسی کار کردیم.

دیروز پروژه کاملاً سالم بود.

امروز چند قسمت از کد رو تغییر دادیم و ناگهان برنامه خراب شد.

حالا سؤال اصلی:

> **نسخه سالم دیروز کجاست؟**

شاید اولین راهی که به ذهنمون برسه این باشه:

```text
project/
project-final/
project-final-2/
project-final-new/
project-final-final/
project-final-REAL/
project-final-REAL-final/
```

برای یک پروژه خیلی کوچک شاید این روش مدتی جواب بده.

اما خیلی زود با چند مشکل روبه‌رو می‌شیم:

- کدوم نسخه جدیدتره؟
- کدوم نسخه سالمه؟
- در هر نسخه چه چیزی تغییر کرده؟
- چرا اون تغییر انجام شده؟
- چه کسی اون تغییر رو انجام داده؟
- اگر چند نفر روی پروژه کار کنن چی میشه؟

برای حل این مشکل به روش بهتری نیاز داریم.

اصطلاح اصلی:

```text
Version Control
```

---

## ⚡ سؤال سریع

فرض کنید ۲۰ نسخه از یک پروژه رو در ۲۰ پوشه جدا نگه داشتیم.

مهم‌ترین مشکل این روش چیه؟

<details>
<summary>نمایش پاسخ</summary>

مدیریت نسخه‌ها سخت میشه.

همچنین به‌راحتی نمی‌تونیم بفهمیم در هر نسخه دقیقاً چه تغییری انجام شده.

</details>

---

# ۲. Version Control چیست؟

نام کامل:

```text
Version Control System
```

مخفف:

```text
VCS
```

Version Control سیستمیه برای مدیریت و ثبت تغییرات فایل‌های یک پروژه در طول زمان.

به زبان ساده:

> **یعنی تاریخچه تغییرات پروژه رو به‌شکل منظم و قابل‌کنترل نگه داریم.**

مثلاً:

```text
Project
   |
   +-- Version 1
   |
   +-- Version 2
   |
   +-- Version 3
   |
   +-- Version 4
```

با استفاده از Version Control می‌تونیم بفهمیم:

- چه چیزی تغییر کرده؟
- چه زمانی تغییر کرده؟
- چه کسی تغییر رو انجام داده؟
- نسخه قبلی پروژه چی بوده؟
- پروژه در طول زمان چطور تغییر کرده؟

---

## یک مثال ساده

یک فایل داریم:

```text
hello.txt
```

نسخه اول:

```text
Hello
```

بعد تغییرش می‌دیم:

```text
Hello Milad
```

و دوباره تغییرش می‌دیم:

```text
Hello Milad
Welcome to Git!
```

حالا تاریخچه می‌تونه به این شکل باشه:

```text
Version 1
    |
    v
Version 2
    |
    v
Version 3
```

دیگه لازم نیست برای هر تغییر، یک کپی کامل از پروژه بسازیم.

---

## 🧠 سؤال مفهومی

آیا Version Control فقط برای فایل‌های برنامه‌نویسی استفاده میشه؟

<details>
<summary>نمایش پاسخ</summary>

خیر.

Version Control فقط مخصوص سورس‌کد نیست.

اما برای فایل‌های متنی و پروژه‌های برنامه‌نویسی بسیار کاربردیه.

</details>

---

# ۳. Git چیست؟

Version Control یک مفهوم کلیه.

ابزاری که ما برای انجام این کار استفاده می‌کنیم:

```text
Git
```

است.

نام فنی Git:

```text
Distributed Version Control System
```

فعلاً لازم نیست وارد جزئیات کلمه زیر بشیم:

```text
Distributed
```

چیزی که الان مهمه:

> **Git ابزاری برای مدیریت تغییرات و تاریخچه پروژه است.**

---

## آیا Git به اینترنت نیاز دارد؟

خیر.

Git می‌تونه روی سیستم خودمون کار کنه.

```text
My Computer
     |
     v
    Git
     |
     v
Project History
```

یعنی حتی بدون اینترنت هم می‌تونیم روی پروژه خودمون Commit ایجاد کنیم.

---

## ⚡ سؤال سریع

اینترنت قطع شده.

آیا هنوز می‌تونیم Commit ایجاد کنیم؟

<details>
<summary>نمایش پاسخ</summary>

بله.

Git می‌تونه کاملاً به‌صورت Local روی سیستم خودمون کار کنه.

</details>

---

# ۴. تفاوت Git و GitHub

یکی از اشتباهات رایج:

```text
Git = GitHub
```

این عبارت اشتباهه.

---

## Git

```text
Git
```

یک ابزار برای Version Control است.

می‌تونه روی سیستم خودمون کار کنه.

```text
My Computer
     |
     v
    Git
```

---

## GitHub

```text
GitHub
```

یک سرویس آنلاینه برای نگهداری Repositoryهای Git و همکاری روی پروژه‌ها.

بعداً به چنین ساختاری می‌رسیم:

```text
Local Repository
       |
       v
     GitHub
```

فعلاً تمام کار ما روی سیستم خودمون انجام میشه.

---

## 🧠 سؤال مفهومی

تفاوت اصلی این دو چیه؟

```text
Git
```

```text
GitHub
```

<details>
<summary>نمایش پاسخ</summary>

Git ابزار Version Control است.

GitHub یک سرویس آنلاین برای میزبانی Repositoryهای Git و همکاری روی پروژه‌هاست.

</details>

---

# ۵. بررسی نصب Git

اول باید ببینیم Git روی سیستم نصب شده یا نه.

Terminal رو باز می‌کنیم.

مثلاً:

```text
PowerShell
Command Prompt
Git Bash
VS Code Terminal
```

بعد اجرا می‌کنیم:

```bash
git --version
```

ممکنه خروجی شبیه این باشه:

```text
git version 2.x.x
```

اگر Version نمایش داده شد، یعنی Git نصب شده.

---

## معرفی خودمون به Git

هر Commit اطلاعات سازنده خودش رو هم داره.

نام خودمون رو تنظیم می‌کنیم:

```bash
git config --global user.name "Your Name"
```

مثلاً:

```bash
git config --global user.name "Ali Ahmadi"
```

ایمیل:

```bash
git config --global user.email "you@example.com"
```

بررسی نام:

```bash
git config --global user.name
```

بررسی ایمیل:

```bash
git config --global user.email
```

---

## این گزینه یعنی چی؟

```text
--global
```

یعنی این تنظیم برای کاربر فعلی سیستم ذخیره بشه.

---

## ⚡ سؤال سریع

دستور زیر چه کاری انجام می‌ده؟

```bash
git --version
```

<details>
<summary>نمایش پاسخ</summary>

Version نصب‌شده Git رو نمایش می‌ده.

هیچ Repository ایجاد نمی‌کنه.

</details>

---

## 🧠 سؤال مفهومی

چرا Git نام و ایمیل ما رو ذخیره می‌کنه؟

<details>
<summary>نمایش پاسخ</summary>

برای اینکه مشخص باشه هر Commit توسط چه کسی ایجاد شده.

</details>

---

# ۶. Repository چیست؟

یکی از مهم‌ترین اصطلاحات Git:

```text
Repository
```

نام کوتاه:

```text
Repo
```

Repository محیطیه که Git اطلاعات پروژه و تاریخچه تغییرات اون رو مدیریت می‌کنه.

فرض کنید این پوشه رو داریم:

```text
my-project/
|
+-- main.py
+-- README.md
+-- notes.txt
```

فعلاً این فقط یک پوشه معمولیه.

Git هنوز مدیریت History اون رو شروع نکرده.

---

## ساخت اولین Repository

یک پوشه جدید می‌سازیم:

```text
git-first-project
```

Terminal رو داخل همون پوشه باز می‌کنیم.

بعد اجرا می‌کنیم:

```bash
git init
```

ممکنه خروجی شبیه این ببینیم:

```text
Initialized empty Git repository
```

حالا پوشه ما تبدیل به یک Git Repository شده.

---

## پشت صحنه چه اتفاقی افتاد؟

بعد از اجرای:

```bash
git init
```

یک پوشه مخفی داخل پروژه ساخته میشه:

```text
.git
```

ساختار پروژه تقریباً به این شکله:

```text
git-first-project/
|
+-- .git/
```

اطلاعات داخلی Git داخل این بخش مدیریت میشه.

> فعلاً هیچ چیزی داخل پوشه `.git` رو دستی تغییر نمی‌دیم.

---

## ⚡ سؤال سریع

آیا هر Folder روی سیستم به‌صورت خودکار Repository محسوب میشه؟

<details>
<summary>نمایش پاسخ</summary>

خیر.

ابتدا باید Git رو داخل اون Initialize کنیم.

</details>

---

## 🧠 سؤال مفهومی

دستور زیر چه کاری انجام می‌ده؟

```bash
git init
```

**A)** پروژه رو روی GitHub می‌فرسته

**B)** پوشه فعلی رو به Git Repository تبدیل می‌کنه

**C)** یک Commit ایجاد می‌کنه

<details>
<summary>نمایش پاسخ</summary>

**B**

پوشه فعلی رو برای استفاده از Git آماده می‌کنه.

</details>

---

# ۷. وضعیت Repository

یکی از مهم‌ترین دستورهای Git:

```bash
git status
```

این دستور وضعیت فعلی Repository رو نشون می‌ده.

با استفاده از اون می‌تونیم بفهمیم:

- فایل جدیدی وجود داره یا نه.
- فایلی تغییر کرده یا نه.
- چه تغییراتی آماده Commit هستن.
- چه تغییراتی هنوز آماده نشدن.

یک قانون کاربردی:

> **اگر نمی‌دونیم داخل Repository چه خبره، یکی از اولین دستورهای خوب اینه:**

```bash
git status
```

---

## اولین فایل پروژه

داخل پروژه یک فایل می‌سازیم:

```text
about-me.txt
```

داخلش می‌نویسیم:

```text
Name: Ali
Major: Computer Engineering
Favorite Language: Python
```

حالا دوباره اجرا می‌کنیم:

```bash
git status
```

احتمالاً Git فایل رو در بخش زیر نمایش می‌ده:

```text
Untracked files
```

---

# ۸. Untracked یعنی چه؟

وضعیت:

```text
Untracked
```

یعنی فایل داخل پروژه وجود داره، اما Git هنوز اون رو وارد History نکرده.

```text
about-me.txt
      |
      v
  Untracked
```

فایل وجود داره.

اما هنوز هیچ Commitی از اون نداریم.

---

## ⚡ سؤال سریع

یک فایل جدید ساختیم.

هنوز هیچ دستور دیگه‌ای اجرا نکردیم.

وضعیت فایل چیه؟

<details>
<summary>نمایش پاسخ</summary>

```text
Untracked
```

</details>

---

# ۹. مدل اصلی کار با Git

این مهم‌ترین شکل جلسه امروزه:

```text
+-------------------+
| Working Directory |
+---------+---------+
          |
          | git add
          v
+-------------------+
|   Staging Area    |
+---------+---------+
          |
          | git commit
          v
+-------------------+
| Repository History|
+-------------------+
```

اگر این مدل رو خوب بفهمیم، بخش بزرگی از مفاهیم اولیه Git ساده میشه.

---

# ۱۰. Working Directory

اصطلاح:

```text
Working Directory
```

همون فایل‌های پروژه‌ای هستن که الان روی اون‌ها کار می‌کنیم.

مثلاً:

```text
git-first-project/
|
+-- about-me.txt
```

وقتی فایل رو داخل VS Code باز می‌کنیم و تغییر می‌دیم، داریم روی Working Directory کار می‌کنیم.

---

## ⚡ سؤال سریع

فایل زیر رو داخل VS Code باز کردیم و یک خط بهش اضافه کردیم:

```text
main.py
```

در کدوم بخش از Workflow قرار داریم؟

<details>
<summary>نمایش پاسخ</summary>

```text
Working Directory
```

</details>

---

# ۱۱. Staging Area

اصطلاح بعدی:

```text
Staging Area
```

ممکنه چند تغییر مختلف در پروژه داشته باشیم.

ولی نخواهیم همه اون‌ها داخل Commit بعدی قرار بگیرن.

اینجاست که Staging Area وارد میشه.

به‌صورت ساده:

```text
Changes
   |
   v
Select Changes
   |
   v
Staging Area
   |
   v
Commit
```

در این مرحله مشخص می‌کنیم چه تغییراتی باید داخل Commit بعدی قرار بگیرن.

> Staging Area یک Folder معمولی نیست.

این بخش توسط Git مدیریت میشه.

---

## 🧠 سؤال مفهومی

چرا هر تغییری که ایجاد می‌کنیم، بلافاصله Commit نمیشه؟

<details>
<summary>نمایش پاسخ</summary>

چون ممکنه چند تغییر مختلف داشته باشیم.

Staging Area به ما اجازه می‌ده مشخص کنیم دقیقاً چه تغییراتی وارد Commit بعدی بشن.

</details>

---

# ۱۲. دستور git add

می‌خوایم محتوای فعلی فایل زیر رو برای Commit بعدی آماده کنیم:

```text
about-me.txt
```

دستور:

```bash
git add about-me.txt
```

بعد دوباره وضعیت رو بررسی می‌کنیم:

```bash
git status
```

حالا تغییر فایل برای Commit آماده شده.

---

## قبل از git add

```text
Working Directory

about-me.txt
     |
     v
Untracked
```

---

## بعد از git add

```text
Working Directory
       |
       | git add
       v
  Staging Area
```

نکته مهم:

> دستور `git add` فایل رو از یک Folder به Folder دیگه منتقل نمی‌کنه.

محتوای فعلی فایل رو برای Commit بعدی Stage می‌کنه.

---

## یک مثال

فرض کنید سه فایل تغییر کردن:

```text
main.py
README.md
notes.txt
```

اما فقط می‌خوایم تغییر فایل زیر وارد Commit بعدی بشه:

```text
main.py
```

اجرا می‌کنیم:

```bash
git add main.py
```

فقط تغییر موردنظر برای Commit بعدی آماده میشه.

---

## ⚡ سؤال سریع

سه فایل تغییر کردن.

فقط می‌خوایم تغییرات فایل زیر وارد Commit بعدی بشه:

```text
main.py
```

چه دستوری اجرا می‌کنیم؟

<details>
<summary>نمایش پاسخ</summary>

```bash
git add main.py
```

</details>

---

# ۱۳. Commit چیست؟

اصطلاح:

```text
Commit
```

Commit یک نقطه ثبت‌شده در History پروژه است.

می‌تونیم اون رو شبیه یک Snapshot از تغییرات آماده‌شده در نظر بگیریم.

```text
Commit 1
Create project
     |
     v
Commit 2
Add profile
     |
     v
Commit 3
Add login page
```

هر Commit یک مرحله از History پروژه رو ثبت می‌کنه.

به زبان ساده:

> **Commit یعنی تغییرات انتخاب‌شده رو به‌عنوان یک نقطه در History پروژه ثبت کنیم.**

---

# ۱۴. اولین Commit

حالا اجرا می‌کنیم:

```bash
git commit -m "Add my profile"
```

اولین Commit ما ساخته میشه. 🎉

---

## این گزینه چیست؟

```text
-m
```

این گزینه اجازه می‌ده Commit Message رو مستقیماً داخل Command وارد کنیم.

پیام ما:

```text
Add my profile
```

است.

---

# ۱۵. Commit Message

هر Commit باید یک پیام مناسب داشته باشه.

پیام باید خیلی سریع مشخص کنه:

> **این Commit چه کاری انجام داده؟**

مثال‌های مناسب:

```text
Add user profile
```

```text
Fix login validation
```

```text
Update README
```

مثال‌های ضعیف:

```text
changes
```

```text
final
```

```text
asdf
```

---

## 🧠 سؤال مفهومی

تفاوت این دو دستور چیه؟

```bash
git add
```

```bash
git commit
```

<details>
<summary>نمایش پاسخ</summary>

دستور اول:

```text
git add
```

تغییرات موردنظر رو برای Commit بعدی آماده می‌کنه.

دستور دوم:

```text
git commit
```

تغییرات آماده‌شده رو در History پروژه ثبت می‌کنه.

</details>

---

## ⚡ سؤال سریع

کدام Commit Message بهتره؟

```text
A) changes
```

```text
B) Fix login validation
```

<details>
<summary>نمایش پاسخ</summary>

```text
B) Fix login validation
```

چون مشخص می‌کنه Commit چه تغییری انجام داده.

</details>

---

# ۱۶. دوباره وضعیت پروژه

بعد از Commit دوباره اجرا می‌کنیم:

```bash
git status
```

اگر هیچ تغییر جدیدی ایجاد نکرده باشیم، چیزی برای Commit کردن وجود نداره.

در این حالت می‌تونیم بگیم Working Tree فعلاً Clean است.

```text
Clean Working Tree
```

---

# ۱۷. فایل را دوباره تغییر می‌دهیم

فایل زیر رو باز می‌کنیم:

```text
about-me.txt
```

یک خط جدید اضافه می‌کنیم:

```text
Goal: Learn Git
```

فایل رو ذخیره می‌کنیم.

دوباره:

```bash
git status
```

رو اجرا می‌کنیم.

این بار وضعیت فایل:

```text
Modified
```

است.

---

# ۱۸. تفاوت Untracked و Modified

وضعیت اول:

```text
Untracked
```

یعنی Git هنوز فایل رو Track نمی‌کنه.

وضعیت دوم:

```text
Modified
```

یعنی Git فایل رو از قبل می‌شناسه، اما از آخرین Commit تغییر کرده.

---

## ⚡ سؤال سریع

یک فایل قبلاً Commit شده.

حالا یک خط جدید بهش اضافه کردیم.

وضعیت فایل چیه؟

<details>
<summary>نمایش پاسخ</summary>

```text
Modified
```

</details>

---

# ۱۹. چهار وضعیت مهم فایل‌ها

فعلاً چهار وضعیت اصلی برای ما مهمه.

---

## حالت اول

```text
Untracked
```

Git هنوز فایل رو Track نمی‌کنه.

---

## حالت دوم

```text
Modified
```

فایل Track شده، اما تغییر کرده.

---

## حالت سوم

```text
Staged
```

تغییر برای Commit بعدی آماده شده.

---

## حالت چهارم

```text
Unmodified
```

فایل نسبت به آخرین Commit تغییری نکرده.

---

## چرخه ساده فایل

```text
Untracked
    |
    | git add
    v
 Staged
    |
    | git commit
    v
Unmodified
    |
    | edit
    v
 Modified
    |
    | git add
    v
 Staged
```

---

## 🧠 سؤال مفهومی

یک فایل رو Commit کردیم.

بعد از اون هیچ تغییری روی فایل انجام ندادیم.

وضعیتش چیه؟

<details>
<summary>نمایش پاسخ</summary>

```text
Unmodified
```

</details>

---

# ۲۰. Commit دوم

تغییر جدید رو آماده می‌کنیم:

```bash
git add about-me.txt
```

بعد ثبتش می‌کنیم:

```bash
git commit -m "Add learning goal"
```

حالا Repository ما حداقل دو Commit داره.

---

# ۲۱. مشاهده History

برای دیدن Commitهایی که ساختیم:

```bash
git log --oneline
```

ممکنه چیزی شبیه این ببینیم:

```text
a1b2c3d Add learning goal
e4f5g6h Add my profile
```

حالا پروژه ما واقعاً History داره.

در این جلسه فقط نتیجه رو مشاهده می‌کنیم.

بررسی دقیق History رو در جلسه بعد انجام می‌دیم.

---

## ⚡ سؤال سریع

اگر سه Commit ایجاد کنیم، Git فقط آخرین Commit رو نگه می‌داره؟

<details>
<summary>نمایش پاسخ</summary>

خیر.

Commitهای قبلی هم داخل History باقی می‌مونن.

</details>

---

# ۲۲. کل Workflow جلسه

```text
Create / Edit File
        |
        v
   git status
        |
        v
     git add
        |
        v
  Staging Area
        |
        v
   git commit
        |
        v
     History
```

---

# ۲۳. تمرین عملی

حالا همه مراحل رو از ابتدا انجام بدید.

یک Folder بسازید:

```text
my-first-repo
```

اون رو به یک Repository تبدیل کنید.

یک فایل بسازید:

```text
about-me.txt
```

مثلاً:

```text
Name: Sara
Major: Computer Engineering
Favorite Language: C++
```

اولین Commit رو با Message زیر بسازید:

```text
Add my profile
```

---

# Challenge

این مرحله رو بدون نگاه کردن به دستورات قبلی انجام بدید.

یک فایل جدید بسازید:

```text
goals.txt
```

داخلش سه هدف بنویسید:

```text
Learn Git
Learn Python
Build a real project
```

اون رو در یک Commit جدید با Message زیر ثبت کنید:

```text
Add my goals
```

در پایان History رو ببینید:

```bash
git log --oneline
```

باید حداقل دو Commit مشاهده کنید.

---

# سؤال نهایی جلسه

یک فایل جدید ساختیم:

```text
project.txt
```

بعد اجرا کردیم:

```bash
git add project.txt
```

اما هنوز Commit ایجاد نکردیم.

الان تغییر فایل در کدوم مرحله قرار داره؟

```text
Working Directory
       |
       | git add
       v
  Staging Area
       |
       | git commit
       v
Repository History
```

<details>
<summary>نمایش پاسخ</summary>

```text
Staging Area
```

تغییر برای Commit آماده شده، اما هنوز داخل History ثبت نشده.

</details>

---

# مهم‌ترین شکل جلسه

```text
Working Directory
       |
       | git add
       v
  Staging Area
       |
       | git commit
       v
Repository History
```

---

# Cheat Sheet

بررسی نصب:

```bash
git --version
```

تنظیم نام:

```bash
git config --global user.name "Your Name"
```

تنظیم ایمیل:

```bash
git config --global user.email "you@example.com"
```

ساخت Repository:

```bash
git init
```

بررسی وضعیت:

```bash
git status
```

آماده‌کردن یک فایل:

```bash
git add <file>
```

مثال:

```bash
git add about-me.txt
```

ایجاد Commit:

```bash
git commit -m "message"
```

مثال:

```bash
git commit -m "Add my profile"
```

مشاهده سریع History:

```bash
git log --oneline
```

---

# جمع‌بندی

امروز از این سؤال شروع کردیم:

> **نسخه قبلی پروژه کجاست؟**

بعد با این مفهوم آشنا شدیم:

```text
Version Control
```

ابزار اصلی دوره رو شناختیم:

```text
Git
```

و این مسیر رو یاد گرفتیم:

```text
Working Directory
       |
       | git add
       v
  Staging Area
       |
       | git commit
       v
Repository History
```

حالا می‌تونیم:

- یک Repository بسازیم.
- وضعیت فایل‌ها رو بررسی کنیم.
- فایل جدید رو تشخیص بدیم.
- تغییرات موردنظر رو Stage کنیم.
- Commit ایجاد کنیم.
- فایل Track شده رو دوباره تغییر بدیم.
- Commit دوم ایجاد کنیم.
- History اولیه پروژه رو ببینیم.

---

# جلسه بعد

حالا یک سؤال جدید داریم:

> **Git تغییرات رو ثبت کرده؛ چطور بفهمیم دقیقاً چه چیزی تغییر کرده؟**

موضوعات جلسه بعد:

```text
git log
git diff
Commit History
Comparing Changes
Basic Undo
```
