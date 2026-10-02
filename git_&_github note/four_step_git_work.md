# Git — Working Directory, Staging Area, Local Repository & Remote Repository

Git-এ একটি project-এর পরিবর্তন সাধারণত চারটি ধাপের মধ্য দিয়ে যায়:

```text
Working Directory
       ↓ git add
Staging Area
       ↓ git commit
Local Repository
       ↓ git push
Remote Repository
```

এই চারটি জায়গা Git-এর basic workflow বোঝার জন্য অত্যন্ত গুরুত্বপূর্ণ।

---

## 1. Working Directory

**Working Directory** হলো আপনার computer-এর সেই project folder যেখানে আপনি সরাসরি code লিখেন, edit করেন এবং নতুন file তৈরি করেন।

উদাহরণ:

```text
my_flutter_app/
├── lib/
│   └── main.dart
├── pubspec.yaml
└── README.md
```

আপনি যদি `main.dart`-এর code পরিবর্তন করেন, তাহলে সেই পরিবর্তন প্রথমে **Working Directory**-তে থাকে।

### Example

আগে:

```dart
Text("Hello");
```

পরিবর্তনের পরে:

```dart
Text("Hello Tuhin");
```

Git এই পরিবর্তনটি detect করতে পারে:

```bash
git status
```

### সহজভাবে

> **Working Directory = যেখানে আমরা project-এর code নিয়ে কাজ করি।**

---

## 2. Staging Area

Working Directory-তে করা পরিবর্তন সরাসরি commit না করে প্রথমে **Staging Area**-তে নেওয়া হয়।

এর জন্য ব্যবহার করা হয়:

```bash
git add .
```

অথবা নির্দিষ্ট file stage করতে:

```bash
git add lib/main.dart
```

Flow:

```text
Working Directory
       ↓
    git add
       ↓
Staging Area
```

Staging Area-এর মাধ্যমে আমরা নির্ধারণ করতে পারি **কোন কোন পরিবর্তন পরবর্তী commit-এর মধ্যে যাবে।**

### Example

ধরুন project-এ দুটি file পরিবর্তন হয়েছে:

```text
main.dart
home_screen.dart
```

শুধু `main.dart` commit করতে চাইলে:

```bash
git add lib/main.dart
```

এতে শুধু `main.dart` staging area-তে যাবে।

### সহজভাবে

> **Staging Area = যেসব পরিবর্তন আমরা commit করতে চাই, সেগুলো প্রস্তুত করে রাখার জায়গা।**

---

## 3. Local Repository

Staging Area-তে থাকা changes-কে Git-এর history-তে save করার জন্য **commit** করা হয়।

```bash
git commit -m "Update home screen"
```

Flow:

```text
Staging Area
      ↓
  git commit
      ↓
Local Repository
```

**Local Repository** হলো আপনার computer-এ থাকা Git repository, যেখানে আপনার commit history সংরক্ষিত থাকে।

Commit history দেখতে:

```bash
git log
```

### গুরুত্বপূর্ণ বিষয়

`git commit` করার পর changes এখনো GitHub-এ যায়নি।

Commit শুধুমাত্র আপনার **Local Repository**-তে save হয়।

### সহজভাবে

> **Local Repository = নিজের computer-এ থাকা Git history যেখানে commits সংরক্ষিত থাকে।**

---

## 4. Remote Repository

**Remote Repository** হলো internet/server-এ থাকা Git repository।

সবচেয়ে জনপ্রিয় Remote Repository platform:

- GitHub
- GitLab
- Bitbucket

Local Repository থেকে Remote Repository-তে commit পাঠাতে:

```bash
git push
```

Flow:

```text
Local Repository
       ↓
    git push
       ↓
Remote Repository
     (GitHub)
```

### সহজভাবে

> **Remote Repository = Online/server-এ থাকা repository যেখানে project এবং commit অন্যদের সাথে share করা যায়।**

---

# Complete Git Workflow

একজন developer সাধারণত এভাবে Git ব্যবহার করেন:

```text
       Write / Edit Code
              ↓
      Working Directory
              ↓
          git add
              ↓
        Staging Area
              ↓
          git commit
              ↓
       Local Repository
              ↓
           git push
              ↓
      Remote Repository
          (GitHub)
```

---

# Important Git Commands

| Command                   | কাজ                                                      |
| ------------------------- | -------------------------------------------------------- |
| `git status`              | Project-এর বর্তমান পরিবর্তন দেখায়                        |
| `git add .`               | সব পরিবর্তন Staging Area-তে নেয়                          |
| `git add <file>`          | নির্দিষ্ট file stage করে                                 |
| `git commit -m "message"` | staged changes Local Repository-তে save করে              |
| `git log`                 | Commit history দেখায়                                     |
| `git push`                | Local Repository থেকে Remote Repository-তে changes পাঠায় |
| `git pull`                | Remote Repository থেকে latest changes নিয়ে আসে           |

---

# Real Project Example

ধরুন আপনি একটি Flutter project-এ কাজ করছেন এবং `home_screen.dart` পরিবর্তন করলেন।

### Step 1 — Check Changes

```bash
git status
```

### Step 2 — Add Changes

```bash
git add lib/home_screen.dart
```

### Step 3 — Commit Changes

```bash
git commit -m "Update home screen UI"
```

### Step 4 — Push to GitHub

```bash
git push
```

Complete flow:

```text
home_screen.dart
      ↓
Working Directory
      ↓ git add
Staging Area
      ↓ git commit
Local Repository
      ↓ git push
GitHub
```

---

# Working Directory vs Staging Area vs Local Repository vs Remote Repository

| বিষয়                  | কোথায় থাকে?          | কী কাজ করে?                             |
| --------------------- | -------------------- | --------------------------------------- |
| **Working Directory** | আপনার computer       | Code লেখা ও পরিবর্তন করা                |
| **Staging Area**      | Git-এর staging space | Commit করার জন্য changes নির্বাচন করা   |
| **Local Repository**  | আপনার computer       | Commit ও Git history সংরক্ষণ করা        |
| **Remote Repository** | Online server        | Project ও commits online রাখা/share করা |

---

# মনে রাখার সহজ নিয়ম

```text
Working Directory
= Code লিখি / পরিবর্তন করি

        ↓ git add

Staging Area
= Commit করার জন্য প্রস্তুত করি

        ↓ git commit

Local Repository
= Commit history নিজের computer-এ save করি

        ↓ git push

Remote Repository
= GitHub-এ upload/share করি
```

## Quick Revision

> **Working Directory → কাজ করি**
> **Staging Area → Changes নির্বাচন করি**
> **Local Repository → Commit save করি**
> **Remote Repository → Online share করি**

### Git Workflow Shortcut

```bash
git status
git add .
git commit -m "Your commit message"
git push
```

এই চারটি command Git-এর দৈনন্দিন basic workflow-এর সবচেয়ে গুরুত্বপূর্ণ অংশ।
