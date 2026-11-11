
# جلسه ۳ — کار با Branch و Merge

**Git Branching & Merging | Session 03**

در جلسه اول با Repository و Commit آشنا شدیم و در جلسه دوم History، Diff و Undo رو تمرین کردیم.

حالا می‌خوایم بدون تغییر مستقیم Branch اصلی، روی یک مسیر جداگانه کار کنیم و بعد تغییرات رو به Branch اصلی برگردونیم.

---

## اهداف یادگیری

در پایان جلسه می‌تونیم:

- توضیح بدیم Branch چیه و چه کاربردی داره.
- تفاوت Branch، Commit و HEAD رو تشخیص بدیم.
- با `git branch`، Branchها رو ببینیم و Branch جدید بسازیم.
- با `git switch` بین Branchها جابه‌جا بشیم.
- روی Branch جدید تغییر ایجاد کنیم و Commit بزنیم.
- با `git merge` یک Fast-forward Merge انجام بدیم.
- نتیجه رو با `git log --oneline --graph --all --decorate` بررسی کنیم.

---

# ۱. آماده‌سازی Repository

در Windows وارد پوشه پروژه جلسه قبل شو:

```text
Desktop/
└── Git-Class/
    └── git-first-project/
        └── about-me.txt
```

در نوار آدرس File Explorer بنویس `powershell` و Enter بزن.

ابتدا مسیر، فایل‌ها و وضعیت Git رو بررسی کن:

```powershell
Get-Location
git --version
Get-ChildItem -Name
git status
```

اگر Repository آماده و بدون تغییر ثبت‌نشده باشه، خروجی `git status` شبیه اینه:

```text
On branch main
nothing to commit, working tree clean
```

ممکنه Branch اصلی سیستم تو `master` باشه. در این راهنما از `main` استفاده می‌کنیم؛ اگر نام Branch اصلی تو فرق داره، از نام واقعی اون استفاده کن.

> ⚠️ اگر تغییرات ثبت‌نشده مهمی داری، قبل از ادامه بررسی‌شون کن. هیچ تغییری رو بدون اطمینان حذف نکن.

فایل تمرینی رو مشاهده کن:

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

---

# ۲. Branch چیست؟

فرض کن پروژه سه Commit داره:

```text
C1 --- C2 --- C3
               |
              main
```

می‌خوایم قابلیت جدیدی رو آزمایش کنیم، اما نمی‌خوایم Commitهای آزمایشی رو مستقیم روی `main` ثبت کنیم.

**Branch در Git یک اشاره‌گر قابل‌حرکت به Commit است.** با Branch می‌تونیم یک مسیر توسعه جداگانه داشته باشیم.

وقتی Branch جدید رو می‌سازیم، هنوز Commit جدیدی ایجاد نشده و هر دو Branch به یک Commit اشاره می‌کنن:

```text
                 main
                  |
C1 --- C2 --- C3
                  |
             feature-profile
```

بعد از ایجاد یک Commit روی Branch جدید:

```text
C1 --- C2 --- C3 --- F1
               |      |
              main  feature-profile
```

**نکته:** Branch کپی مستقل از کل پوشه پروژه نیست؛ یک اشاره‌گر در History گیت است.

## تفاوت مفاهیم

| مفهوم | معنی |
|---|---|
| Commit | یک Snapshot ثبت‌شده از پروژه |
| Branch | اشاره‌گر قابل‌حرکت به Commit |
| main | نام رایج Branch اصلی |
| HEAD | نشان‌دهنده موقعیت فعلی Git؛ معمولاً به Branch فعلی اشاره می‌کند |

---

# ۳. مشاهده Branchها

```powershell
git branch
```

خروجی نمونه:

```text
* main
```

علامت `*` یعنی الان روی این Branch هستیم.

---

# ۴. ساخت Branch جدید

```powershell
git branch feature-profile
```

دوباره Branchها رو ببین:

```powershell
git branch
```

خروجی نمونه:

```text
  feature-profile
* main
```

**دقت کن:** ساخت Branch جدید باعث جابه‌جایی خودکار به اون نمی‌شه.

### ⚡ سؤال سریع

آیا دستور `git branch feature-profile` یک Commit جدید هم ایجاد می‌کنه؟

<details>
<summary>نمایش پاسخ</summary>

خیر. این دستور فقط یک Branch جدید ایجاد می‌کنه که ابتدا به همون Commit فعلی اشاره داره.

</details>

---

# ۵. جابه‌جایی بین Branchها

```powershell
git switch feature-profile
```

خروجی نمونه:

```text
Switched to branch 'feature-profile'
```

برای بررسی:

```powershell
git branch
```

خروجی:

```text
* feature-profile
  main
```

حالا `HEAD` در حالت معمول به `feature-profile` اشاره می‌کنه.

