جلسه ۲ — تاریخچه، مقایسه و مدیریت تغییرات
Git History, Diff & Basic Undo
در جلسه اول یاد گرفتیم چطور یک Repository بسازیم، فایل‌ها رو Stage کنیم و Commit ایجاد کنیم. امروز می‌خوایم Commitهای قبلی رو ببینیم، تغییرات رو قبل از Commit مقایسه کنیم و اشتباهات ساده رو اصلاح کنیم.
اهداف یادگیری
- مشاهده History با git log و git log --oneline
- بررسی جزئیات یک Commit با git show
- مقایسه تغییرات Unstaged با git diff
- مقایسه تغییرات Staged با git diff --staged
- خارج کردن تغییرات از Staging Area با git restore --staged
- کنار گذاشتن تغییرات آزمایشی با git restore و درک خطر آن
۱. شروع از Repository جلسه قبل
در Windows، File Explorer رو باز کن و وارد پوشه Repository جلسه قبل شو؛ مثلاً:
Desktop/Git-Class/git-first-project/
داخل نوار آدرس File Explorer بنویس powershell و Enter بزن. حالا Terminal داخل همان پوشه باز می‌شه.

نصب Git رو بررسی کن:
git --version
مسیر فعلی:
Get-Location
وضعیت Repository:
git status
اگر هیچ تغییر ثبت‌نشده‌ای نداریم، خروجی شبیه اینه:
On branch main
nothing to commit, working tree clean
ممکنه نام Branch در سیستم تو متفاوت باشه. اگر تغییرات واقعی و مهمی داری، فعلاً اون‌ها رو حذف نکن. برای ادامه تمرین بهتره با یک Repository تمیز شروع کنیم.

نام فایل‌ها رو ببین:
Get-ChildItem -Name
فایل تمرینی ما about-me.txt هست. اگر جلسه قبل نام دیگه‌ای انتخاب کردی، از همون نام واقعی استفاده کن.
Get-Content .\about-me.txt
محتوای نمونه:
Name: Ali
Major: Computer Engineering
Favorite Language: Python
Goal: Learn Git
۲. مشاهده Commit History
هر Commit یک نقطه ثبت‌شده در History پروژه است.
Commit 1: Add my profile
          |
          v
Commit 2: Add learning goal
برای مشاهده History:
git log
نمونه خروجی:
commit 5d6e7f8123456789...
Author: Ali Ahmadi <ali@example.com>
Date:   Tue Oct 20 10:30:00 2026

    Add learning goal

commit 1a2b3c4123456789...
Author: Ali Ahmadi <ali@example.com>
Date:   Tue Oct 20 10:10:00 2026

    Add my profile
در این خروجی:
- Commit Hash: شناسه مخصوص Commit
- Author: نام و ایمیل ثبت‌کننده
- Date: زمان ثبت
- Commit Message: توضیح کوتاه درباره تغییر
اعداد و اطلاعات خروجی فقط نمونه هستن. برای خروج از نمایش طولانی git log می‌تونی کلید q رو بزنی.

برای خلاصه کردن History:
git log --oneline
5d6e7f8 Add learning goal
1a2b3c4 Add my profile
⚡ سؤال سریع
تفاوت git log و git log --oneline چیه؟
<details>
<summary>نمایش پاسخ</summary>
دستور اول اطلاعات بیشتری نمایش می‌ده و دستور دوم هر Commit رو خلاصه در یک خط نشون می‌ده.
</details>۳. بررسی جزئیات یک Commit
اگر بخوایم بدونیم آخرین Commit دقیقاً چه خط‌هایی رو تغییر داده:
git show
بخشی از خروجی نمونه:
+Goal: Learn Git
علامت + یعنی خط در مقایسه اضافه شده و - یعنی خط حذف شده.

