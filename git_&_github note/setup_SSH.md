# GitHub SSH Key — সহজ বাংলায়

সংক্ষেপে বললে, আমরা একে **SSH** বলি।

---

## SSH কী?

প্রথমে SSH-এর একটি সংজ্ঞা দেওয়া যাক।

**SSH হলো একটি network protocol, যা দুটি computer-এর মধ্যে নিরাপদভাবে যোগাযোগ করতে সাহায্য করে।**

বিষয়টি একটি উদাহরণের মাধ্যমে বুঝি।

ধরুন, এখানে আপনার **কম্পিউটার** আছে এবং এটি হলো **GitHub-এর কম্পিউটার/সার্ভার**।

আপনি আপনার কম্পিউটার থেকে GitHub-এ কিছু data পাঠাতে চান এবং আবার GitHub থেকে আপনার কম্পিউটারে data গ্রহণ করতে চান।

এখন আপনি চান এই communication বা যোগাযোগটি যেন নিরাপদ হয়।

এখানেই **SSH** আমাদের সাহায্য করে।

---

# SSH কীভাবে কাজ করে?

আপনি যখন SSH সেটআপ করবেন, তখন আপনার কম্পিউটারে সাধারণত দুটি key তৈরি হবে:

- **Public Key**
- **Private Key**

এর মধ্যে **Public Key** আপনি আপনার GitHub account-এর SSH settings-এ যুক্ত করবেন।

আর **Private Key** আপনার কম্পিউটারেই থাকবে।

### সহজভাবে:

```text
Your Computer
     │
     ├── Public Key
     │       ↓
     │    GitHub
     │
     └── Private Key
```

Public Key GitHub-এ দেওয়া যায়, কিন্তু **Private Key কাউকে দেওয়া উচিত নয়**।

SSH ব্যবহার করে আপনার কম্পিউটার এবং GitHub-এর মধ্যে নিরাপদ authentication/communication তৈরি হয়।

---

# SSH কেন প্রয়োজন?

SSH ব্যবহারের প্রধান উদ্দেশ্য হলো **নিরাপদভাবে GitHub-এর সাথে যোগাযোগ করা এবং authentication করা।**

SSH Key সেটআপ করার পর GitHub repository-তে কাজ করার সময় বারবার username/password দেওয়ার প্রয়োজন হয় না।

অর্থাৎ, একবার SSH Key ঠিকভাবে সেটআপ করলে GitHub-এর সাথে কাজ করা অনেক সহজ হয়ে যায়।

বিশেষ করে আপনি যখন:

- `git clone`
- `git push`
- `git pull`

ইত্যাদি কাজ করবেন, তখন SSH authentication ব্যবহার করতে পারবেন।

---

# SSH Key কীভাবে সেটআপ করবেন?

প্রথমে আপনার **Terminal** অথবা **Command Prompt** খুলুন।

তারপর নিচের command ব্যবহার করুন:

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

এখানে:

```text
your-email@example.com
```

এর জায়গায় আপনার নিজের GitHub account-এর email address ব্যবহার করবেন।

উদাহরণ:

```bash
ssh-keygen -t ed25519 -C "example@gmail.com"
```

তারপর **Enter** চাপুন।

---

## Key কোথায় Save করবেন?

এরপর Terminal-এ এমন একটি message আসতে পারে:

```text
Enter file in which to save the key
```

অর্থাৎ, SSH Key কোথায় save করতে চান তা জানতে চাইছে।

আপনি যদি default location ব্যবহার করতে চান, তাহলে শুধু:

**Enter চাপুন।**

তাহলে default location-এ SSH Key তৈরি হবে।

---

# Passphrase কী?

এরপর আপনাকে একটি **passphrase** দিতে বলা হবে।

Passphrase হলো SSH Key-এর জন্য একটি অতিরিক্ত security layer।

আপনি চাইলে একটি strong passphrase দিতে পারেন।

তারপর আবার একই passphrase দিতে হবে।

উদাহরণ:

```text
Enter passphrase:
Enter same passphrase again:
```

তারপর SSH Key তৈরি হয়ে যাবে।

---

# Public Key কোথায় থাকে?

SSH Key তৈরি হওয়ার পর সাধারণত `.ssh` folder-এর মধ্যে key files তৈরি হয়।

Ed25519 ব্যবহার করলে সাধারণত:

```text
id_ed25519
```

এটি হলো **Private Key**।

আর:

```text
id_ed25519.pub
```

এটি হলো **Public Key**।

### মনে রাখবেন:

