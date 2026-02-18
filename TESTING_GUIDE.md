# 🧪 PANDUAN TESTING UPLOAD GAMBAR

## ✅ Langkah Testing

### 1. CLEAR DATA LAMA (Jika perlu fresh start)
```
Buka Developer Tools: F12 (Windows/Linux) atau Cmd+Option+I (Mac)
→ Console tab
→ Paste: localStorage.clear()
→ Press Enter
```

### 2. TEST UPLOAD DI ADMIN PANEL

**Langkah:**
1. Buka: `diary-admin.html`
2. Login dengan password admin
3. Isi form:
   - Judul: "Test Foto"
   - Tanggal: Pilih hari ini
   - Deskripsi: "Testing upload gambar"
   - 📷 Upload 2 foto (gunakan foto HD untuk test)
4. Klik "💾 SIMPAN ENTRI"

**Pengecekan:**
- ✓ Toast notification muncul: "✅ Entri berhasil disimpan! (X.XXmb)"
- ✓ Gambar muncul di preview form (jika ada foto)
- ✓ Entri muncul di "📚 Entri Anda" section dengan thumbnail gambar

### 3. VERIFIKASI DI CONSOLE

```javascript
// Buka Console (F12 → Console tab)

// Check data tersimpan:
JSON.parse(localStorage.getItem('diaryEntries')).length
// Seharusnya menunjukkan: 1 (untuk 1 entry)

// Check entry pertama:
let entry = JSON.parse(localStorage.getItem('diaryEntries'))[0];
entry.title   // Seharusnya: "Test Foto"
entry.images  // Seharusnya: object dengan keys "1" dan "2"

// Check ukuran gambar yang tersimpan:
Object.keys(entry.images).length  // Seharusnya: 2
Object.values(entry.images)[0].length  // Panjang base64 string

// Debug info:
'Jumlah gambar: ' + Object.keys(entry.images).length + 
', Ukuran entry: ' + JSON.stringify(entry).length + ' bytes'
```

### 4. TEST PUBLIC PAGE

**Langkah:**
1. Buka tab baru: `diary-public.html`
2. Refresh halaman (Ctrl+F5 untuk hard refresh)

**Pengecekan:**
- ✓ Entry "Test Foto" muncul
- ✓ 2 thumbnail gambar visible dan dapat di-click
- ✓ Klik gambar → Modal view muncul dengan gambar full-size
- ✓ Deskripsi muncul dengan benar

### 5. MONITOR DEBUG LOGS

```
Saat upload, periksa Console untuk debug messages:
[DIARY DEBUG] Gambar yang disiapkan: Object { "1": "data:image/jpeg;...", "2": "..." }
[DIARY DEBUG] Jumlah gambar: 2
[DIARY DEBUG] Ukuran data yang akan disimpan (MB): X.XX
[DIARY DEBUG] ✓ Data berhasil disimpan ke localStorage
[DIARY DEBUG] ✓ Verifikasi: Gambar yang tersimpan dalam entry terakhir: 2
```

---

## 🚨 TROUBLESHOOTING

### Problem: "Gambar dapat dipilih tapi tidak muncul setelah simpan"

**Solusi:**
1. Buka Console (F12 → Console)
2. Check: `localStorage.getItem('diaryEntries')`
3. Jika kosong atau error → storage penuh
4. Solusi: Hapus entry lama
   ```javascript
   let entries = JSON.parse(localStorage.getItem('diaryEntries')) || [];
   entries = entries.slice(0, 5); // Simpan 5 entry terbaru saja
   localStorage.setItem('diaryEntries', JSON.stringify(entries));
   ```

### Problem: "⚠️ Data terlalu besar!"

**Penyebab:** 
- Foto terlalu besar (> 1200x1200)
- Sudah ada banyak entry dengan foto

**Solusi:**
1. Gunakan foto dengan ukuran lebih kecil/kompres sebelum upload
2. Hapus beberapa entry lama: `localStorage.removeItem('diaryEntries')`
3. Atau gunakan foto lower quality (sistem otomatis kompres ke JPEG quality 0.7)

### Problem: "❌ Storage penuh!"

**Penyebab:** localStorage penuh dengan data entry

**Solusi Long-term:**
```javascript
// Export: Admin Panel → "💾 EXPORT BACKUP"
// Hapus: localStorage.clear()
// Import: Admin Panel → "📂 IMPORT BACKUP"
```

### Problem: Di admin terlihat tapi public tidak

**Debug:**
1. Buka Developer Tools di KEDUA halaman (Admin + Public)
2. Admin Console: `JSON.parse(localStorage.getItem('diaryEntries'))[0].images`
3. Public Console: Sama dengan admin
4. Jika PUBLIC tidak ada → localStorage berbeda per domain
   - Pastikan buka file:// dengan domain yang sama
   - Atau gunakan local server (Python: `python -m http.server 8000`)

---

## 📊 BENCHMARK HASIL

Untuk reference, hasil yang diharapkan:

| Test | Expected Result | Status |
|------|-----------------|--------|
| Upload 1 Foto HD | ✓ Muncul, ~400-600KB | [ ] |
| Upload 2 Foto HD | ✓ Muncul, ~1-1.2MB | [ ] |
| Upload 5 Entries | ✓ Semua visible, ~3-5MB | [ ] |
| Public Display | ✓ Gambar visible, smooth | [ ] |
| Modal Zoom | ✓ Click gambar → Zoom | [ ] |
| Console Logs | ✓ Debug info clear | [ ] |

---

## 🎯 QUICK TEST COMMAND

Paste di Console untuk auto test:

```javascript
// Test 1: Check structure
console.log('=== STRUCTURE CHECK ===');
const entries = JSON.parse(localStorage.getItem('diaryEntries')) || [];
console.log('Total entries:', entries.length);
if (entries.length > 0) {
  console.log('Foto di entry pertama:', Object.keys(entries[0].images || {}).length);
  console.log('Ukuran storage:', (JSON.stringify(entries).length / 1024).toFixed(2), 'KB');
}

// Test 2: Validate images
console.log('=== IMAGE VALIDATION ===');
entries.forEach((e, i) => {
  const imgs = Object.values(e.images || {}).filter(x => !!x);
  console.log(`Entry ${i}: ${imgs.length} valid images`);
});
```

---

## ✨ TIPS OPTIMIZATION

### Reduce Size Further:
```javascript
// Jika ingin compression lebih agresif (quality 0.5):
// Buk diary-admin.html, cari:
// canvas.toBlob(..., 'image/jpeg', 0.7);
// Ubah 0.7 menjadi 0.5
```

### Batch Upload:
- Upload 1-2 entry per hari
- Jangan upload 20 entry sekaligus
- Monitor storage capacity

---

## 📞 REPORTING ISSUES

Jika masih ada problem:
1. Screenshot error message
2. Catat browser + OS
3. Check Console log (F12 → Console) untuk [DIARY DEBUG] messages
4. Buat file backup: Admin Panel → 💾 EXPORT BACKUP

---

**Last Updated:** February 2026
**Version:** 2.0 (With Image Compression)