برای مشاهده یک Commit مشخص، اول شناسه واقعی اون رو پیدا کن:
git log --oneline
بعد با شناسه خودت دستور رو اجرا کن؛ مثلاً:
git show 1a2b3c4
شناسه بالا فقط نمونه است و روی Repository تو ممکنه کار نکنه.
🧠 سؤال مفهومی
برای دیدن تغییرات آخرین Commit از کدام دستور استفاده می‌کنیم؟
<details>
<summary>نمایش پاسخ</summary>
git show
</details>۴. تغییر فایل و مشاهده Diff
فایل تمرینی رو باز کن:
notepad .\about-me.txt
این خط رو در انتهای فایل اضافه کن:
Favorite Tool: Git
با Ctrl + S ذخیره کن و به PowerShell برگرد.
git status
حالا فایل باید در بخش Changes not staged for commit به‌صورت modified دیده بشه.

برای مشاهده اینکه دقیقاً چه چیزی تغییر کرده:
git diff
بخشی از خروجی نمونه:
 Name: Ali
 Major: Computer Engineering
 Favorite Language: Python
 Goal: Learn Git
+Favorite Tool: Git
خطی که با + شروع می‌شه اضافه شده؛ خطی که با - شروع می‌شه حذف شده.

برای مثال:
-Favorite Language: Python
+Favorite Language: Java
یعنی مقدار قبلی عوض شده. git diff خودش هیچ فایلی رو تغییر نمی‌ده.
⚡ سؤال سریع
-Color: Blue
+Color: Green
<details>
<summary>نمایش پاسخ</summary>مقدار Color از Blue به Green تغییر کرده.
</details>۵. تفاوت Staged و Unstaged
مدل اصلی Git:
Working Directory
       |
       | git add
       v
  Staging Area
       |
       | git commit
       v
Repository History
الان فایل تغییر کرده ولی هنوز Stage نشده. تغییر رو Stage کن:
git add about-me.txt
وضعیت:
git status
حالا باید زیر عنوان Changes to be committed نمایش داده بشه.

دوباره دستور زیر رو اجرا کن:
git diff
در این تمرین خروجی خالیه؛ چون محتوای Working Directory و Staging Area یکسان شده. تغییر از بین نرفته.

برای دیدن تغییر Stage شده:
git diff --staged
باید دوباره خط جدید دیده بشه:
+Favorite Tool: Git
این مدل رو به خاطر بسپار:
Last Commit
     |
     | git diff --staged
     v
Staging Area
     |
     | git diff
     v
Working Directory
پیکان‌ها مسیر مقایسه رو نشون می‌دن، نه جابه‌جایی فیزیکی فایل‌ها.
🧠 سؤال مفهومی
چرا بعد از git add خروجی git diff در تمرین ما خالیه؟
<details>
<summary>نمایش پاسخ</summary>
چون تغییر Stage شده و اختلاف جدیدی بین Working Directory و Staging Area وجود نداره. برای دیدن تغییر Stage شده از git diff --staged استفاده می‌کنیم.
</details>۶. Unstage کردن بدون حذف ویرایش‌ها
اگر اشتباهی فایل رو Stage کرده باشیم و بخوایم ویرایش‌ها داخل فایل باقی بمونن:
git restore --staged about-me.txt
حالا:
git status
باید فایل دوباره به‌صورت modified زیر Changes not staged for commit نمایش داده بشه.
git diff
باز هم خط اضافه‌شده دیده می‌شه:
+Favorite Tool: Git
پس git restore --staged تغییرات Working Directory رو پاک نمی‌کنه؛ فقط وضعیت Staged رو تغییر می‌ده.
۷. کنار گذاشتن تغییر آزمایشی
گاهی تصمیم می‌گیریم تغییر آزمایشی رو اصلاً نگه نداریم.
⚠️ هشدار: دستور بعدی تغییرات Unstaged فایل Track شده رو دور می‌ریزه و ممکنه قابل بازیابی نباشن. فقط روی فایل تمرینی و بعد از بررسی تغییرات اجراش کن.

در مثال ما فایل Unstage شده و Staging Area با آخرین Commit یکسانه. حالا:
git restore about-me.txt
بررسی:
git status
اگر تغییر دیگری نداشته باشیم:
nothing to commit, working tree clean
برای اطمینان از محتوای فایل:
Get-Content .\about-me.txt
خط Favorite Tool: Git دیگه نباید وجود داشته باشه.

