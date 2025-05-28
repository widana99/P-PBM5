# Flutter Deep Linking and Custom Routing Demo

## Deskripsi
Proyek ini merupakan implementasi contoh **deep linking** dan **custom routing** menggunakan **Navigator 2.0** di Flutter. Dengan menggunakan `RouterDelegate` dan `RouteInformationParser`, aplikasi ini mampu mengelola navigasi berdasarkan URL, memungkinkan pengguna untuk membuka halaman tertentu melalui tautan langsung (deep link).

## Fitur
- Navigasi dinamis berdasarkan URL.
- Halaman Home yang menampilkan daftar item.
- Halaman Detail yang menampilkan informasi berdasarkan ID item.
- Halaman Settings.
- Dukungan deep linking seperti:
  - `/` → Home
  - `/detail/{id}` → Detail halaman berdasarkan ID
  - `/settings` → Halaman Settings

## Struktur Kode
- **RoutePath**  
  Mendefinisikan tipe rute yang digunakan dalam aplikasi (home, detail, settings).

- **AppRouteInformationParser**  
  Mengurai URL menjadi objek `RoutePath` dan sebaliknya, memungkinkan aplikasi memahami dan memulihkan state berdasarkan URL.

- **AppRouterDelegate**  
  Mengelola state navigasi dan membangun tumpukan halaman (`pages`) sesuai kondisi aplikasi.

- **UI (HomeScreen, DetailScreen, SettingScreen)**  
  Menampilkan antarmuka pengguna dan mengirimkan event navigasi ke `AppRouterDelegate`.

## Tujuan Praktikum
Praktikum ini bertujuan untuk memahami dan mengimplementasikan:
- Konsep **Navigator 2.0** di Flutter.
- Deep linking dan parsing URL untuk navigasi aplikasi.
- Pemisahan logika navigasi dan tampilan UI.
- Penggunaan `RouterDelegate` dan `RouteInformationParser` untuk kontrol routing yang lebih fleksibel dan kuat dibanding Navigator 1.0.

## Cara Menjalankan
1. Pastikan Flutter SDK sudah terpasang dan terkonfigurasi.
2. Clone repositori ini atau salin kode sumber ke proyek Flutter baru.
3. Jalankan perintah berikut di terminal pada folder proyek:
   ```bash
   flutter pub get
   flutter run
