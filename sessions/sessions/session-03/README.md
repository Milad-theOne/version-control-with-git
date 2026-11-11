# راهنمای خصوصی مدرس — جلسه سوم Git

**Session 03 — Branching & Merging**

**مدت کلاس:** ۶۰ دقیقه  
**مخاطب:** دانشجویان مبتدی کامپیوتر  
**محیط:** Windows + PowerShell + Notepad  
**سناریو:** ادامه Repository جلسات اول و دوم  
**محل نگهداری:** Obsidian — یادداشت خصوصی مدرس

---

## ۰. هدف جلسه

در پایان این جلسه دانشجو باید بتواند:

1. توضیح دهد Branch چیست و چرا از آن استفاده می‌کنیم.
2. تفاوت Branch و Commit را بداند.
3. مفهوم اولیه HEAD را درک کند.
4. Branchهای موجود را مشاهده کند.
5. یک Branch جدید ایجاد کند.
6. بین Branchها جابه‌جا شود.
7. روی Branch جدید تغییر ایجاد کند و Commit بزند.
8. به Branch اصلی برگردد و تفاوت فایل‌ها را مشاهده کند.
9. با Merge تغییرات را به Branch اصلی منتقل کند.
10. History نهایی را بررسی کند.

**نکته مدرس:** در این جلسه فقط Fast-forward Merge را به‌صورت عملی آموزش می‌دهیم. Merge Conflict و روش حل آن در جلسه پنجم بررسی می‌شود.

---

# ۱. برنامه زمانی کلاس

| زمان | موضوع |
|---|---|
| دقیقه ۰ تا ۵ | آماده‌سازی سیستم |
| دقیقه ۵ تا ۱۲ | مرور جلسه دوم |
| دقیقه ۱۲ تا ۲۰ | مفهوم Branch و HEAD |
| دقیقه ۲۰ تا ۳۰ | ساخت Branch و جابه‌جایی |
| دقیقه ۳۰ تا ۴۱ | ویرایش فایل و Commit |
| دقیقه ۴۱ تا ۵۱ | برگشت به main و Merge |
| دقیقه ۵۱ تا ۵۷ | تمرین و بررسی History |
| دقیقه ۵۷ تا ۶۰ | جمع‌بندی |

---

# ۲. آماده‌سازی سیستم — دقیقه ۰ تا ۵

## قدم اول: باز کردن Repository

به دانشجوها بگو:

«اول وارد همون پروژه‌ای می‌شیم که در دو جلسه قبل ساختیم. امروز پروژه جدیدی ایجاد نمی‌کنیم.»

در Windows:

1. برنامه File Explorer را باز کنید.
2. وارد پوشه `Git-Class` شوید.
3. پوشه `git-first-project` را باز کنید.
4. روی نوار آدرس File Explorer کلیک کنید.
5. عبارت `powershell` را بنویسید.
6. Enter بزنید.

اکنون PowerShell باید در مسیر Repository باز شده باشد.

### دستور اول

```powershell
Get-Location
```

**هدف:** بررسی مسیر فعلی.

### دستور دوم

```powershell
git --version
```

**هدف:** اطمینان از نصب Git.

### دستور سوم

```powershell
git status
```

خروجی نمونه:

```text
On branch main
nothing to commit, working tree clean
```

**توضیح مدرس:**

«قبل از انجام هر کاری، وضعیت Repository رو بررسی می‌کنیم. می‌خوایم مطمئن بشیم تغییرات ثبت‌نشده‌ای نداریم که موقع جابه‌جایی بین Branchها مشکل ایجاد کنن.»

اگر فایل تغییرکرده‌ای وجود داشت، بدون بررسی آن را حذف نکن.

### دستور چهارم

```powershell
Get-ChildItem -Name
```

باید فایل تمرینی را ببینیم:

```text
about-me.txt
```

### دستور پنجم

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

محتوای واقعی دانشجو ممکن است متفاوت باشد.

---

# ۳. مرور جلسه دوم — دقیقه ۵ تا ۱۲

## چه چیزی بگویم؟

