# Deep Link Navigation
![navigation_20 main](https://github.com/user-attachments/assets/6ab337c5-b56f-42d4-81ac-4b74e9efe02d)
- class HomeScreen extends StatelessWidget { ... }
  - Menampilkan daftar item
  - Menggunakan ListView.builder
- class DetailScreen extends StatelessWidget { ... }
  - Menampilkan info yang dipilih
  - Tombol back to home memanggil onBack() untuk kembali
![item 1](https://github.com/user-attachments/assets/d957278c-e772-47b9-a7ac-6c7c94cd8d36)
![item 2](https://github.com/user-attachments/assets/0c026d44-82b1-4740-8ea1-29708e7f2dc8)
![deep link setting main](https://github.com/user-attachments/assets/38a6a16a-9808-425d-9772-f217855816ab)
![deep link settings](https://github.com/user-attachments/assets/56966b1d-5364-49b6-a51b-26fcc00c01e1)

# Deep Linking Flutter App

Aplikasi Flutter sederhana yang menggunakan Navigator 2.0 dengan `RouterDelegate` dan `RouteInformationParser` untuk mengelola navigasi berbasis URL (deep linking). Aplikasi ini terdiri dari tiga halaman utama: Home, Detail, dan Settings.

---

## Penjelasan Widget dan Struktur Aplikasi

### 1. **Item**
Kelas model sederhana yang merepresentasikan data item dengan properti:
- `id` (int) : ID unik dari item.
- `name` (String) : Nama item.

---

### 2. **RoutePath**
Kelas yang merepresentasikan state dari navigasi aplikasi, terdiri dari:
- `isHome` : Menandakan halaman Home.
- `id` : ID item yang sedang ditampilkan pada halaman Detail (opsional).
- `isSettings` : Menandakan halaman Settings.

Memiliki konstruktor khusus:
- `RoutePath.home()` untuk halaman Home.
- `RoutePath.detail(int id)` untuk halaman Detail berdasarkan ID.
- `RoutePath.settings()` untuk halaman Settings.

---


### 3. **AppRouteInformationParser**
Merupakan parser yang mengubah URL menjadi objek `RoutePath` dan sebaliknya, mendukung deep linking dengan URL berikut:
- `/` → HomeScreen
- `/detail/:id` → DetailScreen untuk item dengan ID tertentu.
- `/settings` → SettingScreen

---

### 4. **AppRouterDelegate**
Router delegate utama yang mengelola stack halaman (`Navigator`) berdasarkan state aplikasi:
- Menyimpan state saat ini dengan variabel `_selectedItemId` dan `_showSettings`.
- Mengatur halaman yang tampil berdasarkan state tersebut.
- Fungsi utama:
  - `selectItem(int id)` untuk navigasi ke DetailScreen.
  - `goHome()` untuk kembali ke HomeScreen.
  - `goToSettings()` untuk pindah ke SettingScreen.
- Membuat `Navigator` dengan daftar `MaterialPage` sesuai dengan state saat ini.

---

### 5. **MyApp**
Widget utama aplikasi yang menggunakan `MaterialApp.router` dengan konfigurasi `routerDelegate` dan `routeInformationParser` dari kelas-kelas di atas.

---

### 6. **HomeScreen**
Halaman utama yang menampilkan daftar item dalam bentuk `ListView`.  
Fitur:
- Menampilkan daftar `Item` dengan nama dan ID.
- Tombol di AppBar untuk masuk ke Settings.
- Ketika item dipilih, memanggil callback `onItemSelected`.

---

### 7. **DetailScreen**
Halaman detail untuk menampilkan informasi sebuah item berdasarkan `id` yang dipilih.  
Fitur:
- Menampilkan nama dan ID item.
- Tombol untuk kembali ke halaman Home dengan memanggil callback `onBack`.

---

### 8. **SettingScreen**
Halaman pengaturan sederhana yang menampilkan teks statis sebagai placeholder.

---

## Cara Kerja Navigasi

- URL yang diakses akan di-parse oleh `AppRouteInformationParser` dan dikonversi menjadi `RoutePath`.
- `AppRouterDelegate` menggunakan `RoutePath` tersebut untuk mengatur halaman yang akan ditampilkan.
- Navigasi dapat dilakukan dengan:
  - Memilih item di HomeScreen → menuju DetailScreen.
  - Menekan tombol settings di HomeScreen → menuju SettingScreen.
  - Tombol back di DetailScreen atau navigasi pop akan kembali ke HomeScreen.
- URL juga akan diperbarui secara otomatis sesuai dengan halaman yang aktif (deep linking).
