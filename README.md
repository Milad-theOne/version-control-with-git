
# Version Control with Git & GitHub

یک دوره ساده، عملی و قدم‌به‌قدم برای یادگیری کنترل نسخه با Git و GitHub.

هدف این دوره فقط حفظ کردن چند دستور نیست.

هدف اینه که بعد از پایان دوره بتونیم Git رو واقعاً داخل پروژه‌های دانشگاهی و شخصی خودمون استفاده کنیم.

---

# مسیر یادگیری

در طول دوره از مفاهیم پایه شروع می‌کنیم و کم‌کم به Workflow واقعی Git و GitHub می‌رسیم.

```text
Version Control
      |
      v
     Git
      |
      v
 Repository
      |
      v
Commit & History
      |
      v
Branch & Merge
      |
      v
GitHub & Remote
      |
      v
     Push
      |
      v
    Clone
      |
      v
 Fetch & Pull
      |
      v
Collaboration
      |
      v
Merge Conflict
      |
      v
Pull Request & Code Review
```

---

# جلسات دوره

## جلسه ۱ — شروع کار با Git

```text
Version Control & Git Basics
```

در این جلسه با مفهوم کنترل نسخه آشنا می‌شیم و اولین Repository و Commit خودمون رو می‌سازیم.

### موضوعات اصلی

```text
Version Control
Git
GitHub
Repository
Working Directory
Staging Area
git init
git status
git add
git commit
git log --oneline
```

**وضعیت:** برگزارشده و منتشرشده

### [ورود به جلسه ۱](./sessions/session-01/)

---

## جلسه ۲ — تاریخچه و تغییرات پروژه

```text
History, Diff & Undo
```

در این جلسه یاد می‌گیریم چطور تاریخچه تغییرات رو مشاهده کنیم، تفاوت نسخه‌های مختلف فایل‌ها رو بررسی کنیم و بعضی اشتباهات ساده رو اصلاح کنیم.

### موضوعات اصلی

```text
git log
git log --oneline
git show
git diff
git diff --staged
git restore --staged
git restore
Commit History
Comparing Changes
Basic Undo
```

**وضعیت:** برگزارشده و منتشرشده

### [ورود به جلسه ۲](./sessions/session-02/)

---

## جلسه ۳ — Branch و Merge

```text
Branching & Merging
```

در این جلسه یاد می‌گیریم چطور روی بخش‌های جدید پروژه در شاخه‌های جداگانه کار کنیم، بدون اینکه مستقیماً شاخه اصلی پروژه رو تغییر بدیم.

همچنین یاد می‌گیریم چطور تغییرات رو در شاخه جدید ثبت کنیم و در نهایت اون‌ها رو وارد شاخه اصلی کنیم.

### موضوعات اصلی

```text
Branch
Commit vs Branch
HEAD
git branch
git switch
git switch -c
git merge
Fast-forward Merge
git log --oneline --graph --all --decorate
```

**وضعیت:** برگزارشده و منتشرشده

### [ورود به جلسه ۳](./sessions/session-03/)

---

## جلسه ۴ — اتصال پروژه به GitHub

```text
GitHub & Remote Repository
```

تا قبل از این جلسه، تمام فعالیت‌های ما روی کامپیوتر خودمون انجام می‌شدن.

در جلسه چهارم یاد می‌گیریم چطور پروژه محلی رو به مخزن راه دور متصل کنیم و تغییرات ثبت‌شده پروژه رو برای اولین بار در GitHub منتشر کنیم.

همچنین تفاوت گیت و گیت‌هاب و مفهوم مخزن محلی و مخزن راه دور رو بررسی می‌کنیم.

### موضوعات اصلی

```text
Git vs GitHub
Local Repository
Remote Repository
Remote
origin
HTTPS Repository URL
git remote -v
git remote add origin URL
git push -u origin main
git push
Upstream
git branch -vv
```

### مهارت‌های عملی

در پایان این جلسه می‌تونیم:

- یک مخزن خالی در گیت‌هاب ایجاد کنیم.
- آدرس مخزن آنلاین رو دریافت کنیم.
- مخزن محلی رو به مخزن راه دور متصل کنیم.
- اتصال ایجادشده رو بررسی کنیم.
- اولین ارسال تغییرات رو انجام بدیم.
- فایل‌ها و تاریخچه پروژه رو در گیت‌هاب مشاهده کنیم.

**وضعیت:** برگزارشده و منتشرشده

### [ورود به جلسه ۴](./sessions/session-04/)

---

## جلسه ۵ — دریافت پروژه از GitHub

```text
Git Clone & Download ZIP
```

در جلسه چهارم یاد گرفتیم چطور پروژه محلی خودمون رو در گیت‌هاب منتشر کنیم.

در جلسه پنجم مسیر برعکس رو بررسی می‌کنیم.

یاد می‌گیریم چطور یک مخزن موجود رو همراه با تاریخچه تغییراتش روی کامپیوتر خودمون دریافت کنیم.

همچنین تفاوت دریافت کامل مخزن با دانلود فایل فشرده رو به‌صورت عملی بررسی می‌کنیم.

### موضوعات اصلی

```text
Clone
git clone
Repository URL
Destination Folder
.git Directory
Clone vs Download ZIP
git init vs git clone
git status
git log --oneline
git remote -v
Get-ChildItem -Force -Name
```

### مهارت‌های عملی

در پایان این جلسه می‌تونیم:

- آدرس یک مخزن موجود رو دریافت کنیم.
- یک نسخه محلی جدید از مخزن ایجاد کنیم.
- نام پوشه مقصد رو مشخص کنیم.
- فایل‌های پروژه دریافت‌شده رو بررسی کنیم.
- تاریخچه تغییرات مخزن رو مشاهده کنیم.
- اتصال راه دور ایجادشده رو بررسی کنیم.
- فایل‌ها و پوشه‌های مخفی پروژه رو مشاهده کنیم.
- تفاوت دریافت کامل مخزن و دانلود فایل فشرده رو توضیح بدیم.
- روش مناسب دریافت پروژه رو بر اساس نیاز خودمون انتخاب کنیم.

**وضعیت:** برگزارشده

### [ورود به جلسه ۵](./sessions/session-05/)

---

## جلسه ۶ — دریافت تغییرات و همکاری تیمی

```text
Fetch, Pull & Collaboration
```

در جلسه پنجم یاد گرفتیم چطور یک نسخه محلی از مخزن موجود ایجاد کنیم.

اما ممکنه بعد از دریافت پروژه، تغییرات جدیدی در مخزن راه دور ایجاد بشن.

در این جلسه یاد می‌گیریم چطور بدون دریافت دوباره کل پروژه، تغییرات جدید رو دریافت کنیم و مخزن محلی خودمون رو به‌روز نگه داریم.

همچنین با مفاهیم همکاری تیمی و مشکلاتی که هنگام تغییر هم‌زمان پروژه ایجاد می‌شن آشنا می‌شیم.

### موضوعات برنامه‌ریزی‌شده

```text
git fetch
git pull
Fetch vs Pull
Remote-tracking Branch
origin/main
Synchronization
Fast-forward
Collaboration
Merge Conflict
Conflict Resolution
```

### مهارت‌های مورد انتظار

- دریافت تغییرات جدید مخزن راه دور
- بررسی تغییرات قبل از اعمال آن‌ها
- به‌روزرسانی شاخه محلی
- درک تفاوت دریافت و ادغام تغییرات
- آشنایی با همکاری چند نفر روی یک پروژه
- آشنایی با تعارض تغییرات و روش حل آن

**وضعیت:** در برنامه پیشنهادی دوره

---

## جلسه ۷ — Workflow واقعی GitHub

```text
Pull Request & Code Review
```

در این جلسه با روش رایج همکاری تیم‌های نرم‌افزاری آشنا می‌شیم.

