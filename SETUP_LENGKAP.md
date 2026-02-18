# 📔 DIARY WEB SETUP LENGKAP

## 1. CEK INSTALL PYTHON ATAU NODE.JS

### Jika belum install, download di:
- **Python**: https://www.python.org/downloads/ (Recommended)
- **Node.js**: https://nodejs.org/

### Saat install Python:
- ✅ Centang "Add Python to PATH"
- ✅ Pilih "Install for all users"

---

## 2. JALANKAN SERVER

Pilih salah satu sesuai apa yang terinstall:

### A. Jika Punya Python ✔️
```powershell
cd "d:\DIARY WEB"
python -m http.server 8000
```

Atau:
```powershell
python3 -m http.server 8000
```

### B. Jika Punya Node.js ✔️
```powershell
cd "d:\DIARY WEB"
npx http-server -p 8000
```

Atau (after npm install):
```powershell
npm install -g http-server
http-server -p 8000
```

---

## 3. BUKA BROWSER

Setelah console menunjukkan "Server running on..." atau "http://localhost:8000":

1. Buka browser (Chrome, Firefox, Edge, Safari)
2. Ketik: **http://localhost:8000**
3. Enter

---

## 4. PERTAMA KALI LOGIN

- Klik **"🔒 LOGIN ADMIN"**
- Masukkan password: **admin123**
- Klik **"🔒 LOGIN ADMIN"**

---

## 5. BUAT ENTRY PERTAMA

1. Isi "📝 Judul" (misal: "Hari Pertamaku")
2. Pilih "📅 Tanggal" (default hari ini)
3. Tulis "📄 Deskripsi" (cerita Anda)
4. Upload "🖼️ Foto" (optional, max 2)
5. Upload "🎵 Musik" (optional)
6. Klik **"💾 SIMPAN ENTRI"**

---

## 6. LIHAT DARI PENGUNJUNG

1. Back ke halaman utama
2. Klik **"👁️ PENGUNJUNG"**
3. Baca entri yang sudah dibuat
4. Klik gambar untuk lihat full screen
5. Play musik di audio player

---

## 7. AKSES DARI HP

### HP & PC di WiFi Sama:

1. Di PC, buka PowerShell:
```powershell
ipconfig
```

2. Cari "IPv4 Address" (misal: 192.168.1.100)

3. Di HP, buka browser:
```
http://192.168.1.100:8000
```

---

## 8. BACKUP DATA ANDA

Penting! Data tersimpan di browser, bukan cloud.

**Setiap 1-2 minggu:**
1. Login admin
2. Scroll ke "⚙️ Backup Data"
3. Klik "💾 EXPORT BACKUP"
4. Simpan file JSON di tempat aman

---

## 9. RESTORE DATA

Jika data hilang atau switch device:

1. Login admin
2. Scroll ke "⚙️ Backup Data"
3. Klik "📂 IMPORT BACKUP"
4. Pilih file JSON yang tersimpan
5. Data akan di-restore

---

## 10. UBAH PASSWORD

Setelah login admin:

1. Scroll ke "🔐 Atur Password Admin"
2. Masukkan password baru (min. 6 karakter)
3. Konfirmasi password
4. Klik "💾 SIMPAN PASSWORD BARU"
5. System otomatis logout

---

## ❌ JIKA ADA ERROR

### Error: "python is not recognized"
```powershell
# Cek apakah Python terinstall
python --version

# Jika error, download di https://www.python.org/downloads/
# Ingat centang "Add Python to PATH"
```

### Error: "Port 8000 already in use"
```powershell
# Gunakan port lain
python -m http.server 8001
# Buka: http://localhost:8001
```

### Error: "Data tidak muncul"
1. Clear browser cache (Ctrl+Shift+Delete)
2. Refresh halaman (F5)
3. Coba incognito mode (Ctrl+Shift+N)

### Error: "Foto tidak upload"
- Max size: 5MB per gambar
- Format: JPG, PNG, GIF, WebP
- Total max: 2 foto

### Error: "Musik tidak bisa diputar"
- Format: MP3, OGG, WAV
- Max size: 50MB
- Ketengan: Beberapa browser block auto-play

---

## 📋 TIPS & TRIK

### Clear Semua Data
```javascript
// Buka Developer Tools (F12) → Console
localStorage.clear();
// Refresh halaman
```

### Setup Password Baru
```javascript
// Buka Developer Tools → Console
localStorage.setItem('adminPassword', 'password-baru-anda');
```

### Cek Semua Entry
```javascript
// Buka Developer Tools → Console
console.log(JSON.parse(localStorage.getItem('diaryEntries')));
```

---

## 🎉 SELESAI!

Sekarang Anda siap menggunakan Diary Web. Happy journaling! 📔✨
