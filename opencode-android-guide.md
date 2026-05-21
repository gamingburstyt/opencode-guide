📱 OpenCode + MiniMax M2.5 Free on Android

Free AI Coding Assistant — Complete Setup Guide

> Guide by @GamingBurst007
📺 YouTube — @GamingBurst007




---

✅ What You'll Have

OpenCode running on your Android phone via Termux

MiniMax M2.5 Free model — no credit card, no GPU needed

Full AI coding assistant right in your terminal



---

📋 Requirements

Android phone

Termux (GitHub Version) — link in links section below

Internet connection

GitHub account (optional — only needed if you want to push code to GitHub)



---

> 💡 Quick Guide — Where to run commands:

🟡 Termux — run in Termux directly after opening the app

🔵 Alpine — run after typing alpine to enter Alpine

🟢 Debian — run after typing debian to enter Debian





---

🚀 Installation (First Time Only)

Step 1 — Install Termux

1. Go to the link in the links section below


2. Download the latest APK — pick arm64-v8a for most phones


3. Install it



> ⚠️ WARNING: Do NOT use the Play Store version. It is outdated and broken.




---

Step 2 — Set Up Termux

> 🟡 Run in Termux



pkg update -y && pkg upgrade -y
pkg install proot-distro curl unzip ripgrep -y


---

Step 3 — Allow Storage Access

> 🟡 Run in Termux



termux-setup-storage

> Tap Allow on the popup that appears.




---

🟢 Method 1 — Alpine Linux (Lightweight)

> 💡 Alpine is smaller and lighter, but some users may get OpenCode crashes or libc-related issues.
If Alpine doesn't work properly on your device, scroll down to the Debian method.




---

Step 4 — Create Permanent Alpine Shortcut

> 🟡 Run in Termux



echo 'alias alpine="proot-distro login alpine --bind /sdcard:/sdcard"' >> ~/.bashrc
source ~/.bashrc

> Now you can just type alpine to enter Alpine every time — no long command needed.




---

Step 5 — Install Alpine Linux

> 🟡 Run in Termux



proot-distro install alpine
alpine

> Your prompt changes to localhost:~#
Everything from this point runs INSIDE Alpine.




---

Step 6 — Install Dependencies Inside Alpine

> 🔵 Run in Alpine



apk add curl bash libstdc++ libgcc


---

Step 7 — Install OpenCode

> 🔵 Run in Alpine



curl -fsSL https://opencode.ai/install | bash
export PATH="$HOME/.opencode/bin:$PATH"

Make PATH permanent so it works every session:

echo 'export PATH="$HOME/.opencode/bin:$PATH"' >> ~/.bashrc


---

Step 8 — Verify Installation

> 🔵 Run in Alpine



opencode --version

> ✅ Should show a version number like 1.x.xx




---

🟢 If Alpine Doesn't Work — Use Debian (Recommended)

> ⚠️ Some devices may get errors like:

gnu_get_libc_version

OpenCode crashes/freezes

Bun/Node native module issues

npm install failures


This happens because Alpine uses musl libc, while many modern tools expect glibc.

Debian is currently the most stable OpenCode setup for Android.




---

Step 9 — Create Permanent Debian Shortcut

> 🟡 Run in Termux



echo 'alias debian="proot-distro login debian --bind /sdcard:/sdcard"' >> ~/.bashrc
source ~/.bashrc

> ✅ Now you can just type debian anytime to enter Debian.




---

Step 10 — Install Debian Linux

> 🟡 Run in Termux



proot-distro install debian
debian

> Your prompt changes to something like:



root@localhost:~#

> Everything from this point runs INSIDE Debian.




---

Step 11 — Install Dependencies Inside Debian

> 🟢 Run in Debian



apt update && apt upgrade -y
apt install curl bash git build-essential -y


---

Step 12 — Install OpenCode

> 🟢 Run in Debian



curl -fsSL https://opencode.ai/install | bash
export PATH="$HOME/.opencode/bin:$PATH"

Make PATH permanent:

echo 'export PATH="$HOME/.opencode/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc


---

Step 13 — Verify Installation

> 🟢 Run in Debian



opencode --version

> ✅ Should show a version number like 1.x.xx




---

🧠 Alpine vs Debian — Which Should You Use?

	Alpine	Debian

Size	Smaller	Bigger
Speed	Slightly faster	Slightly slower
OpenCode compatibility	⚠️ Mixed	✅ Best
Native module support	⚠️ Can break	✅ Stable
Recommended for beginners	❌ Not really	✅ Yes


> 💡 Recommendation:
Try Alpine first if you want the lightest setup.
If you get weird crashes or libc errors, switch to Debian and stay there.




---

Step 14 — Get Your OpenCode Zen API Key

1. Go to opencode.ai


2. Click Zen → Login → create a free account


3. Go to API Keys → Create → name it anything → copy the key


4. Save it somewhere safe




---

Step 15 — Connect MiniMax M2.5 Free

> 🔵 Run in Alpine
OR
🟢 Run in Debian



opencode

Inside OpenCode do this:

