
# جلسه ۲ — تاریخچه، مقایسه و مدیریت تغییرات

**Git History, Diff & Basic Undo**

در جلسه اول یاد گرفتیم چطور یک Repository بسازیم، فایل‌ها رو Stage کنیم و Commit ایجاد کنیم.

امروز می‌خوایم Commitهای قبلی رو ببینیم، تغییرات رو قبل از Commit مقایسه کنیم و اشتباهات ساده رو اصلاح کنیم.

---

## اهداف یادگیری

تا پایان این جلسه می‌تونیم:

- History پروژه رو با `git log` مشاهده کنیم.
- جزئیات یک Commit رو با `git show` بررسی کنیم.
- تغییرات Unstaged رو با `git diff` ببینیم.
- تغییرات Staged رو با `git diff --staged` مقایسه کنیم.
- تغییرات رو بدون حذف ویرایش‌ها Unstage کنیم.
- تغییرات آزمایشی رو با احتیاط کنار بذاریم.

---

# ۱. شروع از Repository جلسه قبل

در Windows، برنامه File Explorer رو باز کن و وارد پوشه Repository جلسه قبل شو.

مثلاً:

```text
Desktop/
└── Git-Class/
    └── git-first-project/
        └── about-me.txt
```

داخل پوشه `git-first-project`، روی نوار آدرس File Explorer کلیک کن، عبارت زیر رو بنویس و Enter بزن:

```text
powershell
```

حالا PowerShell داخل پوشه پروژه باز می‌شه.

### مرحله اول: بررسی Git

```powershell
git --version
```

### مرحله دوم: بررسی مسیر فعلی

```powershell
Get-Location
```

### مرحله سوم: بررسی وضعیت Repository

```bash
git status
```

اگر تغییر ثبت‌نشده‌ای نداشته باشیم، خروجی شبیه اینه:

```text
On branch main
nothing to commit, working tree clean
```

ممکنه نام Branch در سیستم شما متفاوت باشه.

> اگر تغییرات مهم و ثبت‌نشده‌ای داری، قبل از ادامه تمرین اون‌ها رو بررسی کن و بدون اطمینان حذفشون نکن.

### مرحله چهارم: مشاهده فایل‌ها

```powershell
Get-ChildItem -Name
```

### مرحله پنجم: مشاهده محتوای فایل

```powershell
Get-Content .\about-me.txt
```

محتوای نمونه:

```text
Name: Ali
Major: Computer Engineering
Favorite Language: Python
Goal: Learn Git
```

اگر اطلاعات یا نام فایل شما متفاوته، از اطلاعات واقعی پروژه خودتون استفاده کنید.

---

# ۲. مشاهده Commit History

هر Commit یک نقطه ثبت‌شده در History پروژه است.

فرض کنیم در جلسه قبل دو Commit ایجاد کردیم:

```text
Commit 1: Add my profile
          |
          v
Commit 2: Add learning goal
```

## دستور git log

برای مشاهده History:

```bash
git log
```

خروجی نمونه:

```text
commit 5d6e7f8123456789...
Author: Ali Ahmadi <ali@example.com>
Date:   Tue Oct 20 10:30:00 2026

    Add learning goal

commit 1a2b3c4123456789...
Author: Ali Ahmadi <ali@example.com>
Date:   Tue Oct 20 10:10:00 2026

    Add my profile
```

در خروجی این اطلاعات رو داریم:

- **Commit Hash:** شناسه مخصوص Commit
- **Author:** نام و ایمیل ثبت‌کننده
- **Date:** زمان ثبت Commit
- **Commit Message:** توضیح کوتاه درباره تغییر

اعداد، تاریخ‌ها و نام‌ها نمونه هستن و در سیستم هر نفر متفاوت خواهند بود.

اگر خروجی داخل Pager نمایش داده شد، برای خروج کلید `q` رو فشار بده.

## دستور git log --oneline

برای نمایش خلاصه History:

```bash
git log --oneline
```

خروجی نمونه:

```text
5d6e7f8 Add learning goal
1a2b3c4 Add my profile
```

هر خط شامل Hash کوتاه و Commit Message است.

معمولاً Commit جدیدتر در بالای فهرست قرار می‌گیره.

