# ⚙️ AutoScript VPN ⚙️

## 📤 Main Features 📤
- ▶️ All in One Port 443 TLS and 80 Non-TLS
- ▶️ Supports VMess, VLess and Trojan [WebSocket]
- ▶️ User management without disrupting other users' activities
- 🚀 No repeated restarts required for every action (create, edit, renew or delete accounts)
- ▶️ No Xray Logging
- 🚀 Server doesn't need to continuously read log files which causes server performance to decrease
- ▶️ Uses Database for account storage

## 📤 Supporting Features 📤
### ▶️ Connection Limitations
- 🛡 IP limit that can be set per account
- 🛡 Automatic suspension for multi-login
- 🛡 Un-suspend that can be set automatically or manually

### ▶️ Quota Management
- 🛡 Quota limit can be set per account
- 🛡 Track quota usage
- 🛡 Auto disconnect if quota is exceeded

### ▶️ Domain Management
- 🛡 Ability to change domains easily
- 🛡 Automatic certificate issuance after domain change

### ▶️ Backup & Restore
- 🛡 Automatic backup via Telegram that can be configured
- 🛡 Restore using direct download URL

## 📤 Supported Servers 📤
- ▶️ Ubuntu 22.04 and 24.04
- ▶️ Minimum RAM: 512MB
- 🚀 Initial RAM required when autoscript is installed is only about 120MB [*including system, etc.]

## 💬 FAQ
**👀 Is there a trial?**  
🎙 Yes, just run the installation command, and the trial will automatically run

**👀 Why is the required RAM so small?**  
🎙 The AutoScript I created prioritizes server speed and efficiency, as it doesn't require continuous log reading, Xray doesn't continuously record unnecessary logs, and there are several other optimizations

**👀 Are there plans to support SSH?**  
🎙 Certainly, but not in the near future. I want to add and complete supporting features for Xray first

## 🧲 Installation
```bash
wget "https://raw.githubusercontent.com/vpnix/Autoscript/refs/heads/main/install" && chmod +x install && ./install
```

## 💳 Contact Person
- 📱 Telegram: [@vpnix_net](https://t.me/vpnix_net)
- 📱 YouTube: [https://youtu.be/ZP4N5Ehb5jw](https://youtu.be/ZP4N5Ehb5jw)
