# Git Command List

# Essential Git Commands

Git শেখার শুরুতে সবচেয়ে গুরুত্বপূর্ণ কিছু command হলো:

```bash
git config
git init
git status
git add
```

এই commands-গুলো Git repository setup করা এবং changes track করার basic workflow-এর অংশ।

---

# 1. `git config`

## What is `git config`?

`git config` command ব্যবহার করে Git-এর **configuration settings** সেট, পরিবর্তন এবং দেখতে পারি।

সহজভাবে:

> **`git config` → Git-এর settings configure করার command।**

Git-এর configuration-এর মধ্যে user name, email, default branch ইত্যাদি settings থাকতে পারে।

---

## কেন `git config` ব্যবহার করা হয়?

Git commit করার সময় Git-কে জানতে হয়:

- কে commit করেছে?
- তার name কী?
- তার email কী?

তাই Git ব্যবহার শুরু করার আগে সাধারণত user identity configure করা হয়।

---

## কখন ব্যবহার করতে হয়?

সাধারণত Git install করার পর **প্রথমবার setup করার সময়**।

### User Name

```bash
git config --global user.name "Your Name"
```

উদাহরণ:

```bash
git config --global user.name "Md Tuhin"
```

### User Email

```bash
git config --global user.email "your-email@example.com"
```

---

## `--global` কেন?

```bash
--global
```

ব্যবহার করলে configuration পুরো computer-এর Git-এর জন্য apply হয়।

অর্থাৎ:

```text
Computer
   │
   ├── Project A → একই Git identity
   ├── Project B → একই Git identity
   └── Project C → একই Git identity
```

---

## Configuration Check

```bash
git config --global --list
```

অথবা:

```bash
git config --global user.name
git config --global user.email
```

---

## Scope

Git configuration-এর তিনটি গুরুত্বপূর্ণ scope আছে:

```text
System
   ↓
Global
   ↓
Local
```

### Global

সব repository-এর জন্য:

```bash
git config --global user.name "Your Name"
```

### Local

শুধু current repository-এর জন্য:

```bash
git config --local user.name "Project Name"
```

সাধারণ developer-এর ক্ষেত্রে `--global` দিয়ে basic identity configure করাই যথেষ্ট।

---

# 2. `git init`

## What is `git init`?

`git init` command ব্যবহার করে একটি existing project folder-কে **Git repository** হিসেবে initialize করা হয়।

সহজভাবে:

> **`git init` → একটি project-এ Git tracking শুরু করে।**

---

## কেন `git init` ব্যবহার করা হয়?

ধরো তোমার computer-এ একটি project আছে:

```text
my-project/
├── main.py
├── README.md
└── requirements.txt
```

এখন তুমি চাও Git এই project-এর changes track করুক।

তাহলে project folder-এর ভিতরে:

```bash
git init
```

চালাতে হবে।

এর ফলে একটি hidden `.git` directory তৈরি হবে:

```text
my-project/
├── .git/
├── main.py
├── README.md
└── requirements.txt
```

`.git` directory-র ভিতরে Git-এর repository information এবং history management-এর প্রয়োজনীয় data থাকে।

---

## কখন `git init` ব্যবহার করতে হয়?

যখন তুমি:

- নতুন local project-এ Git শুরু করবে
- Existing project-কে Git repository বানাবে
- Local repository তৈরি করবে

---

## Example

```bash
mkdir my-project
cd my-project

git init
```

তারপর:

```bash
git status
```

দিয়ে repository-এর status দেখতে পারো।

---

## ⚠️ Important

একটি repository clone করার পর সাধারণত আবার:

```bash
git init
```

করতে হয় না।

কারণ `git clone` নিজেই Git repository তৈরি করে দেয়।

```text
git init
→ Existing folder → Git repository

git clone
→ Remote repository → Local Git repository
```

---

# 3. `git status`

## What is `git status`?

`git status` command বর্তমান Git repository-এর **বর্তমান অবস্থা** দেখায়।

সহজভাবে:

> **`git status` → Git project-এর current situation দেখার command।**

---

## কেন `git status` ব্যবহার করা হয়?

এটি আমাদের জানায়:

- কোন files নতুন
- কোন files modified
- কোন files staged
- কোন files commit-এর জন্য ready
- কোন branch-এ আছি
- কোনো change এখনও commit করা হয়নি কি না

---

## কখন ব্যবহার করতে হয়?

`git status` খুব frequently ব্যবহার করা যায়।

বিশেষ করে:

```text
কাজ শুরু
   ↓
git status
   ↓
Code change
   ↓
git status
   ↓
git add
   ↓
git status
   ↓
git commit
```

---

## Example

ধরো project-এ নতুন একটি file তৈরি করলে:

```text
my-project/
├── main.py
└── README.md
```

তারপর:

```bash
git status
```

Git দেখাতে পারে:

```text
Untracked files:
    README.md
```

এর অর্থ Git এখনও `README.md`-কে tracking-এর জন্য stage করেনি।

