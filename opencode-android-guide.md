# 📱 OpenCode + MiniMax M2.5 Free on Android
### Free AI Coding Assistant — Complete Setup Guide

> **Guide by [@GamingBurst007](https://youtube.com/@GamingBurst007)**  
> 📺 YouTube · 💬 Discord · 📸 Instagram — `@GamingBurst007`

---

## ✅ What You'll Have
- OpenCode running on your Android phone via Termux
- MiniMax M2.5 Free model — no credit card, no GPU needed
- Full AI coding assistant right in your terminal

---

## 📋 Requirements
- Android phone
- **Termux (GitHub Version)** — link in links section below
- Internet connection
- GitHub account *(optional — only needed if you want to push code to GitHub)*

---

## 🚀 Installation (First Time Only)

### Step 1 — Install Termux
1. Go to the link in the links section below
2. Download the latest APK — pick **arm64-v8a** for most phones
3. Install it

> ⚠️ **WARNING:** Do NOT use the Play Store version. It is outdated and broken.

---

### Step 2 — Set Up Termux
Open Termux and run these commands:
```bash
pkg update -y && pkg upgrade -y
pkg install proot-distro curl unzip ripgrep -y
```

---

### Step 3 — Allow Storage Access
```bash
termux-setup-storage
```
> Tap **Allow** on the popup that appears.

---

### Step 4 — Create Permanent Alpine Shortcut
```bash
echo 'alias alpine="proot-distro login alpine --bind /sdcard:/sdcard"' >> ~/.bashrc
source ~/.bashrc
```
> Now you can just type `alpine` to enter Alpine every time — no long command needed.

---

### Step 5 — Install Alpine Linux
```bash
proot-distro install alpine
alpine
```
> Your prompt changes to `localhost:~#`  
> Everything from this point runs **INSIDE Alpine**.

---

### Step 6 — Install Dependencies Inside Alpine
```bash
apk add curl bash libstdc++ libgcc
```

---

### Step 7 — Install OpenCode
```bash
curl -fsSL https://opencode.ai/install | bash
export PATH="$HOME/.opencode/bin:$PATH"
```

Make PATH permanent so it works every session:
```bash
echo 'export PATH="$HOME/.opencode/bin:$PATH"' >> ~/.bashrc
```

---

### Step 8 — Verify Installation
```bash
opencode --version
```
> ✅ Should show a version number like `1.x.xx`

---

### Step 9 — Get Your OpenCode Zen API Key
1. Go to **opencode.ai**
2. Click **Zen** → Login → create a free account
3. Go to **API Keys** → Create → name it anything → copy the key
4. Save it somewhere safe

---

### Step 10 — Connect MiniMax M2.5 Free
Launch OpenCode:
```bash
opencode
```

Inside OpenCode do this:
1. Type `/connect`
2. Select **opencode**
3. Open the link shown in your Android browser
4. Login → copy the API key shown
5. Paste it back in the terminal
6. Select **MiniMax M2.5 Free**

> ✅ Done! API key is saved forever. You never need to do `/connect` again.

---

## ⚡ Daily Startup
> Every time you open Termux — only 4 commands, under 1 minute

```bash
termux-wake-lock
alpine
cd /sdcard/Download/your-project-folder
opencode
```

---

## 📁 Navigating Folders

| What you want to do | Command |
|---|---|
| Go to a project in Downloads | `cd /sdcard/Download/example-folder` |
| Go to home directory | `cd ~` |
| Create a new project folder | `mkdir /sdcard/Download/my-project` |
| See what's in current folder | `ls` |
| See your current location | `pwd` |
| Delete a file | `rm filename.txt` |
| Delete a folder | `rm -rf foldername` |
| Copy a file | `cp file.txt /sdcard/Download/other-folder/` |
| Move or rename a file | `mv oldname.txt newname.txt` |
| Create an empty file | `touch filename.txt` |
| View contents of a file | `cat filename.txt` |
| Search for text inside files | `grep -r "search term" .` |

---

## 🔄 Switching Between Projects

```bash
/exit                              # exit OpenCode
cd /sdcard/Download/other-project  # go to new folder
opencode                           # launch again
```

---

## ❌ How to Exit / Turn Off

| What | How |
|---|---|
| Exit OpenCode | Press `Ctrl+C` or type `/exit` |
| Exit Alpine back to Termux | Type `exit` |
| Close everything | Just close the Termux app |

---

## 🔧 Troubleshooting

**`opencode: command not found`**
```bash
export PATH="$HOME/.opencode/bin:$PATH"
```

---

**`libstdc++ not found` error**
```bash
apk add libstdc++ libgcc
```

---

**`proot-distro should not be executed under PRoot`**
> You are already inside Alpine. Type `exit` first, then run the command from Termux.

---

**`/sdcard not accessible` inside Alpine**
```bash
# Exit Alpine first, then run in Termux:
termux-setup-storage
# Then re-enter Alpine:
alpine
```

---

**Android killed Termux in the background**
```bash
termux-wake-lock
alpine
cd /sdcard/Download/your-project
opencode
```
> 💡 Fix permanently: **Settings → Apps → Termux → Battery → Unrestricted**

---

**OpenCode freezes or crashes**
```bash
/exit
cd /sdcard/Download/your-project
opencode
```

---

## 📌 Key Things to Remember

- ✅ Always run `termux-wake-lock` before starting
- ✅ Termux must be the **GitHub version** — not Play Store
- ✅ Always `cd` to your project folder **before** typing `opencode`
- ✅ `/connect` only needed once — API key saved forever
- ✅ Type `alpine` to enter Alpine (shortcut we created in Step 4)
- ✅ MiniMax M2.5 Free has soft limits — if slow, just wait a moment
- ✅ Use `/exit` to cleanly quit OpenCode

---

## ⚡ Quick Reference

```bash
# Daily startup
termux-wake-lock
alpine
cd /sdcard/Download/your-project
opencode

# Switch project
/exit
cd /sdcard/Download/other-project
opencode
```

---

## 🐙 Optional — GitHub Integration
> Skip this section if you don't need to push code to GitHub

### Install git and GitHub CLI
```bash
apk add git github-cli
```

### Set Up Git Identity (one time only)
```bash
git config --global user.name "YourGitHubUsername"
git config --global user.email "your@email.com"
```

### Login to GitHub (one time only)
```bash
gh auth login
```

Answer every question like this:

| Question | Answer |
|---|---|
| Where do you use GitHub? | **GitHub.com** |
| Preferred protocol? | **HTTPS** |
| Authenticate Git with GitHub credentials? | **Y** |
| How to authenticate? | **Login with a web browser** |

Then:
1. **Copy** the one-time code shown (e.g. `XXXX-XXXX`)
2. Press **Enter**
3. Open **https://github.com/login/device** in your Android browser
4. Paste the code → tap **Authorize**

> ✅ Done! GitHub login saved forever.

---

### First Time Setting Up a Project with GitHub
```bash
cd /sdcard/Download/your-project
git init
git remote add origin https://github.com/YourUsername/your-repo.git
git add .
git commit -m "Initial commit"
git push origin main --force
```

### Upload Changes to GitHub (Every Time)
```bash
git add .
git commit -m "describe your changes here"
git push
```

### Override Old Files on GitHub
```bash
git add .
git commit -m "Update all files"
git push origin main --force
```

> If branch name error, try `master` instead of `main`:
> ```bash
> git push origin master --force
> ```

### Other Useful Git Commands
```bash
git status        # check what changed before uploading
git log --oneline # see upload history
```

### Switch GitHub Account
```bash
gh auth logout
gh auth login
```

---

## 🔗 Links

| | |
|---|---|
| OpenCode | https://opencode.ai |
| OpenCode Docs | https://opencode.ai/docs |
| Termux GitHub | https://github.com/termux/termux-app/releases |

---

## 👤 Credits

**Guide by [@GamingBurst007](https://youtube.com/@GamingBurst007)**

| Platform | Link |
|---|---|
| 📺 YouTube | youtube.com/@GamingBurst007 |
| 💬 Discord | discord.gg/GamingBurst007 |
| 📸 Instagram | instagram.com/GamingBurst007 |

---

*Android Edition · May 2026*