| Key              | কাজ         | অন্যকে দেওয়া যাবে?    |
| ---------------- | ----------- | --------------------- |
| `id_ed25519`     | Private Key | ❌ না                 |
| `id_ed25519.pub` | Public Key  | ✅ GitHub-এ দেওয়া যায় |

**সবচেয়ে গুরুত্বপূর্ণ বিষয়: Private Key কখনো GitHub, GitHub repository, বা অন্য কারও সাথে share করবেন না।**

---

# Public Key কীভাবে দেখবেন?

Linux/macOS-এ নিচের command ব্যবহার করা যায়:

```bash
cat ~/.ssh/id_ed25519.pub
```

Windows PowerShell-এ ব্যবহার করতে পারেন:

```powershell
Get-Content ~/.ssh/id_ed25519.pub
```

এতে আপনার Public Key দেখা যাবে।

সাধারণত এটি এমন কিছু দিয়ে শুরু হবে:

```text
ssh-ed25519 AAAA...
```

পুরো Public Key copy করতে হবে।

---

# GitHub-এ Public Key যুক্ত করা

এখন আপনার GitHub account-এ login করুন।

তারপর:

**GitHub → Settings → SSH and GPG keys**

এ যান।

এরপর:

**New SSH key**

এ click করুন।

তারপর:

### Title

আপনি যেকোনো meaningful নাম দিতে পারেন।

উদাহরণ:

```text
Personal Computer
```

### Key

এখানে আপনার copy করা **Public Key** paste করুন।

তারপর:

**Add SSH key**

এ click করুন।

এখন আপনার GitHub account-এর সাথে SSH Key যুক্ত হয়ে যাবে।

---

# SSH দিয়ে GitHub Repository Clone

এখন ধরুন GitHub-এ আপনার একটি repository আছে।

আপনি সেটি আপনার computer-এ আনতে চান।

GitHub repository-তে গিয়ে:

**Code → SSH**

select করুন।

তারপর SSH URL copy করুন।

এটি সাধারণত এমন হবে:

```text
git@github.com:username/repository.git
```

তারপর Terminal-এ যে folder-এর মধ্যে repository রাখতে চান সেখানে যান।

এরপর লিখুন:

```bash
git clone git@github.com:username/repository.git
```

তারপর **Enter** চাপুন।

---

# Passphrase চাইলে কী করবেন?

আপনি যদি SSH Key তৈরি করার সময় passphrase দিয়ে থাকেন, তাহলে প্রথমবার SSH ব্যবহার করার সময় আপনার কাছে passphrase চাইতে পারে।

সেক্ষেত্রে আপনি যে passphrase সেট করেছিলেন সেটি লিখবেন।

Authentication সফল হলে Git আপনার GitHub repository clone করতে শুরু করবে।

---

# পুরো Process এক নজরে

```text
1. SSH Key তৈরি করুন
        ↓
2. Public Key + Private Key তৈরি হবে
        ↓
3. Public Key GitHub-এ Add করুন
        ↓
4. Private Key আপনার Computer-এ থাকবে
        ↓
5. GitHub Repository-এর SSH URL Copy করুন
        ↓
6. git clone ব্যবহার করুন
        ↓
7. SSH-এর মাধ্যমে Authentication হবে
        ↓
8. GitHub-এর সাথে Securely কাজ করতে পারবেন
```

---

## গুরুত্বপূর্ণ বিষয়

### 🔐 Public Key

GitHub-এ add করা যায়।

### 🔒 Private Key

শুধু আপনার computer-এ থাকবে।

**Private Key কখনো কারও সাথে share করবেন না।**

### SSH-এর সুবিধা

- GitHub-এর সাথে secure authentication
- বারবার username/password দেওয়ার প্রয়োজন কমে যায়
- `clone`, `push`, `pull` ইত্যাদিতে SSH ব্যবহার করা যায়
- GitHub-এর সাথে কাজ করার জন্য একটি standard authentication method

---

## Short Revision Note

**SSH = Secure Shell**

SSH হলো এমন একটি protocol যা network-এর মাধ্যমে নিরাপদ communication ও authentication করতে সাহায্য করে।

GitHub-এর জন্য SSH ব্যবহার করলে মূলত:

**Public Key → GitHub-এ থাকে**

**Private Key → আপনার Computer-এ থাকে**

এই দুইটির মাধ্যমে আপনার computer এবং GitHub-এর মধ্যে authentication প্রতিষ্ঠিত হয়।

সবচেয়ে গুরুত্বপূর্ণ:

> **Public Key share করা যায়, কিন্তু Private Key কখনো share করা যাবে না।**
