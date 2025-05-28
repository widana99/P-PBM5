# nested_navigation
# Nested Navigation

![nested nav main](https://github.com/user-attachments/assets/4fe9a33e-afa8-4634-a5cd-d2a06298fca3)

![setup flow](https://github.com/user-attachments/assets/096c0778-b92a-4d79-8be5-e8e6b8536adf)

![connecting to device](https://github.com/user-attachments/assets/93e37c61-36a9-455e-a005-383875555722)

![connection configuration](https://github.com/user-attachments/assets/f4ce7c51-44ce-434d-8e69-d5263451a771)

![configure device](https://github.com/user-attachments/assets/24d23c97-7b83-4a8f-a90b-bd860751e593)

# Nested Navigation Flutter App

Aplikasi Flutter sederhana yang memperlihatkan penggunaan **nested navigation** dengan Navigator di dalam sebuah flow setup multi-step.

---

## Struktur Aplikasi

### 1. MyApp
- Widget utama aplikasi.
- Menggunakan `MaterialApp` dengan tema dasar dan menunjuk ke `HomeScreen` sebagai halaman awal.

### 2. HomeScreen
- Halaman utama yang menampilkan teks sambutan dan tombol untuk memulai setup flow.
- Ketika tombol ditekan, akan membuka layar `SetupFlowScreen` menggunakan `Navigator.push`.

### 3. SetupFlowScreen
- Halaman utama untuk flow setup perangkat.
- Menggunakan **nested Navigator** (Navigator di dalam layar ini) agar flow setup bisa memiliki rute dan stack sendiri tanpa mempengaruhi navigator utama aplikasi.
- Memiliki key navigator tersendiri (`_navigatorKey`) untuk kontrol navigasi internal.

#### Nested Navigator Routes:
- `'find_devices'` — Halaman pencarian perangkat (`FindDevicesScreen`).
- `'connect_device'` — Halaman untuk menghubungkan perangkat (`ConnectDeviceScreen`).
- `'configure_device'` — Halaman konfigurasi perangkat (`DeviceConfigurationScreen`).

Navigasi antar halaman ini dilakukan dengan `pushNamed` pada navigator bersarang.

### 4. FindDevicesScreen
- Layar pertama di flow setup.
- Menampilkan status "Finding Devices..." dan tombol "Device Found".
- Ketika tombol ditekan, memanggil callback `onDeviceFound` yang memicu navigasi ke layar berikutnya: `connect_device`.

### 5. ConnectDeviceScreen
- Layar kedua di flow setup.
- Menampilkan status "Connecting to Device..." dan tombol untuk lanjut ke konfigurasi.
- Ada juga tombol "Back" untuk kembali ke layar sebelumnya (`find_devices`).

### 6. DeviceConfigurationScreen
- Layar terakhir di flow setup.
- Menampilkan opsi konfigurasi perangkat.
- Tombol "Complete Setup" akan memanggil callback `onSetupComplete` yang akan menutup seluruh flow setup dan kembali ke `HomeScreen`.
- Tombol "Back" kembali ke layar sebelumnya (`connect_device`).

---

## Navigasi Bersarang

- Setup flow menggunakan nested navigator agar flow setup bisa memiliki stack sendiri tanpa mengganggu navigator utama aplikasi.
- Nested navigator ini diatur menggunakan key `_navigatorKey`.
- Penggunaan nested navigator membuat flow multi-step seperti setup perangkat menjadi terisolasi dan mudah dikendalikan.

---

## Cara Menggunakan

1. Jalankan aplikasi.
2. Pada halaman utama (Home), tekan tombol **Start Setup Flow**.
3. Ikuti flow setup dengan menekan tombol "Device Found", "Proceed to Configuration", dan "Complete Setup".
4. Flow setup dapat menggunakan tombol Back untuk kembali antar langkah, dan tombol kembali di app bar untuk keluar dari flow setup.

---

## Teknologi

- Flutter
- Dart
- Navigator 1.0 API dengan `Navigator`, `pushNamed`, dan `MaterialPageRoute`
