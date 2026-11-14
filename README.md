
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
Collaboration
      |
      v
 Pull Request
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

در این جلسه یاد می‌گیریم چطور با استفاده از Branch روی قابلیت‌های جدید پروژه کار کنیم، بدون اینکه مستقیماً Branch اصلی رو تغییر بدیم.

همچنین یاد می‌گیریم چطور تغییرات رو روی Branch جدید Commit کنیم و در نهایت با Merge اون‌ها رو وارد Branch اصلی کنیم.

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

## جلسه ۴ — GitHub و اتصال Repository

```text
GitHub & Remote Repository
```

تا این جلسه تمام فعالیت‌های ما روی کامپیوتر خودمون انجام می‌شدن.

در جلسه چهارم یاد می‌گیریم چطور پروژه محلی رو به GitHub متصل کنیم و Commitهای پروژه رو برای اولین بار روی GitHub منتشر کنیم.

همچنین تفاوت Git و GitHub و مفهوم مخزن محلی و مخزن راه دور رو بررسی می‌کنیم.

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
```

### مهارت‌های عملی

در پایان این جلسه می‌تونیم:

- یک Repository خالی در GitHub ایجاد کنیم.
- آدرس Repository آنلاین رو دریافت کنیم.
- Repository محلی رو به GitHub متصل کنیم.
- اتصال ایجادشده رو بررسی کنیم.
- اولین Push رو انجام بدیم.
- فایل‌ها و Commitهای پروژه رو در GitHub مشاهده کنیم.

**وضعیت:** برگزارشده

### [ورود به جلسه ۴](./sessions/session-04/)

---

## جلسه ۵ — دریافت پروژه و همکاری تیمی

```text
Clone, Fetch, Pull & Collaboration
```

در این جلسه یاد می‌گیریم چطور یک Repository موجود رو از GitHub روی سیستم خودمون دریافت کنیم.

همچنین بررسی می‌کنیم چطور تغییرات جدید مخزن راه دور رو دریافت کنیم و پروژه محلی رو با اون هماهنگ نگه داریم.

در ادامه با مفاهیم اولیه همکاری تیمی آشنا می‌شیم.

### موضوعات برنامه‌ریزی‌شده

```text
git clone
git fetch
git pull
Remote-tracking Branch
Sync
Collaboration
Merge Conflict
Conflict Resolution
```

**وضعیت:** در برنامه آموزشی

---

## جلسه ۶ — Workflow واقعی GitHub

```text
Pull Request & Code Review
```

در جلسه آخر با Workflow رایج تیم‌های نرم‌افزاری آشنا می‌شیم.

یاد می‌گیریم چطور تغییرات یک Branch رو برای بررسی به دیگران پیشنهاد بدیم و بعد از بررسی، اون‌ها رو وارد Branch اصلی کنیم.

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

در پایان دوره یک Workflow واقعی GitHub رو از ابتدا تا انتها انجام می‌دیم.

**وضعیت:** در برنامه آموزشی

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

قرار نیست فقط Commandها رو حفظ کنیم.

اول می‌فهمیم هر ابزار **چرا وجود داره**، بعد ازش استفاده می‌کنیم.

---

# تمرین نهایی

در پایان دوره باید بتونیم این Workflow رو بدون کمک انجام بدیم:

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
 Push / Pull
      |
      v
 Collaborate
      |
      v
Resolve Conflict
      |
      v
Create Pull Request
```

این تمرین به ما کمک می‌کنه مطالب دوره رو در یک پروژه واقعی کنار هم استفاده کنیم.

---

# منابع

برای طراحی محتوای دوره از منابع معتبر زیر استفاده می‌شه.

## کتاب Pro Git

```text
Pro Git
```

کتاب رسمی و رایگان Git.

[مطالعه کتاب Pro Git](https://git-scm.com/book/en/v2)

## مستندات رسمی Git

```text
Git Documentation
```

مرجع رسمی دستورات و قابلیت‌های Git.

[مشاهده مستندات Git](https://git-scm.com/docs)

## مستندات رسمی GitHub

```text
GitHub Documentation
```

راهنمای رسمی استفاده از GitHub و قابلیت‌های همکاری تیمی.

[مشاهده مستندات GitHub](https://docs.github.com/)

## دوره مقدماتی Google

```text
Google - Introduction to Git and GitHub
```

دوره مقدماتی Google در Coursera.

[مشاهده دوره در Coursera](https://www.coursera.org/learn/introduction-git-github)

---

# شروع دوره

برای شروع، جلسات رو به‌ترتیب دنبال کن.

### [جلسه ۱ — Version Control & Git Basics](./sessions/session-01/)

### [جلسه ۲ — Git History, Diff & Basic Undo](./sessions/session-02/)

### [جلسه ۳ — Git Branching & Merging](./sessions/session-03/)

### [جلسه ۴ — GitHub & Remote Repository](./sessions/session-04/)

---

**Version Control with Git & GitHub**

یادگیری قدم‌به‌قدم Git، از اولین Commit تا همکاری روی پروژه‌های واقعی.
