# ⚙️ AutoScript VPN ⚙️

## 📤 Fitur Utama 📤
- ▶️ All in One Port 443 TLS dan 80 Non-TLS
- ▶️ Mendukung VMess, VLess dan Trojan [WebSocket]
- ▶️ Manajemen pengguna tanpa mengganggu aktivitas pengguna lain
- 🚀 Tidak membutuhkan restart berulang-ulang untuk setiap tindakan (create, edit, renew maupun delete akun)
- ▶️ Tanpa Log Xray
- 🚀 Server tidak perlu terus-menerus membaca file log yang menyebabkan kinerja server menurun 
- ▶️ Menggunakan Database untuk penyimpanan akun

## 📤 Fitur Pendukung 📤
### ▶️ Pembatasan Koneksi
- 🛡 Limit IP yang bisa diatur per akun
- 🛡 Suspend otomatis untuk multi login
- 🛡 Un-suspend yang bisa diatur otomatis atau manual

### ▶️ Manajemen Kuota
- 🛡 Limit kuota bisa diatur per akun
- 🛡 Track penggunaan kuota
- 🛡 Auto disconnect jika kuota sudah terlampaui

### ▶️ Manajemen Domain
- 🛡 Kemampuan untuk mengganti domain dengan mudah
- 🛡 Issue sertifikat otomatis setelah penggantian domain

### ▶️ Backup Restore
- 🛡 Backup otomatis via telegram yang bisa diatur
- 🛡 Restore menggunakan direct download URL

## 📤 Server yang didukung 📤
- ▶️ Ubuntu 22.04 dan 24.04
- ▶️ Ram minimal 512Mb
- 🚀 inisial ram yang dibutuhkan ketika autoscript sudah terpasang sekitar 120Mb saja [*sudah termasuk system dll]

## 💬 Tanya jawab
**👀 Apa ada trial?**  
🎙 Ada, cukup jalankan command installasi, maka trial akan otomatis berjalan

**👀 Kenapa ram yang dibutuhkan sangat kecil?**  
🎙 AutoScript yang saya buat memprioritaskan kecepatan dan efisiensi server, karena tidak membutuhkan pembacaan log secara terus menerus, xray tidak terus mencatat log yang tidak diperlukan. dan ada beberapa optimasi lainnya

**👀 Apa ada rencana untuk mendukung SSH?**  
🎙 tentunya ada, tetapi tidak dalam waktu dekat ini. Karena saya ingin menambah dan melengkapi fitur pendukung untuk xray

## 🧲 Installasi
```bash
wget "https://raw.githubusercontent.com/vpnix/Autoscript/refs/heads/main/install" && chmod +x install && ./install
```

## 💳 Contact Person
- 📱 Telegram: [@vpnix_net](https://t.me/vpnix_net)
- 📱 YouTube: [https://youtu.be/ZP4N5Ehb5jw](https://youtu.be/ZP4N5Ehb5jw)
