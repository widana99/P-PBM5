![item 2 description](https://github.com/user-attachments/assets/3dc641d4-85af-4992-ac15-c75f721c95b8)

![item 3 description](https://github.com/user-attachments/assets/7ee20aa0-853e-4c18-b220-15764bc0e782)


## Struktur Aplikasi

### 1. `Item`  
Kelas model yang merepresentasikan data item dengan properti:  
- `id` (int)  
- `name` (String)  
- `description` (String) — deskripsi tambahan untuk tiap item.

---

### 2. `MyApp` (StatefulWidget)  
Merupakan root widget aplikasi.  
- Menyimpan state untuk item yang sedang dipilih (`_selectedItem`).  
- Mendefinisikan daftar item contoh (`_items`).  
- Mengelola navigasi dengan widget `Navigator` dan daftar `pages` yang berubah secara deklaratif berdasarkan item yang dipilih.

**Fungsi penting:**  
- `_selectItem(Item item)`: Menandai sebuah item sebagai item terpilih dan memperbarui state.  
- `_clearSelection()`: Menghapus item yang dipilih dan kembali ke halaman utama.

**Navigasi:**  
- Selalu menampilkan halaman `HomeScreen`.  
- Menampilkan halaman `DetailScreen` jika ada item yang dipilih.  
- Menangani aksi pop (back) untuk menghapus seleksi item dan kembali ke `HomeScreen`.

---

### 3. `HomeScreen` (StatelessWidget)  
Menampilkan daftar item dalam bentuk `ListView`.  
- Parameter:  
  - `items`: List data `Item`.  
  - `onItemSelected`: Callback yang dijalankan ketika item dipilih.  

**UI:**  
- `AppBar` dengan judul "Home".  
- List tile untuk setiap item dengan nama dan ID, serta ikon panah sebagai indikator bisa klik.  
- Ketika item ditekan, memicu `onItemSelected` untuk memilih item dan navigasi ke detail.

---

### 4. `DetailScreen` (StatelessWidget)  
Menampilkan detail dari item yang dipilih.  
- Parameter:  
  - `item`: Objek `Item` yang dipilih.  
  - `onBack`: Callback untuk aksi kembali ke halaman utama.

**UI:**  
- `AppBar` dengan judul dinamis sesuai nama item.  
- Menampilkan nama, ID, dan deskripsi item dengan style yang jelas dan terstruktur.  
- Tombol "Back to Home" untuk kembali ke `HomeScreen` dengan memicu `onBack`.

---

## Navigasi dengan Navigator 2.0

- Menggunakan widget `Navigator` dengan `pages` yang diatur secara deklaratif berdasarkan state.  
- Halaman detail hanya ditampilkan saat ada item yang dipilih.  
- Saat pengguna menekan tombol back, halaman detail hilang dan state seleksi di-reset.

---