1. Type /connect


2. Select opencode


3. Paste your Zen API key when prompted


4. Select MiniMax M2.5 Free as your model



> ✅ Done! API key is saved forever. You never need to do /connect again.




---

⚡ Daily Startup

> Every time you open Termux — under 1 minute



🟡 Termux — Prevent Android from killing Termux in the background

termux-wake-lock


---

⚡ Alpine Daily Startup

🟡 Termux

alpine

🔵 Alpine

cd /sdcard/Download/your-project-folder
opencode


---

⚡ Debian Daily Startup

🟡 Termux

debian

🟢 Debian

cd /sdcard/Download/your-project-folder
opencode


---

📁 Navigating Folders

> 🔵 Alpine / 🟢 Debian



What you want to do	Command

Go to a project in Downloads	cd /sdcard/Download/example-folder
Go to home directory	cd ~
Create a new project folder	mkdir /sdcard/Download/my-project
See what's in current folder	ls
See your current location	pwd
Delete a file	rm filename.txt
Delete a folder	rm -rf foldername
Copy a file	cp file.txt /sdcard/Download/other-folder/
Move or rename a file	mv oldname.txt newname.txt
Create an empty file	touch filename.txt
View contents of a file	cat filename.txt
Search for text inside files	grep -r "search term" .



---

🔄 Switching Between Projects

> 🔵 Alpine / 🟢 Debian



/exit
cd /sdcard/Download/other-project
opencode


---

❌ How to Exit / Turn Off

What	How

Exit OpenCode	Press Ctrl+C or type /exit
Exit Alpine/Debian back to Termux	Type exit
Close everything	Just close the Termux app



---

🌐 Testing Your Project in Browser (Optional)

Alpine

> 🔵 Run in Alpine



Install once:

apk add nodejs npm tmux


---

Debian

> 🟢 Run in Debian



Install once:

apt install nodejs npm tmux -y


---

Start Your Dev Server

> 🔵 Alpine / 🟢 Debian



cd /sdcard/Download/your-project
npm install
npm run dev

> 📱 Open the Network URL shown (e.g. http://192.168.x.x:5173) in your Android browser — not the localhost one.




---

Keep Server Running in Background

> 🔵 Alpine / 🟢 Debian



tmux new-session -s dev
npm run dev
# Press Ctrl+B then D to detach
# Come back anytime with: tmux attach -t dev


---

🔧 Troubleshooting

opencode: command not found

> 🔵 Alpine / 🟢 Debian



export PATH="$HOME/.opencode/bin:$PATH"


---

gnu_get_libc_version error

> ❌ Alpine libc compatibility issue



> 🟡 Exit Alpine:



exit

> 🟡 Then switch to Debian:



proot-distro install debian
debian


---

proot-distro should not be executed under PRoot

> You are already inside Alpine/Debian. Type exit first to go back to Termux, then run the command again.




---

/sdcard not accessible

> 🟡 Run in Termux



termux-setup-storage

Then re-enter Alpine or Debian.


---

Android killed Termux in the background

> 🟡 Run in Termux



termux-wake-lock

> 💡 Fix permanently:
Settings → Apps → Termux → Battery → Unrestricted




---

npm run dev says cannot find package.json`

> You are in the wrong folder.



ls /sdcard/Download/
cd /sdcard/Download/your-project
npm run dev


---

npm install timeout / Rollup native module errors

> More common on Alpine.



> 🟢 Debian is recommended for Node/Vite projects.



Inside your project:

rm -rf node_modules package-lock.json
npm install

If using GitHub Actions:

git add package-lock.json
git commit -m "add lock file"
git push


---

📌 Key Things to Remember

✅ Always run termux-wake-lock before starting

✅ Use the GitHub version of Termux — not Play Store

✅ alpine = Alpine Linux

✅ debian = Debian Linux

✅ Debian is the most stable option for OpenCode

✅ Always cd into your project folder before opencode

✅ /connect only needed once

✅ Use the Network URL — not localhost — in browser



---

⚡ Quick Reference

# 🟡 Termux
termux-wake-lock

# Alpine
alpine

# Debian
debian

# Inside Alpine/Debian
cd /sdcard/Download/your-project
opencode

# Switch project
/exit
cd /sdcard/Download/other-project
opencode


---

🔗 Links

	

[OpenCode](https://opencode.ai?utm_source=chatgpt.com)	https://opencode.ai
[OpenCode Docs](https://opencode.ai/docs?utm_source=chatgpt.com)	https://opencode.ai/docs
[Termux GitHub Releases](https://github.com/termux/termux-app/releases?utm_source=chatgpt.com)	https://github.com/termux/termux-app/releases
[NVIDIA NIM](https://build.nvidia.com?utm_source=chatgpt.com)	https://build.nvidia.com



---

👤 Credits

Guide by @GamingBurst007

Platform	Link

📺 YouTube	youtube.com/@GamingBurst007



---

> 💬 Have a question? Drop it in the comments.

👍 If this helped you — Like, Share & Subscribe for more useful videos!




---

Android Edition · May 2026
