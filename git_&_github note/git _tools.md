

# Git Bash, Git GUI & Gitk

Git install করার পর Git-এর সাথে কিছু additional tools পাওয়া যায়। এর মধ্যে **Git Bash, Git GUI এবং Gitk** সবচেয়ে পরিচিত।

---

## 1. Git Bash

**Git Bash** হলো Windows-এর জন্য একটি **command-line interface (CLI)**, যেখানে Git commands এবং Unix/Linux-style commands ব্যবহার করা যায়।

উদাহরণ:

```bash
git status
git add .
git commit -m "Initial commit"
git push
```

### সহজভাবে

> **Git Bash = Git commands চালানোর Terminal**

Windows-এ Linux-এর মতো command-line environment ব্যবহার করতে Git Bash অনেক সুবিধাজনক।

---

## 2. Git GUI

**Git GUI** হলো Git-এর জন্য একটি **graphical user interface (GUI)**।

এখানে command না লিখে graphical interface-এর মাধ্যমে Git-এর বিভিন্ন কাজ করা যায়।

যেমন:

- Changes দেখা
- Files stage করা
- Commit করা
- Branch manage করা
- Repository-এর status দেখা

### সহজভাবে

> **Git GUI = Git commands-এর graphical interface**

যারা command line-এর পরিবর্তে visual interface পছন্দ করে, তাদের জন্য Git GUI useful হতে পারে।

---

## 3. Gitk

**Gitk** হলো Git-এর একটি **graphical history viewer**।

এটি মূলত repository-এর:

- Commit history
- Branches
- Commit relationships
- Parent/child commits

visualভাবে দেখানোর জন্য ব্যবহৃত হয়।

Command:

```bash
gitk
```

Gitk চালু করলে repository-এর commit history একটি graphical view-তে দেখা যায়।

### সহজভাবে

> **Gitk = Git commit history দেখার graphical tool**

---

## ⚖️ Quick Comparison

| Tool         | Type | Main Purpose                 |
| ------------ | ---- | ---------------------------- |
| **Git Bash** | CLI  | Git commands চালানো          |
| **Git GUI**  | GUI  | Graphicalভাবে Git manage করা |
| **Gitk**     | GUI  | Commit history visualize করা |

---

## 🧠 সহজভাবে মনে রাখো

```text
Git Bash
   ↓
Commands লিখে Git ব্যবহার

Git GUI
   ↓
GUI দিয়ে Git manage

Gitk
   ↓
Git history দেখতে
```

### Professional Development

বর্তমানে professional developers সাধারণত **Git CLI** বেশি ব্যবহার করেন, কারণ command line দ্রুত এবং automation-friendly। তবে Git GUI এবং Gitk Git-এর concepts বোঝা ও visualভাবে history দেখার ক্ষেত্রে useful tools।

---

## Summary

**Git Bash** → Git-এর command-line interface

**Git GUI** → Git-এর graphical interface

**Gitk** → Git commit history-এর graphical viewer

> **Git Bash is for executing Git commands, Git GUI is for graphical Git operations, and Gitk is for visualizing Git history.**