تفاوت دو دستور:
دستور	نتیجه
git restore --staged about-me.txt	Unstage می‌کنه، ویرایش‌های Working Directory باقی می‌مونن
git restore about-me.txt	تغییرات Unstaged فایل Track شده رو کنار می‌ذاره


نکته دقیق: git restore بدون --staged محتوای Working Directory رو از Staging Area بازسازی می‌کنه؛ در تمرین ما چون Staging Area با آخرین Commit یکسانه، فایل به وضعیت Commit قبلی برمی‌گرده.
۸. تمرین عملی
این تمرین رو روی Repository خودت انجام بده:

۱. ابتدا وضعیت پروژه رو بررسی کن:
git status
۲. فایل Track شده رو باز کن:
notepad .\about-me.txt
۳. این خط رو اضافه و ذخیره کن:
Current Course: Git Basics
۴. وضعیت و تغییر Unstaged رو ببین:
git status
git diff
۵. Stage کن:
git add about-me.txt
۶. هر دو نوع Diff رو بررسی کن:
git diff
git diff --staged
۷. Unstage کن:
git restore --staged about-me.txt
۸. ببین تغییر هنوز باقیه:
git status
git diff
۹. فقط اگر این تغییر آزمایشی رو نمی‌خوای، اون رو کنار بذار:
git restore about-me.txt
۱۰. وضعیت و History رو بررسی کن:
git status
git log --oneline
مدل تمرین:
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
۹. Challenge — بدون نگاه به راهنما
- یک فایل Track شده انتخاب کن و یک خط بهش اضافه کن.
- قبل از Stage، تغییر رو مشاهده کن.
- تغییر رو Stage کن و Diff مربوط به Staging Area رو ببین.
- بدون حذف ویرایش‌ها، فایل رو Unstage کن.
- وضعیت فایل رو بررسی کن.
- فقط در صورت اطمینان، تغییر آزمایشی رو کنار بذار.
- آخرین وضعیت و History رو نمایش بده.
<details>
<summary>پرسش‌های راهنما و پاسخ‌ها</summary>- تغییر Unstaged: git diff
- تغییر Staged: git diff --staged
- Unstage بدون حذف ویرایش‌ها: git restore --staged about-me.txt
- کنار گذاشتن تغییر Unstaged: git restore about-me.txt (با احتیاط)
- دیدن History: git log --oneline
</details>۱۰. مشکلات رایج
fatal: not a git repository
احتمالاً داخل پوشه Repository نیستیم. مسیر رو بررسی کن:
Get-Location
git diff خروجی نداره
ممکنه فایل Save نشده باشه یا تغییر Stage شده باشه. وضعیت رو بررسی کن:
git status
اگر Staged بود:
git diff --staged
نام فایل پیدا نمی‌شه
Get-ChildItem -Name
نام واقعی فایل رو بررسی کن.
صفحه طولانی خروجی بسته نمی‌شه
کلید q رو فشار بده.
۱۱. Cheat Sheet
هدف	دستور
نمایش History	git log
نمایش خلاصه History	git log --oneline
بررسی آخرین Commit	git show
بررسی Commit مشخص	git show <commit-hash>
نمایش تغییرات Unstaged	git diff
نمایش تغییرات Staged	git diff --staged
Unstage کردن تغییر	git restore --staged <file>
حذف تغییرات Unstaged	git restore <file> ⚠️


جمع‌بندی
در جلسه اول یاد گرفتیم تغییرات رو Commit کنیم. در جلسه دوم یاد گرفتیم:
- History و جزئیات Commitها رو بخونیم.
- تغییرات فایل رو با Diff بررسی کنیم.
- تفاوت Staged و Unstaged رو تشخیص بدیم.
- یک تغییر رو بدون حذف ویرایش‌ها Unstage کنیم.
- تغییرات آزمایشی رو با احتیاط کنار بذاریم.
جلسه بعد:
Branching & Merging
منابع
- Pro Git
- git-log
- git-show
- git-diff
- git-restore