> روش کوتاه‌تر برای **ساخت و جابه‌جایی هم‌زمان**: `git switch -c new-feature`. این دستور رو فعلاً اجرا نکن؛ چون برای تمرین از `feature-profile` استفاده می‌کنیم.

### 🧠 سؤال مفهومی

فرق این دو دستور چیه؟

```powershell
git branch feature-profile
git switch feature-profile
```

<details>
<summary>نمایش پاسخ</summary>

دستور اول Branch رو می‌سازه و دستور دوم به Branch موردنظر جابه‌جا می‌شه.

</details>

---

# ۶. ویرایش فایل روی Branch جدید

فایل رو باز کن:

```powershell
notepad .\about-me.txt
```

در انتهای فایل این خط رو اضافه کن:

```text
Git Skill: Branching
```

با `Ctrl + S` ذخیره کن.

بررسی وضعیت:

```powershell
git status
```

باید فایل `about-me.txt` به‌صورت `modified` در بخش `Changes not staged for commit` دیده بشه.

تغییر رو مشاهده کن:

```powershell
git diff
```

بخشی از خروجی:

```diff
+Git Skill: Branching
```

---

# ۷. ثبت Commit روی Branch جدید

فایل رو Stage کن:

```powershell
git add about-me.txt
```

تغییر Staged رو بررسی کن:

```powershell
git diff --staged
```

حالا Commit بساز:

```powershell
git commit -m "Add branching skill"
```

خروجی نمونه:

```text
[feature-profile abc1234] Add branching skill
 1 file changed, 1 insertion(+)
```

شناسه Commit در سیستم هر نفر متفاوته.

History و وضعیت رو بررسی کن:

```powershell
git log --oneline
git status
```

الان Commit جدید روی `feature-profile` ثبت شده؛ اشاره‌گر `main` هنوز روی Commit قبلیه.

---

# ۸. برگشت به Branch اصلی

قبل از جابه‌جایی، محتوای فایل رو ببین:

```powershell
Get-Content .\about-me.txt
```

باید `Git Skill: Branching` وجود داشته باشه.

حالا به Branch اصلی برگرد:

```powershell
git switch main
```

اگر Branch اصلی تو `master` است، به‌جاش `git switch master` اجرا کن.

دوباره فایل رو بررسی کن:

```powershell
Get-Content .\about-me.txt
```

در سناریوی تمرین، خط `Git Skill: Branching` دیگه داخل فایل Branch اصلی نیست.

**آیا تغییر حذف شده؟ خیر!** این تغییر در Commit مربوط به `feature-profile` ذخیره شده.

برای دیدن History همه Branchهای محلی:

```powershell
git log --oneline --graph --all --decorate
```

---

# ۹. Merge چیست؟

**Merge** یعنی ادغام مسیر توسعه یک Branch در Branch فعلی.

ما می‌خوایم تغییر `feature-profile` رو وارد `main` کنیم.

قبل از Merge:

```text
C1 --- C2 --- C3 --- F1
               |      |
              main  feature-profile
```

چون `main` از زمان جدا شدن Branch جدید جلو نرفته، Git می‌تونه **Fast-forward Merge** انجام بده.

بعد از Merge:

```text
C1 --- C2 --- C3 --- F1
                      |
             main, feature-profile
```

در Fast-forward Merge، Commit جدید مخصوص Merge ساخته نمی‌شه؛ اشاره‌گر Branch مقصد جلو می‌ره.

---

# ۱۰. انجام Merge

ابتدا مطمئن شو روی `main` هستی:

```powershell
git status
git branch
```

سپس:

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

حالا فایل رو ببین:

```powershell
Get-Content .\about-me.txt
```

خط زیر دوباره وجود داره:

```text
Git Skill: Branching
```

و History رو بررسی کن:

```powershell
git log --oneline --graph --all --decorate
```

خروجی نمونه:

```text
* def5678 (HEAD -> main, feature-profile) Add branching skill
* abc1234 Add learning goal
* 123abcd Add my profile
```

**نکته:** Merge کردن، Branch مبدأ رو حذف نمی‌کنه.

---

# ۱۱. حذف Branch ادغام‌شده (اختیاری)

اگر Merge موفق بوده و روی `main` هستی:

```powershell
git branch -d feature-profile
```

این دستور Branch محلی ادغام‌شده رو حذف می‌کنه، نه Commitهایی که از طریق `main` قابل دسترس هستن.

> این مرحله اختیاریه. اگر می‌خوای Branch رو برای تمرین‌های بعدی نگه داری، اجراش نکن.

---

# ۱۲. تمرین عملی

حالا خودت همین Workflow رو با یک Branch جدید انجام بده:

1. وضعیت Repository رو بررسی کن.
2. Branch جدید `feature-hobby` بساز.
3. به Branch جدید برو.
4. فایل `about-me.txt` رو باز کن.
5. خط `Hobby: Programming` رو اضافه و ذخیره کن.
6. تغییر رو بررسی کن و Commit بزن.
7. به Branch اصلی برگرد و محتوای فایل رو بررسی کن.
8. Branch جدید رو Merge کن.
9. History نهایی رو نمایش بده.