### ⚡ سؤال سریع

تفاوت این دو دستور چیه؟

```bash
git log
git log --oneline
```

<details>
<summary>نمایش پاسخ</summary>

`git log` جزئیات بیشتری نمایش می‌ده.

`git log --oneline` هر Commit رو در یک خط خلاصه می‌کنه.

</details>

---

# ۳. بررسی جزئیات یک Commit

تا اینجا فهمیدیم چه Commitهایی داریم.

اما چطور بفهمیم داخل یک Commit دقیقاً چه چیزی تغییر کرده؟

## دستور git show

```bash
git show
```

این دستور به‌صورت پیش‌فرض جزئیات آخرین Commit فعلی رو نمایش می‌ده.

بخشی از خروجی نمونه:

```diff
+Goal: Learn Git
```

علامت `+` یعنی خط اضافه شده.

علامت `-` یعنی خط حذف شده.

## بررسی یک Commit مشخص

ابتدا History رو مشاهده کن:

```bash
git log --oneline
```

بعد Hash واقعی یکی از Commitها رو بردار.

مثلاً:

```bash
git show 1a2b3c4
```

> شناسه `1a2b3c4` فقط نمونه است. باید Hash واقعی Repository خودتون رو جایگزین کنید.

### 🧠 سؤال مفهومی

برای مشاهده تغییرات آخرین Commit از چه دستوری استفاده می‌کنیم؟

<details>
<summary>نمایش پاسخ</summary>

```bash
git show
```

</details>

---

# ۴. تغییر فایل و مشاهده Diff

فرض کن می‌خوایم فایل `about-me.txt` رو ویرایش کنیم.

ابتدا فایل رو باز کن:

```powershell
notepad .\about-me.txt
```

این خط رو در انتهای فایل اضافه کن:

```text
Favorite Tool: Git
```

با `Ctrl + S` فایل رو ذخیره کن.

حالا به PowerShell برگرد.

## بررسی وضعیت

```bash
git status
```

باید فایل در بخش زیر نمایش داده بشه:

```text
Changes not staged for commit:
        modified:   about-me.txt
```

یعنی فایل تغییر کرده، اما تغییر هنوز Staged نیست.

## دستور git diff

```bash
git diff
```

بخشی از خروجی نمونه:

```diff
 Name: Ali
 Major: Computer Engineering
 Favorite Language: Python
 Goal: Learn Git
+Favorite Tool: Git
```

علامت‌ها:

```diff
+Added line
-Deleted line
```

برای مثال:

```diff
-Favorite Language: Python
+Favorite Language: Java
```

یعنی مقدار قبلی با مقدار جدید جایگزین شده.

**نکته:** دستور `git diff` خودش هیچ فایلی رو تغییر نمی‌ده.

همچنین `git diff` به‌صورت پیش‌فرض محتوای فایل‌های Untracked رو نمایش نمی‌ده.

### ⚡ سؤال سریع

خروجی زیر چه معنایی داره؟

```diff
-Color: Blue
+Color: Green
```

<details>
<summary>نمایش پاسخ</summary>

مقدار `Color` از `Blue` به `Green` تغییر کرده.

</details>

---

# ۵. تفاوت Staged و Unstaged

مدل اصلی Git رو از جلسه اول به یاد بیاریم:

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

الان فایل تغییر کرده، ولی هنوز Stage نشده.

## مرحله اول: Stage کردن تغییر

```bash
git add about-me.txt
```

وضعیت رو بررسی کن:

```bash
git status
```

خروجی نمونه:

```text
Changes to be committed:
        modified:   about-me.txt
```

## مرحله دوم: اجرای git diff

```bash
git diff
```

در تمرین ما خروجی خالیه.

چرا؟

چون محتوای Working Directory و Staging Area یکسان شده.

**آیا تغییر از بین رفته؟**

خیر! تغییر فقط Stage شده.

## مرحله سوم: اجرای git diff --staged

```bash
git diff --staged
```

حالا دوباره تغییر رو می‌بینیم:

```diff
+Favorite Tool: Git
```

## مدل مقایسه در Git

```text
Last Commit
     |
     | git diff --staged
     v
Staging Area
     |
     | git diff
     v
Working Directory
```