«در جلسه قبل یاد گرفتیم چطور History پروژه رو ببینیم، تغییرات فایل رو بررسی کنیم و تغییرات اشتباهی رو مدیریت کنیم.»

دستورات مروری:

```powershell
git log --oneline
```

```powershell
git diff
```

```powershell
git diff --staged
```

```powershell
git status
```

از دانشجوها بپرس:

**سؤال اول:** Commit چیست؟

پاسخ مورد انتظار:

«Commit یک Snapshot ثبت‌شده از وضعیت پروژه است.»

**سؤال دوم:** آیا Git فقط آخرین نسخه فایل‌ها را نگه می‌دارد؟

پاسخ:

«خیر، Git تاریخچه Commitها را نگه می‌دارد و امکان بررسی نسخه‌های قبلی را فراهم می‌کند.»

## ورود به موضوع جدید

بگو:

«فرض کنید روی یک پروژه دانشگاهی کار می‌کنیم. پروژه فعلاً سالمه، ولی می‌خوایم یک قابلیت جدید بهش اضافه کنیم.»

«اگر قابلیت جدید هنوز کامل نشده باشه، بهتره مستقیم روی نسخه اصلی پروژه کار کنیم یا یک مسیر جدا برای توسعه داشته باشیم؟»

بعد توضیح بده که Git برای این مسئله Branch دارد.

---

# ۴. مفهوم Branch — دقیقه ۱۲ تا ۲۰

## Branch چیست؟

تعریف علمی:

**Branch در Git یک اشاره‌گر قابل‌حرکت به یک Commit است.**

تعریف ساده برای کلاس:

«Branch به ما اجازه می‌ده روی یک مسیر توسعه جداگانه کار کنیم، بدون اینکه مجبور باشیم تغییرات جدید رو مستقیم روی Branch اصلی ثبت کنیم.»

## مثال روی تخته

فرض کنیم پروژه سه Commit دارد:

```text
C1 --- C2 --- C3
               |
              main
```

اکنون یک Branch جدید ایجاد می‌کنیم:

```text
C1 --- C2 --- C3
               | \
               |  feature-profile
              main
```

**توضیح مهم:** در لحظه ساخت Branch، هر دو اشاره‌گر به یک Commit اشاره می‌کنند. هنوز Commit جدیدی ساخته نشده است.

حالا روی Branch جدید یک Commit ایجاد می‌کنیم:

```text
C1 --- C2 --- C3 --- F1
               |      |
              main  feature-profile
```

اینجا `main` همچنان به C3 اشاره می‌کند، ولی `feature-profile` به F1 منتقل شده است.

## تفاوت Branch و Commit

| مفهوم | تعریف |
|---|---|
| Commit | Snapshot ثبت‌شده از پروژه |
| Branch | اشاره‌گر قابل‌حرکت به Commit |
| main | نام رایج Branch اصلی |
| HEAD | نشان‌دهنده موقعیت فعلی در Git |

## HEAD چیست؟

به دانشجوها بگو:

«HEAD به Git می‌گه الان روی کدوم موقعیت از History قرار داریم. در حالت معمول HEAD به Branch فعلی اشاره می‌کنه.»

مثال:

```text
HEAD
 |
 v
main
 |
 v
 C3
```

اگر به Branch جدید برویم:

```text
HEAD
 |
 v
feature-profile
 |
 v
 C3
```

فعلاً وارد Detached HEAD نشو.

---

# ۵. مشاهده Branchها — دقیقه ۲۰ تا ۲۳

## دستور اول

```powershell
git branch
```

خروجی نمونه:

```text
* main
```

توضیح بده:

«علامت ستاره نشون می‌ده الان روی کدوم Branch هستیم.»

ممکن است نام Branch اصلی `master` باشد.

**نکته مدرس:** اگر خروجی دانشجو `master` بود، در مراحل برگشت و Merge از همان نام استفاده کند.

---

# ۶. ساخت Branch جدید — دقیقه ۲۳ تا ۲۷

## دستور دوم

```powershell
git branch feature-profile
```

بگو:

«با این دستور یک Branch به نام feature-profile می‌سازیم.»

حالا:

```powershell
git branch
```