---

## Modified File

যদি tracked file পরিবর্তন করো:

```text
main.py
```

তারপর:

```bash
git status
```

Git জানাবে যে `main.py` modified হয়েছে।

---

# 4. `git add`

## What is `git add`?

`git add` command ব্যবহার করে files-এর changes-কে **Staging Area**-তে যোগ করা হয়।

সহজভাবে:

> **`git add` → কোন changes পরবর্তী commit-এ যাবে তা নির্বাচন করার command।**

---

# 🧠 Staging Area কী?

Git-এর basic workflow:

```text
Working Directory
       ↓
    git add
       ↓
Staging Area
       ↓
   git commit
       ↓
Repository
```

### Working Directory

তুমি যেখানে code লিখো এবং files পরিবর্তন করো।

### Staging Area

যেসব changes তুমি next commit-এ রাখতে চাও।

### Repository

যেখানে committed changes-এর history সংরক্ষিত হয়।

---

## কেন `git add` ব্যবহার করা হয়?

ধরো তোমার project-এ তিনটি file পরিবর্তন হয়েছে:

```text
main.py
login.py
payment.py
```

কিন্তু তুমি শুধু `login.py`-এর changes commit করতে চাও।

তাহলে:

```bash
git add login.py
```

এতে শুধু `login.py` staging area-তে যাবে।

এটি Git-এর একটি গুরুত্বপূর্ণ feature।

---

# `git add .`

সব modified এবং untracked files stage করতে:

```bash
git add .
```

এখানে:

```text
.
```

বর্তমান directory এবং তার নিচের applicable files/directories বোঝায়।

---

## Specific File Add

একটি নির্দিষ্ট file:

```bash
git add main.py
```

একাধিক file:

```bash
git add main.py login.py
```

---

# 🔄 Complete Workflow

এই ৪টি command কীভাবে একসঙ্গে কাজ করে সেটা সবচেয়ে গুরুত্বপূর্ণ।

ধরো নতুন project:

```text
my-project/
└── main.py
```

### Step 1 — Git Configure

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

এটি সাধারণত একবার setup করলেই হয়।

---

### Step 2 — Git Initialize

```bash
git init
```

এটি project-এ Git শুরু করে।

---

### Step 3 — Check Status

```bash
git status
```

এটি project-এর current Git state দেখায়।

---

### Step 4 — Stage Changes

```bash
git add main.py
```

অথবা:

```bash
git add .
```

এতে changes staging area-তে যায়।

---

### Step 5 — Check Again

```bash
git status
```

এখন দেখতে পারবে কোন changes staged হয়েছে।

---

### Step 6 — Commit

এরপর সাধারণত:

```bash
git commit -m "Add main file"
```

এটি staged changes-এর একটি snapshot তৈরি করে।

---

# 📊 Quick Comparison

| Command      | কাজ                               | কখন ব্যবহার করব?                    |
| ------------ | --------------------------------- | ----------------------------------- |
| `git config` | Git settings configure করে        | Git setup-এর সময়                    |
| `git init`   | Project-এ Git শুরু করে            | নতুন local repository তৈরি করার সময় |
| `git status` | Repository-এর current state দেখায় | কাজের সময় বারবার                    |
| `git add`    | Changes staging area-তে নেয়       | Commit করার আগে                     |

---

---

# ⚠️ Common Mistakes

### Mistake 1

`git init` বারবার করা।

```bash
git init
```

একটি repository initialize করার পর সাধারণত প্রতিবার এটি চালানোর প্রয়োজন নেই।

---

### Mistake 2

`git add .` করার আগে changes না দেখা।

ভালো workflow:

```bash
git status
git add .
git status
git commit -m "..."
```

---

### Mistake 3

`git add` এবং `git commit` একই জিনিস মনে করা।

এগুলো আলাদা:

```text
git add
   ↓
Select changes for commit

git commit
   ↓
Save staged changes as a snapshot
```

---

### Mistake 4

Sensitive files stage করা।

যেমন:

```text
.env
API keys
passwords
private keys
```

এসব repository-তে commit করা উচিত নয়।

---

# ⭐ Professional Workflow

একজন developer-এর জন্য একটি ভালো basic workflow:

```bash
git status

# Make changes

git status

git add <files>

git status

git commit -m "Meaningful commit message"
```

আর সব changes stage করার ক্ষেত্রে:

```bash
git status
git add .
git status
git commit -m "Describe the changes"
```

---

# 📌 Final Summary

চারটি command মনে রাখার সবচেয়ে সহজ উপায়:

```text
git config
    ↓
"Git কে আমি?"

git init
    ↓
"এই project-এ Git শুরু করো"

git status
    ↓
"এখন project-এর অবস্থা কী?"

git add
    ↓
"এই changes-গুলো next commit-এর জন্য প্রস্তুত করো"
```

### One-Line Definition

> **`git config` configures Git, `git init` initializes a repository, `git status` shows the repository state, and `git add` stages changes for the next commit.**