پیکان‌ها مسیر مقایسه رو نشون می‌دن، نه جابه‌جایی فیزیکی فایل‌ها.

- `git diff`: مقایسه Working Directory با Staging Area
- `git diff --staged`: مقایسه Staging Area با آخرین Commit

### 🧠 سؤال مفهومی

چرا بعد از `git add`، خروجی `git diff` در تمرین ما خالیه؟

<details>
<summary>نمایش پاسخ</summary>

چون تمام تغییرات فایل Stage شدن و اختلاف جدیدی بین Working Directory و Staging Area وجود نداره.

برای مشاهده تغییر Staged از دستور زیر استفاده می‌کنیم:

```bash
git diff --staged
```

</details>

---

# ۶. Unstage کردن بدون حذف ویرایش‌ها

فرض کنیم اشتباهی فایل رو Stage کردیم.

می‌خوایم فایل از Staging Area خارج بشه، اما ویرایش‌هاش باقی بمونن.

## دستور git restore --staged

```bash
git restore --staged about-me.txt
```

حالا وضعیت رو بررسی کن:

```bash
git status
```

خروجی نمونه:

```text
Changes not staged for commit:
        modified:   about-me.txt
```

بعد:

```bash
git diff
```

دوباره خط اضافه‌شده رو مشاهده می‌کنیم:

```diff
+Favorite Tool: Git
```

پس:

> دستور `git restore --staged` تغییرات Working Directory رو حذف نمی‌کنه؛ فقط محتوای Staged فایل رو به حالت آخرین Commit برمی‌گردونه.

### ⚡ سؤال سریع

اگر بخوایم فایلی رو Unstage کنیم، بدون اینکه ویرایش‌هاش پاک بشن، چه دستوری اجرا می‌کنیم؟

<details>
<summary>نمایش پاسخ</summary>

```bash
git restore --staged about-me.txt
```

</details>

---

# ۷. کنار گذاشتن تغییر آزمایشی

گاهی تصمیم می‌گیریم یک تغییر آزمایشی رو اصلاً نگه نداریم.

**⚠️ هشدار مهم**

دستور بعدی تغییرات Unstaged فایل Track شده رو کنار می‌ذاره و ممکنه امکان بازیابی اون‌ها وجود نداشته باشه.

فقط روی فایل تمرینی و پس از بررسی تغییرات اجراش کنید.

در مثال ما فایل Unstage شده و Staging Area با آخرین Commit یکسانه.

حالا:

```bash
git restore about-me.txt
```

وضعیت رو بررسی کن:

```bash
git status
```

خروجی مورد انتظار:

```text
nothing to commit, working tree clean
```

برای بررسی محتوای فایل:

```powershell
Get-Content .\about-me.txt
```

خط زیر دیگه نباید وجود داشته باشه:

```text
Favorite Tool: Git
```

## تفاوت دو دستور Restore

| دستور | نتیجه |
|---|---|
| `git restore --staged about-me.txt` | Unstage می‌کنه و ویرایش‌های Working Directory رو نگه می‌داره |
| `git restore about-me.txt` | تغییرات Unstaged فایل رو کنار می‌ذاره |

**نکته علمی:** دستور `git restore` بدون `--staged` محتوای Working Directory رو از Staging Area بازسازی می‌کنه، نه لزوماً از آخرین Commit.

در تمرین ما چون Staging Area با آخرین Commit یکسانه، فایل به وضعیت آخرین Commit برمی‌گرده.

---

# ۸. تمرین عملی

این تمرین رو روی Repository خودت انجام بده.

### مرحله ۱: بررسی وضعیت

```bash
git status
```

### مرحله ۲: باز کردن فایل

```powershell
notepad .\about-me.txt
```

### مرحله ۳: اضافه کردن خط جدید

```text
Current Course: Git Basics
```

فایل رو ذخیره کن.

### مرحله ۴: مشاهده تغییر Unstaged

```bash
git status
git diff
```

### مرحله ۵: Stage کردن تغییر

```bash
git add about-me.txt
```

### مرحله ۶: مقایسه دو نوع Diff

```bash
git diff
git diff --staged
```

### مرحله ۷: Unstage کردن

```bash
git restore --staged about-me.txt
```