خروجی نمونه:

```text
  feature-profile
* main
```

## نکته مهم

از دانشجوها بپرس:

«آیا الان روی Branch جدید هستیم؟»

پاسخ: خیر.

چون علامت `*` هنوز کنار `main` است.

**نکته‌ای که باید تأکید کنی:**

دستور `git branch` در این حالت فقط Branch را می‌سازد و ما را به آن منتقل نمی‌کند.

---

# ۷. جابه‌جایی بین Branchها — دقیقه ۲۷ تا ۳۰

## دستور سوم

```powershell
git switch feature-profile
```

خروجی نمونه:

```text
Switched to branch 'feature-profile'
```

حالا:

```powershell
git branch
```

خروجی:

```text
* feature-profile
  main
```

توضیح بده:

«الان HEAD به feature-profile اشاره می‌کنه. از این به بعد Commitهایی که ایجاد می‌کنیم روی همین Branch ثبت می‌شن.»

## یک نکته تکمیلی

برای ساخت و جابه‌جایی هم‌زمان می‌توانیم از دستور زیر استفاده کنیم:

```powershell
git switch -c new-feature
```

اما **این دستور را فعلاً اجرا نکنید**؛ چون سناریوی کلاس را با Branch دیگری پیچیده می‌کند.

فقط توضیح بده که چنین امکانی وجود دارد.

---

# ۸. ایجاد تغییر روی Branch جدید — دقیقه ۳۰ تا ۳۵

قبل از ویرایش:

```powershell
git status
```

باید Branch فعلی `feature-profile` باشد.

## باز کردن فایل

```powershell
notepad .\about-me.txt
```

از دانشجوها بخواه در انتهای فایل این خط را اضافه کنند:

```text
Git Skill: Branching
```

با `Ctrl + S` ذخیره کنند.

بعد به PowerShell برگردند.

## بررسی وضعیت

```powershell
git status
```

خروجی نمونه:

```text
On branch feature-profile

Changes not staged for commit:
        modified:   about-me.txt
```

## بررسی تغییر

```powershell
git diff
```

باید خط جدید دیده شود:

```diff
+Git Skill: Branching
```

**توضیح مدرس:**

«این تغییر فعلاً فقط در Working Directory ماست. هنوز Commit نشده.»

---

# ۹. ثبت Commit روی Branch جدید — دقیقه ۳۵ تا ۴۱

## Stage کردن

```powershell
git add about-me.txt
```

بررسی:

```powershell
git status
```

اکنون فایل باید در بخش `Changes to be committed` باشد.

## مشاهده تغییر Staged

```powershell
git diff --staged
```

## ایجاد Commit

```powershell
git commit -m "Add branching skill"
```

خروجی نمونه:

```text
[feature-profile abc1234] Add branching skill
 1 file changed, 1 insertion(+)
```

شناسه Commit در هر سیستم متفاوت است.

## بررسی History

```powershell
git log --oneline
```

در بالای History باید Commit جدید را ببینیم.

## بررسی وضعیت

```powershell
git status
```

اگر همه چیز درست باشد:

```text
On branch feature-profile
nothing to commit, working tree clean
```

### نکته مدرس

به دانشجوها بگو:

«الان یک Commit جدید روی feature-profile داریم. اما Branch اصلی هنوز به Commit قبلی اشاره می‌کنه.»

---

# ۱۰. برگشت به Branch اصلی — دقیقه ۴۱ تا ۴۵

این بخش یکی از مهم‌ترین قسمت‌های کلاس است.

## قبل از جابه‌جایی

محتوای فایل را نشان بده:

```powershell
Get-Content .\about-me.txt
```

باید این خط وجود داشته باشد:

```text
Git Skill: Branching
```

## برگشت به main

```powershell
git switch main
```

اگر Branch اصلی `master` است:

```powershell
git switch master
```

فقط یکی از این دو دستور را متناسب با نام واقعی Branch اجرا کنید.

## بررسی Branch فعلی

```powershell
git branch
```

## بررسی فایل

```powershell
Get-Content .\about-me.txt
```

در سناریوی ما، خط زیر دیگر نباید وجود داشته باشد:

```text
Git Skill: Branching
```

## اینجا چه بگویم؟

«دقت کنید! ما فایل رو دستی تغییر ندادیم. فقط Branch رو عوض کردیم و Git محتوای Working Directory رو مطابق Commit مربوط به Branch جدید تنظیم کرد.»

از دانشجوها بپرس:

«آیا تغییر قبلی پاک شده؟»

پاسخ:

«خیر. تغییر در Commit مربوط به feature-profile ثبت شده و هنوز در History وجود داره.»

## بررسی History

```powershell
git log --oneline
```

در `main`، Commit جدید feature-profile در History فعلی دیده نمی‌شود.

اما با دستور زیر می‌توانیم Commitهای همه Branchهای محلی را مشاهده کنیم:

```powershell
git log --oneline --graph --all --decorate
```

---

# ۱۱. مفهوم Merge — دقیقه ۴۵ تا ۴۷

## Merge چیست؟

تعریف ساده:

«Merge عملیاتی است که تغییرات یک مسیر توسعه را با مسیر دیگر ترکیب می‌کند.»

در سناریوی ما می‌خواهیم Commit مربوط به `feature-profile` را وارد `main` کنیم.

قبل از Merge:

```text
C1 --- C2 --- C3 --- F1
               |      |
              main  feature-profile
```

چون `main` از زمان ساخت Branch جدید جلو نرفته، Git می‌تواند اشاره‌گر `main` را مستقیماً به F1 منتقل کند.

بعد از Fast-forward Merge:

```text
C1 --- C2 --- C3 --- F1
                      |
             main, feature-profile
```

**نکته علمی:** در Fast-forward Merge، Commit جدیدی مخصوص Merge ساخته نمی‌شود.

---

# ۱۲. انجام Merge — دقیقه ۴۷ تا ۵۱

## بررسی وضعیت

ابتدا:

```powershell
git status
```

باید روی Branch اصلی باشیم و Working Directory تمیز باشد.

## دستور Merge

```powershell
git merge feature-profile
```

خروجی نمونه:

```text
Updating abc1234..def5678
Fast-forward
 about-me.txt | 1 +
 1 file changed, 1 insertion(+)
```

شناسه‌ها نمونه هستند.

## بررسی فایل

```powershell
Get-Content .\about-me.txt
```

حالا خط زیر باید دوباره وجود داشته باشد:

```text
Git Skill: Branching
```

## بررسی History

```powershell
git log --oneline --graph --all --decorate
```

خروجی نمونه:

```text
* def5678 (HEAD -> main, feature-profile) Add branching skill
* abc1234 Add learning goal
* 123abcd Add my profile
```

## چه چیزی بگویم؟

«الان هر دو Branch به یک Commit اشاره می‌کنن. Merge موفق بود و تغییرات feature-profile وارد main شدن.»

تأکید کن که خود Branch با Merge حذف نمی‌شود.

---

# ۱۳. حذف Branch بعد از Merge — بخش اختیاری

اگر زمان کلاس کافی بود، می‌توانیم Branch ادغام‌شده را حذف کنیم.

ابتدا مطمئن شو روی `main` هستیم:

```powershell
git branch
```

سپس:

```powershell
git branch -d feature-profile
```

خروجی نمونه:

```text
Deleted branch feature-profile
```

**توضیح مهم:**

«حذف Branch در این وضعیت به معنی حذف Commitهای ادغام‌شده نیست. چون Commit جدید اکنون از طریق main قابل دسترسه.»

اگر دانشجو هنوز مفهوم Merge را خوب درک نکرده، این مرحله را به پایان کلاس موکول کن.

---

# ۱۴. تمرین دانشجویان — دقیقه ۵۱ تا ۵۷

از دانشجوها بخواه بدون نگاه کردن به مراحل قبلی، کارهای زیر را انجام دهند:

1. Branch فعلی را بررسی کنند.
2. یک Branch جدید به نام `feature-hobby` بسازند.
3. به آن جابه‌جا شوند.
4. یک خط جدید به `about-me.txt` اضافه کنند.
5. تغییر را Commit کنند.
6. به Branch اصلی برگردند.
7. نبودن تغییر جدید در فایل Branch اصلی را بررسی کنند.
8. Branch جدید را Merge کنند.
9. History نهایی را نمایش دهند.