یاد می‌گیریم چطور روی یک شاخه جداگانه کار کنیم، تغییرات خودمون رو ثبت کنیم و اون‌ها رو برای بررسی به سایر اعضای تیم پیشنهاد بدیم.

در نهایت، بعد از بررسی تغییرات، اون‌ها رو وارد شاخه اصلی پروژه می‌کنیم.

### موضوعات برنامه‌ریزی‌شده

```text
Branch
Commit
Push
Pull Request
Code Review
Merge
Collaboration Workflow
```

### مهارت‌های مورد انتظار

- ایجاد شاخه برای توسعه قابلیت جدید
- ثبت و ارسال تغییرات شاخه
- ایجاد درخواست ادغام تغییرات
- بررسی تغییرات سایر اعضای تیم
- ادغام تغییرات تأییدشده
- انجام یک چرخه کامل همکاری تیمی

در پایان دوره یک Workflow واقعی GitHub رو از ابتدا تا انتها انجام می‌دیم.

**وضعیت:** در برنامه پیشنهادی دوره

---

# روش یادگیری

این دوره تا جای ممکن عملی طراحی شده.

هر جلسه شامل این بخش‌هاست:

```text
  Concept
     |
     v
  Example
     |
     v
Live Practice
     |
     v
 Questions
     |
     v
 Challenge
```

قرار نیست فقط دستورات رو حفظ کنیم.

اول می‌فهمیم هر ابزار **چرا وجود داره**، بعد ازش استفاده می‌کنیم.

هدف اینه که بتونیم مفاهیم یادگرفته‌شده رو در پروژه‌های واقعی به کار ببریم.

---

# تمرین نهایی

در پایان دوره باید بتونیم مسیر زیر رو بدون کمک انجام بدیم:

```text
Create Project
      |
      v
Initialize Git
      |
      v
Create Commits
      |
      v
Create Branch
      |
      v
Merge Changes
      |
      v
Connect to GitHub
      |
      v
   git push
      |
      v
   git clone
      |
      v
 Fetch & Pull
      |
      v
 Collaborate
      |
      v
Resolve Conflict
      |
      v
Create Pull Request
      |
      v
 Code Review
      |
      v
 Merge Changes
```

این تمرین به ما کمک می‌کنه مطالب دوره رو در یک پروژه واقعی کنار هم استفاده کنیم.

---

# منابع

برای طراحی محتوای دوره از منابع معتبر زیر استفاده می‌شه.

## کتاب Pro Git

```text
Pro Git
```

کتاب رایگان و مرجع جامع یادگیری گیت.

[مطالعه کتاب Pro Git](https://git-scm.com/book/en/v2)

## مستندات رسمی Git

```text
Git Documentation
```

مرجع رسمی دستورات و قابلیت‌های گیت.

[مشاهده مستندات Git](https://git-scm.com/docs)

## مستندات رسمی GitHub

```text
GitHub Documentation
```

راهنمای رسمی استفاده از گیت‌هاب و قابلیت‌های همکاری تیمی.

[مشاهده مستندات GitHub](https://docs.github.com/)

## دوره مقدماتی Google

```text
Google - Introduction to Git and GitHub
```

دوره مقدماتی گوگل در کورسرا.

[مشاهده دوره در Coursera](https://www.coursera.org/learn/introduction-git-github)

---

# شروع دوره

برای شروع، جلسات رو به‌ترتیب دنبال کن.

### [جلسه ۱ — Version Control & Git Basics](./sessions/session-01/)

### [جلسه ۲ — Git History, Diff & Basic Undo](./sessions/session-02/)

### [جلسه ۳ — Git Branching & Merging](./sessions/session-03/)

### [جلسه ۴ — GitHub & Remote Repository](./sessions/session-04/)

### [جلسه ۵ — Git Clone & Download ZIP](./sessions/session-05/)

---

**Version Control with Git & GitHub**

یادگیری قدم‌به‌قدم Git، از اولین Commit تا همکاری روی پروژه‌های واقعی.