### مرحله ۸: بررسی باقی ماندن تغییر

```bash
git status
git diff
```

### مرحله ۹: کنار گذاشتن تغییر آزمایشی

فقط اگر مطمئنی به این تغییر نیازی نداری:

```bash
git restore about-me.txt
```

### مرحله ۱۰: بررسی نهایی

```bash
git status
git log --oneline
```

## مدل تمرین

```text
Modified
   |
   | git add
   v
Staged
   |
   | git restore --staged
   v
Modified
   |
   | git restore
   v
Unmodified
```

---

# ۹. Challenge — بدون نگاه به راهنما

این مراحل رو بدون کمک انجام بده:

1. یک فایل Track شده انتخاب کن.
2. یک خط جدید بهش اضافه کن.
3. تغییر Unstaged رو مشاهده کن.
4. فایل رو Stage کن.
5. تغییر Staged رو بررسی کن.
6. بدون حذف ویرایش‌ها، فایل رو Unstage کن.
7. وضعیت فایل رو بررسی کن.
8. فقط در صورت اطمینان، تغییر آزمایشی رو کنار بذار.
9. وضعیت نهایی و History رو نمایش بده.

<details>
<summary>پرسش‌های راهنما و پاسخ‌ها</summary>

**نمایش تغییر Unstaged:**

```bash
git diff
```

**نمایش تغییر Staged:**

```bash
git diff --staged
```

**Unstage بدون حذف ویرایش‌ها:**

```bash
git restore --staged about-me.txt
```

**کنار گذاشتن تغییر Unstaged:**

```bash
git restore about-me.txt
```

این دستور باید با احتیاط اجرا بشه.

**نمایش History:**

```bash
git log --oneline
```

</details>

---

# ۱۰. مشکلات رایج

## خطای not a git repository

```text
fatal: not a git repository
```

احتمالاً Terminal داخل Repository نیست.

مسیر رو بررسی کن:

```powershell
Get-Location
```

## دستور git diff خروجی نداره

ممکنه فایل ذخیره نشده باشه یا تغییر Stage شده باشه.

ابتدا:

```bash
git status
```

اگر تغییر Staged بود:

```bash
git diff --staged
```

## فایل پیدا نمی‌شه

نام فایل‌ها رو ببین:

```powershell
Get-ChildItem -Name
```

از نام واقعی فایل خودت استفاده کن.

## صفحه خروجی بسته نمی‌شه

اگر خروجی `git log` یا `git show` داخل Pager باز شد، کلید زیر رو فشار بده:

```text
q
```

---

# ۱۱. Cheat Sheet

| هدف | دستور |
|---|---|
| نمایش History | `git log` |
| نمایش خلاصه History | `git log --oneline` |
| بررسی آخرین Commit | `git show` |
| بررسی Commit مشخص | `git show <commit-hash>` |
| نمایش تغییرات Unstaged | `git diff` |
| نمایش تغییرات Staged | `git diff --staged` |
| Unstage کردن | `git restore --staged <file>` |
| کنار گذاشتن تغییرات Unstaged | `git restore <file>` ⚠️ |

---

# جمع‌بندی

در جلسه اول یاد گرفتیم تغییرات رو Commit کنیم.

در جلسه دوم یاد گرفتیم:

- History و جزئیات Commitها رو بررسی کنیم.
- تغییرات فایل‌ها رو با Diff مشاهده کنیم.
- تفاوت Staged و Unstaged رو تشخیص بدیم.
- یک تغییر رو بدون حذف ویرایش‌ها Unstage کنیم.
- تغییرات آزمایشی رو با احتیاط کنار بذاریم.

## جلسه بعد

**Branching & Merging**

در جلسه سوم یاد می‌گیریم چطور با Branchها روی تغییرات مختلف کار کنیم و اون‌ها رو با هم Merge کنیم.

---

# منابع

- [Pro Git Book](https://git-scm.com/book/en/v2)
- [Git — git-log](https://git-scm.com/docs/git-log)
- [Git — git-show](https://git-scm.com/docs/git-show)
- [Git — git-diff](https://git-scm.com/docs/git-diff)
- [Git — git-restore](https://git-scm.com/docs/git-restore)
