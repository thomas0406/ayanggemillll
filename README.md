## 📔 PANDUAN LENGKAP DIARY WEB

Website diary digital dengan fitur upload foto dan musik yang responsif.

### 🚀 CARA MENJALANKAN

#### Opsi 1: Menggunakan Node.js (Recommended)
```powershell
npm install -g http-server
cd "d:\DIARY WEB"
http-server -p 8000
```

Buka browser: `http://localhost:8000`

#### Opsi 2: Menggunakan Python 3
```powershell
cd "d:\DIARY WEB"
python3 -m http.server 8000
```

Buka browser: `http://localhost:8000`

#### Opsi 3: Menggunakan Python 2
```powershell
cd "d:\DIARY WEB"
python -m SimpleHTTPServer 8000
```

Buka browser: `http://localhost:8000`

#### Opsi 4: Menggunakan PowerShell (Windows)
```powershell
cd "d:\DIARY WEB"
# Jalankan script PowerShell yang sudah disediakan
.\Start-Server.ps1
```

---

### 🔐 AKSES APLIKASI

#### 📱 Halaman Utama
**URL**: `http://localhost:8000` atau `http://localhost:8000/index.html`
- Ada 2 tombol: LOGIN ADMIN dan PENGUNJUNG

#### 🔒 Panel Admin
**Password Default**: `admin123`

**Di sini Anda dapat:**
- ✏️ Membuat entri diary baru
- 📝 Menulis judul (akan ditampilkan tebal & besar)
- 📅 Memilih tanggal
- 📄 Menulis deskripsi (tebal di tampilan public)
- 📷 Upload maksimal 2 foto
- 🎵 Upload file musik (opsional)
- ✏️ Edit entri yang sudah dibuat
- 🗑️ Hapus entri
- 💾 Export data sebagai backup JSON
- 📂 Import backup data
- 🔐 Mengubah password

**Cara akses**: Klik tombol "LOGIN ADMIN" → masukkan password → klik "LOGIN ADMIN"

#### 👁️ Panel Pengunjung
**URL**: Klik tombol "PENGUNJUNG" atau akses langsung `http://localhost:8000/diary-public.html`

**Fitur:**
- 📖 Baca semua entri diary
- 📷 Lihat foto (bisa di-fullscreen dengan klik gambar)
- 🎵 Dengarkan musik
- ⚠️ TIDAK bisa edit, hapus, atau upload

---

### 🎨 TEMA & DESAIN

- **Tema**: Glow Tech dengan warna cyan (#00e5ff) dan magenta (#ff00d0)
- **Background**: Animasi gradient dengan partikel kecil yang bergerak
- **Partikel Tombol**: Saat klik tombol, keluar partikel kecil yang berkilau
- **Responsive**: Optimal di HP, Tablet, dan Desktop

---

### 📱 RESPONSIVITAS

#### Breakpoint
- **Mobile (max-width: 480px)**: Layout single column, font lebih kecil
- **Tablet (480px - 768px)**: Grid 2 kolom
- **Desktop (768px+)**: Layout penuh

#### Gambar
- Otomatis menyesuaikan ukuran dengan layar
- Bisa fullscreen view
- Ratio tetap 16:9 untuk best viewing

---

### 💾 PENYIMPANAN DATA

Data disimpan di **localStorage** browser:
- Entri diary: Disimpan otomatis saat "SIMPAN ENTRI" diklik
- Password admin: Tersimpan di localStorage (default: admin123)
- Gambar & Audio: Dikonversi ke Base64 dan disimpan di localStorage

**Catatan**: Data akan hilang jika:
- Hapus browser cache/history
- Buat profile browser baru
- Gunakan private/incognito mode

**Untuk menjaga data**, gunakan fitur "EXPORT BACKUP" rutin!

---

### 🔄 BACKUP & RESTORE

#### Export Backup
1. Klik tombol "💾 EXPORT BACKUP" di panel admin
2. File JSON akan otomatis terunduh dengan nama `diary-backup-YYYY-MM-DD.json`

#### Import Backup
1. Klik tombol "📂 IMPORT BACKUP" di panel admin
2. Pilih file JSON backup yang sudah disimpan
3. Semua data akan di-restore

---

### 🔐 MENGUBAH PASSWORD

1. Login ke panel admin dengan password saat ini
2. Scroll ke bawah ke bagian "🔐 Atur Password Admin"
3. Masukkan password baru (minimal 6 karakter)
4. Konfirmasi password
5. Klik "💾 SIMPAN PASSWORD BARU"
6. System akan otomatis logout dan redirect ke halaman login

---

### 📱 AKSES DARI HP

#### Di Jaringan Lokal (WiFi sama)
1. Cari IP Address PC Anda:
   ```powershell
   ipconfig
   ```
   Cari IPv4 Address (biasanya `192.168.x.x`)

2. Di HP, buka browser dan akses:
   ```
   http://[IP_ADDRESS]:8000
   ```
   Contoh: `http://192.168.1.100:8000`

#### Catatan
- HP dan PC harus connect ke WiFi yang sama
- Port 8000 harus accessible (tidak di-block firewall)
- Untuk akses dari luar rumah, perlu setup networking yang lebih kompleks

---

### 🐛 TROUBLESHOOTING

#### "Cannot find module 'http-server'"
**Solusi**: Jalankan `npm install -g http-server` terlebih dahulu

#### "Port 8000 already in use"
**Solusi**: 
```powershell
# Gunakan port berbeda
http-server -p 8001
# atau kill process yang menggunakan port 8000
netstat -ano | findstr :8000
taskkill /PID [PID] /F
```

#### Data hilang setelah close browser
**Solusi**: Gunakan fitur "EXPORT BACKUP" untuk menjaga data

#### Gambar tidak muncul
**Solusi**: 
- Pastikan file format gambar supported (JPG, PNG, GIF, WebP)
- File size tidak lebih dari 5MB per gambar
- Clear browser cache dan refresh halaman

#### Musik tidak bisa diputar
**Solusi**:
- Format audio harus MP3 atau OGG
- File size tidak lebih dari 50MB
- Browser harus mendukung HTML5 audio

---

### 📋 FITUR YANG TERSEDIA

#### Panel Admin ✔️
- [x] Password protection
- [x] Form input: Judul, Tanggal, Deskripsi
- [x] Upload foto (max 2)
- [x] Upload musik
- [x] Edit entry
- [x] Delete entry
- [x] Export backup
- [x] Import backup
- [x] Ubah password
- [x] Logout

#### Panel Pengunjung ✔️
- [x] View semua entries
- [x] Lihat foto
- [x] Fullscreen view gambar
- [x] Play musik
- [x] Responsive design
- [x] Read-only (aman)

#### Design ✔️
- [x] Tema glow tech
- [x] Warna cyan & magenta
- [x] Partikel background kecil
- [x] Partikel tombol saat click
- [x] Responsive untuk HP & PC
- [x] Dark mode modern

---

### 📝 NOTES

- Password disimpan di localStorage, bukan server
- Semua data local, tidak ada cloud backup
- Browser cache harus di-clear jika mau reset semuanya
- Untuk production, gunakan database yang proper (bukan localStorage)

---

### 🆘 SUPPORT

Jika ada masalah:
1. Check console browser (F12 → Console)
2. Lihat error message yang muncul
3. Coba clear cache dan refresh
4. Coba di browser lain
5. Coba di device lain

---

**Selamat menggunakan Diary Web! 📔✨**