## راهنمای دستورات برای مدرس

```powershell
git status
git branch feature-hobby
git switch feature-hobby
notepad .\about-me.txt
```

خط پیشنهادی:

```text
Hobby: Programming
```

پس از ذخیره:

```powershell
git diff
git add about-me.txt
git commit -m "Add hobby information"
git switch main
Get-Content .\about-me.txt
git merge feature-hobby
git log --oneline --graph --all --decorate
```

اگر Branch اصلی `master` است، دستور برگشت را متناسب با آن تغییر بده.

---

# ۱۵. مشکلات رایج و روش رفع آن‌ها

## مشکل اول: Not a Git Repository

خطا:

```text
fatal: not a git repository
```

علت احتمالی:

دانشجو در پوشه اشتباه قرار دارد.

راهکار:

```powershell
Get-Location
```

سپس وارد Repository صحیح شود.

## مشکل دوم: Branch از قبل وجود دارد

خطا:

```text
fatal: a branch named 'feature-profile' already exists
```

راهکار:

```powershell
git branch
```

اگر Branch وجود دارد، به‌جای ساخت دوباره، به آن جابه‌جا شو:

```powershell
git switch feature-profile
```

## مشکل سوم: Branch موردنظر پیدا نمی‌شود

خطا:

```text
fatal: invalid reference: feature-profile
```

راهکار:

```powershell
git branch
```

نام Branch را دقیق بررسی کن.

## مشکل چهارم: Git اجازه Switch نمی‌دهد

ممکن است خطایی درباره تغییرات محلی نمایش داده شود.

ابتدا:

```powershell
git status
```

سپس:

```powershell
git diff
```

**نکته مدرس:** بدون بررسی، تغییرات دانشجو را حذف نکن.

اگر تغییرات مهم هستند، باید درباره Commit کردن یا نگهداری آن‌ها تصمیم بگیریم.

## مشکل پنجم: Nothing to Commit

خروجی:

```text
nothing to commit, working tree clean
```

اگر انتظار Commit جدید داریم:

1. بررسی کن فایل واقعاً ویرایش شده باشد.
2. مطمئن شو با `Ctrl + S` ذخیره شده.
3. دستور `git status` را اجرا کن.
4. محتوای فایل را بررسی کن.

```powershell
Get-Content .\about-me.txt
```

## مشکل ششم: Git می‌گوید Already up to date

خروجی:

```text
Already up to date.
```

این پیام لزوماً خطا نیست.

ممکن است تغییرات Branch قبلاً Merge شده باشند یا Branch موردنظر Commit جدیدی برای وارد کردن نداشته باشد.

بررسی:

```powershell
git log --oneline --graph --all --decorate
```

## مشکل هفتم: Merge به‌جای Fast-forward مسیر دیگری دارد

اگر دانشجو روی Branch اصلی هم Commit جدید ساخته باشد، ممکن است وضعیت History با سناریوی کلاس متفاوت شود.

در این حالت بدون بررسی History، دستورهای جدید اجرا نکن.

ابتدا:

```powershell
git status
git log --oneline --graph --all --decorate
```

اگر Merge Conflict رخ داد، وضعیت را بررسی کن. در صورت مناسب بودن شرایط و برای لغو Merge در حال انجام:

```powershell
git merge --abort
```

سپس مسئله را جداگانه بررسی کن.

---

# ۱۶. سؤال‌های مفهومی پایان کلاس

## سؤال ۱

آیا ساخت Branch جدید باعث ایجاد Commit جدید می‌شود؟

**پاسخ:** خیر. Branch جدید ابتدا به Commit موجود اشاره می‌کند.

## سؤال ۲

آیا دستور `git branch feature-profile` ما را به Branch جدید منتقل می‌کند؟

**پاسخ:** خیر. فقط Branch را می‌سازد.

## سؤال ۳

برای جابه‌جایی بین Branchها از چه دستوری استفاده می‌کنیم؟