دستورهای موردنیاز:

```powershell
git status
git branch feature-hobby
git switch feature-hobby
notepad .\about-me.txt
```

بعد از ذخیره خط جدید:

```powershell
git diff
git add about-me.txt
git commit -m "Add hobby information"
git switch main
Get-Content .\about-me.txt
git merge feature-hobby
git log --oneline --graph --all --decorate
```

اگر Branch اصلی `master` است، در دستور برگشت نام اون رو جایگزین کن.

---

# ۱۳. Challenge — بدون نگاه به راهنما

- یک Branch جدید با نام دلخواه بساز.
- به اون جابه‌جا شو.
- یک فایل Track شده رو ویرایش کن.
- تغییر رو Commit کن.
- به Branch اصلی برگرد.
- بررسی کن تغییر جدید هنوز در Branch اصلی وجود نداره.
- Branch جدید رو Merge کن.
- History رو با نمودار نمایش بده.

<details>
<summary>نمایش راهنمای پاسخ</summary>

```powershell
git branch my-feature
git switch my-feature
notepad .\about-me.txt
git add about-me.txt
git commit -m "Update profile"
git switch main
git merge my-feature
git log --oneline --graph --all --decorate
```

قبل از `git add`، فایل رو ویرایش و ذخیره کن. اگر Branch اصلی `master` است، از نام واقعی اون استفاده کن.

</details>

---

# ۱۴. مشکلات رایج

### fatal: not a git repository

احتمالاً در پوشه Repository نیستی:

```powershell
Get-Location
```

### a branch named 'feature-profile' already exists

این Branch قبلاً ساخته شده. ابتدا بررسی کن:

```powershell
git branch
```

اگر می‌خوای وارد همون Branch بشی:

```powershell
git switch feature-profile
```

### invalid reference: feature-profile

نام Branch رو بررسی کن:

```powershell
git branch
```

### موقع Switch خطای تغییرات محلی می‌گیرم

ابتدا:

```powershell
git status
git diff
```

بدون بررسی، تغییرات رو حذف نکن. ممکنه لازم باشه تغییرات مهم رو ابتدا Commit کنی.

### nothing to commit

مطمئن شو فایل ویرایش و ذخیره شده:

```powershell
Get-Content .\about-me.txt
git status
```

### Already up to date

این پیام لزوماً خطا نیست؛ ممکنه تغییرات Branch قبلاً ادغام شده باشن یا Commit جدیدی برای Merge وجود نداشته باشه.

```powershell
git log --oneline --graph --all --decorate
```

### Merge Conflict

در این جلسه سناریو طوری طراحی شده که Fast-forward Merge داشته باشیم. اگر Conflict رخ داد، قبل از اجرای دستورهای بیشتر، وضعیت و History رو بررسی کن:

```powershell
git status
git log --oneline --graph --all --decorate
```

حل Conflict رو در جلسه پنجم یاد می‌گیریم.

---

# ۱۵. Cheat Sheet

| هدف | دستور |
|---|---|
| مشاهده Branchها | `git branch` |
| ساخت Branch | `git branch feature-profile` |
| جابه‌جایی | `git switch feature-profile` |
| ساخت و جابه‌جایی هم‌زمان | `git switch -c new-feature` |
| بررسی تغییرات | `git diff` |
| Stage کردن | `git add about-me.txt` |
| ثبت Commit | `git commit -m "Add branching skill"` |
| برگشت به Branch اصلی | `git switch main` |
| Merge | `git merge feature-profile` |
| مشاهده نمودار History | `git log --oneline --graph --all --decorate` |
| حذف Branch ادغام‌شده | `git branch -d feature-profile` |

---

# جمع‌بندی

در این جلسه یاد گرفتیم:

- Branch مسیر جداگانه‌ای برای توسعه فراهم می‌کنه.
- ساخت Branch با جابه‌جایی به اون فرق داره.
- Commit جدید روی Branch فعلی ثبت می‌شه.
- با جابه‌جایی بین Branchها، فایل‌های Working Directory ممکنه تغییر کنن.
- Merge تغییرات یک Branch رو وارد Branch فعلی می‌کنه.
- در Fast-forward Merge، Merge Commit جدید ساخته نمی‌شه.

## جلسه بعد

**Session 04 — GitHub & Remote Repository**

در جلسه چهارم با Remote Repository، Clone، Push، Pull و Fetch آشنا می‌شیم.

---

# منابع

- [Pro Git — Git Branching](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
- [Git — git-branch](https://git-scm.com/docs/git-branch)
- [Git — git-switch](https://git-scm.com/docs/git-switch)
- [Git — git-merge](https://git-scm.com/docs/git-merge)
- [Git — git-log](https://git-scm.com/docs/git-log)
