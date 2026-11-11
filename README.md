
# Version Control with Git & GitHub

یک دوره‌ی ساده، عملی و قدم‌به‌قدم برای یادگیری کنترل نسخه با Git و GitHub.

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

موضوعات اصلی:

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

### [ورود به جلسه ۱](./sessions/session-01/)

---

## جلسه ۲ — تاریخچه و تغییرات پروژه

```text
History, Diff & Undo
```

موضوعات اصلی:

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

### [ورود به جلسه ۲](./sessions/session-02/)

---

## جلسه ۳ — Branch و Merge

```text
Branching & Merging
```

در این جلسه یاد می‌گیریم چطور با استفاده از Branch روی قابلیت‌های جدید پروژه کار کنیم، بدون اینکه مستقیماً Branch اصلی رو تغییر بدیم.

همچنین یاد می‌گیریم چطور تغییرات رو روی Branch جدید Commit کنیم و در نهایت با Merge اون‌ها رو وارد Branch اصلی کنیم.

موضوعات اصلی:

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

### [ورود به جلسه ۳](./sessions/session-03/)

---

## جلسه ۴ — GitHub و Remote Repository

```text
GitHub & Remote
```

پروژه Local رو به GitHub متصل می‌کنیم.

موضوعات اصلی:

```text
Remote Repository
git remote
git clone
git push
git pull
git fetch
```

---

## جلسه ۵ — کار تیمی و Conflict

```text
Collaboration & Merge Conflicts
```

یاد می‌گیریم چند نفر چطور روی یک Repository کار کنن و Conflictهای ساده رو حل کنن.

موضوعات اصلی:

```text
Collaboration
Sync
Push
Pull
Merge Conflict
Conflict Resolution
```

---

## جلسه ۶ — Workflow واقعی GitHub

```text
Pull Request & Code Review
```

در جلسه آخر با Workflow رایج تیم‌های نرم‌افزاری آشنا می‌شیم.

موضوعات اصلی:

```text
Branch
Commit
Push
Pull Request
Code Review
Merge
```

در پایان دوره یک Workflow واقعی GitHub رو از ابتدا تا انتها انجام می‌دیم.

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

---

# منابع

برای طراحی محتوای دوره از منابع معتبر زیر استفاده می‌شه:

```text
Pro Git
```

کتاب رسمی و رایگان Git

[مطالعه کتاب Pro Git](https://git-scm.com/book/en/v2)

```text
Git Documentation
```

مستندات رسمی Git

[مشاهده مستندات Git](https://git-scm.com/docs)

```text
GitHub Documentation
```

مستندات رسمی GitHub

[مشاهده مستندات GitHub](https://docs.github.com/)

```text
Google - Introduction to Git and GitHub
```

دوره مقدماتی Google در Coursera

[مشاهده دوره در Coursera](https://www.coursera.org/learn/introduction-git-github)

---

# شروع دوره

برای شروع، جلسات رو به‌ترتیب دنبال کن:

### [جلسه ۱ — Version Control & Git Basics](./sessions/session-01/)

### [جلسه ۲ — Git History, Diff & Basic Undo](./sessions/session-02/)

### [جلسه ۳ — Git Branching & Merging](./sessions/session-03/)