**پاسخ:**

```powershell
git switch feature-profile
```

## سؤال ۴

اگر روی Branch جدید Commit بزنیم، آیا اشاره‌گر main هم جلو می‌رود؟

**پاسخ:** خیر. در سناریوی معمول، فقط اشاره‌گر Branch فعلی جلو می‌رود.

## سؤال ۵

آیا Merge همیشه Commit جدید ایجاد می‌کند؟

**پاسخ:** خیر. در Fast-forward Merge معمولاً فقط اشاره‌گر Branch مقصد جلو می‌رود.

## سؤال ۶

آیا Merge کردن، Branch مبدأ را حذف می‌کند؟

**پاسخ:** خیر. حذف Branch یک عملیات جداگانه است.

---

# ۱۷. Cheat Sheet مخصوص مدرس

| هدف | دستور |
|---|---|
| بررسی وضعیت | `git status` |
| مشاهده Branchها | `git branch` |
| ساخت Branch | `git branch feature-profile` |
| جابه‌جایی | `git switch feature-profile` |
| ساخت و جابه‌جایی هم‌زمان | `git switch -c new-feature` |
| نمایش تغییرات | `git diff` |
| Stage کردن | `git add about-me.txt` |
| ایجاد Commit | `git commit -m "Add branching skill"` |
| برگشت به Branch اصلی | `git switch main` |
| Merge کردن | `git merge feature-profile` |
| مشاهده گراف History | `git log --oneline --graph --all --decorate` |
| حذف Branch ادغام‌شده | `git branch -d feature-profile` |

---

# ۱۸. جمع‌بندی نهایی — دقیقه ۵۷ تا ۶۰

## متن پیشنهادی برای پایان کلاس

«امروز یاد گرفتیم Git فقط برای ذخیره نسخه‌های قبلی نیست. ما می‌تونیم با Branchها مسیرهای توسعه جداگانه داشته باشیم.»

«یاد گرفتیم Branch جدید بسازیم، بین Branchها جابه‌جا بشیم، روی یک Branch تغییر ثبت کنیم و در نهایت با Merge تغییرات رو وارد Branch اصلی کنیم.»

«در پروژه‌های واقعی، این قابلیت کمک می‌کنه چند نفر یا حتی یک نفر روی قابلیت‌های مختلف کار کنن، بدون اینکه مجبور باشن تمام تغییرات رو مستقیم روی Branch اصلی ثبت کنن.»

## مهم‌ترین مفاهیم جلسه

- Branch
- Commit
- HEAD
- git branch
- git switch
- git merge
- Fast-forward Merge

## جلسه بعد

**Session 04 — GitHub & Remote Repository**

در جلسه چهارم یاد می‌گیریم:

- Remote Repository چیست؟
- تفاوت Local Repository و Remote Repository چیست؟
- چطور پروژه را به GitHub متصل کنیم؟
- چطور تغییرات را Push کنیم؟
- چطور Repository را Clone کنیم؟
- تفاوت Push، Pull و Fetch چیست؟

---

# ۱۹. چک‌لیست مدرس قبل از کلاس

- [ ] Git روی لپ‌تاپ نصب باشد.
- [ ] Repository جلسات قبلی وجود داشته باشد.
- [ ] فایل `about-me.txt` موجود باشد.
- [ ] وضعیت Repository تمیز باشد.
- [ ] نام Branch اصلی مشخص باشد.
- [ ] Branch تمرینی `feature-profile` از قبل وجود نداشته باشد.
- [ ] سناریوی Commit و Merge یک بار آزمایش شده باشد.
- [ ] خروجی‌های نمونه برای نمایش آماده باشند.
- [ ] برای دانشجوهایی که جلسه قبل غایب بودند، یک Repository تمرینی آماده باشد.

**نکته نهایی:** هدف اصلی جلسه سوم این نیست که دانشجو تعداد زیادی دستور حفظ کند. هدف این است که بفهمد Branch چگونه به او اجازه می‌دهد روی مسیر مستقلی کار کند و بعد تغییرات آن را وارد Branch اصلی کند.
