# 🧠 OCS01 Client Setup Guide

This guide walks you through building and running the `ocs01-test` client inside a Docker container, resolving common issues, and pushing your documentation to GitHub.

---

## 📦 1. Setting up the Docker Environment

```bash
# Run Docker container and mount code folder
sudo docker run -it -v $(pwd):/code rust:latest bash

# Change to working directory
cd /code
```

---

## ⚙️ 2. Building the Project

```bash
# Navigate to the cloned repo
cd /code

# Build in release mode
cargo build --release
```

If you see OpenSSL-related errors:

```bash
apt-get update && apt-get install -y pkg-config libssl-dev
```

Then try building again.

---

## 📁 3. Place Required Files in `release` Folder

Make sure the following JSON files exist in your `/code` directory:

* `wallet.json`
* `exec_interface.json`

Example content for `wallet.json`:

```json
{
  "priv": "C06oEo27KMjDjNzyrVxE1bhaCNdFOXyPkrLOSH2RXqM=",
  "address": "oct3tdtpV4Mz38U2my5iEPuunn1e9a91U3mFTZo6jRKyoXi"
}
```

Copy them into the release folder:

```bash
cp wallet.json ./target/release/
cp exec_interface.json ./target/release/
cd ./target/release/
```

---

## 🚀 4. Run the Program

```bash
./ocs01-test
```

You should now see a menu of options and your wallet balance.

---

## 📝 5. Record Full Terminal Session (Optional)

```bash
script full-session.log
# When finished
exit
```

This will save your entire terminal history to `full-session.log`

---

## 📤 6. Push to GitHub

### Initialize Git (if not already)

```bash
git init
git remote add origin https://github.com/Okon41/ocs01-client-guide.git
```

### Configure Your Identity

```bash
git config --global user.name "Okon41"
git config --global user.email "icecool914@gmail.com"
git config --global --add safe.directory /code
```

### Add & Commit

```bash
git add .
git commit -m "Initial commit of ocs01-client-guide"
```

### Push to GitHub

```bash
git branch -M main
git push -u origin main
```

If prompted, [generate a personal access token (PAT)](https://github.com/settings/tokens) and use that as your GitHub password (GitHub no longer supports account passwords over HTTPS).

---

## ✅ You're Done!

Your setup is live and working. You can now build, run, and edit the OCS01 test client, and all documentation is safely stored in your GitHub repo.

**Repo:** [github.com/Okon41/ocs01-client-guide](https://github.com/Okon41/ocs01-client-guide)

---

Let me know if you want a cleaner version or a README format!

