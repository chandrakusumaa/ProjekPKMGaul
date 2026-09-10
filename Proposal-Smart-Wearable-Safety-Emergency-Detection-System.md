# DOKUMEN PROPOSAL INOVASI PRODUK (PITCHING DOSEN PEMBIMBING)

**Judul Proyek:** Smart Wearable Safety & Emergency Detection System Berbasis Biometric, Kinematik, dan Voice Recognition
**Nama Mahasiswa:** [Nama Anda]
**NIM:** [NIM Anda]
**Program Studi / Jurusan:** Informatics / Teknik Informatika
**Instansi:** Universitas Pembangunan Nasional "Veteran" Jakarta
**Tanggal:** September 2026

---

## 1. Executive Summary & Latar Belakang

### 1.1 Latar Belakang Masalah

Tingkat kejahatan jalanan seperti pembegalan, perampasan, penculikan, hingga kecelakaan lalu lintas tunggal pada pengendara motor terus menjadi ancaman serius bagi masyarakat, khususnya pada jam-jam rawan dan area minim pengawasan.

Perangkat *smartwatch* komersial yang ada saat ini mayoritas berfokus pada *fitness tracking* dan kesehatan harian. Fitur *SOS/Emergency Call* pada *smartwatch* umum masih memiliki keterbatasan signifikan:

- **Manual Interventions:** Membutuhkan interaksi fisik manual yang konstan (misalnya menekan tombol beberapa kali), yang hampir tidak mungkin dilakukan saat korban ditodong, diserang tiba-tiba, atau mengalami benturan keras/pingsan.
- **Lack of Contextual Data:** Hanya mengirimkan pesan teks singkat berisi lokasi satu kali tanpa memberikan visibilitas situasi *real-time* (seperti kondisi fisik korban atau bukti percakapan di TKP).

### 1.2 Solusi Inovasi

Mengembangkan sebuah **Sistem Smart Wearable Khusus Keamanan & Deteksi Bahaya** (*Wearable Safety Device*) yang mengintegrasikan tiga moda pemicu darurat (*Multi-Modal Emergency Triggering*) berbasis **Hardware & Embedded AI/TinyML**, terhubung secara *real-time* ke *Companion Mobile Application* bagi kerabat/orang terdekat.

---

## 2. Rumusan Masalah & Tujuan Proyek

### 2.1 Rumusan Masalah

1. Bagaimana merancang sistem *wearable* yang mampu mendeteksi kondisi darurat secara otomatis melalui kombinasi respons fisiologis (*heart rate*, suhu) dan kinematik tubuh (*gyro/accelerometer*)?
2. Bagaimana mengimplementasikan modul *voice recognition* (*Keyword Spotting*) hemat daya pada perangkat *embedded* untuk mengenali teriakan/kata kunci darurat secara *offline*?
3. Bagaimana membangun mekanisme transmisi data *multi-sensor* (*GPS tracking*, *biometric feed*, dan *live audio streaming*) dari perangkat ke aplikasi pendamping kerabat tanpa mengalami *delay* tinggi?

### 2.2 Tujuan Penelitian / Pengembangan

1. Membangun prototipe perangkat *smartwatch safety* yang dapat mendeteksi bahaya (kecelakaan, pembegalan, penculikan) secara otomatis maupun terpicu suara.
2. Mengembangkan algoritma klasifikasi kondisi darurat (*Anomaly & Impact Detection*) menggunakan metode *Sensor Fusion*.
3. Menyediakan aplikasi pendamping (*penerima alert*) yang menyiarkan lokasi *real-time*, rekaman audio, serta indikator vital korban secara kontinu saat status bahaya aktif.

---

## 3. Aplikasi dan Integrasi Sistem

```
+-----------------------------------------------------------------------+
|                           SMART WEARABLE DEVICE                       |
|                                                                       |
|  [MAX30102 / MLX90614]  --> PPG & Suhu    -\                          |
|  [MPU6050 / Accelerometer] --> Kinematik   ---->  [ESP32 / MCU]       |
|  [INMP441 Digital Mic]  --> Voice / TinyML-/       | (Logic & Fusion) |
|  [Panic Button]         --> Manual Trigger         |                  |
+----------------------------------------------------+------------------+
                                                     |
                                        Wi-Fi / GSM / LTE (SIM7600)
                                                     |
                                                     v
+-----------------------------------------------------------------------+
|                      BACKEND / CLOUD SERVER (MQTT/WSS)                 |
+-----------------------------------------------------------------------+
                                                     |
                                            Real-time Push
                                                     |
                                                     v
+-----------------------------------------------------------------------+
|                     COMPANION APP (Orang Terdekat)                   |
|  - High-Priority Loud Alarm (Bypass Silent)                           |
|  - Live Map & GPS Tracking                                            |
|  - Real-Time Audio Broadcast / Recording                              |
|  - Live Biometric Feed (Heart Rate & Temp)                            |
+-----------------------------------------------------------------------+
```

---

## 4. Fitur Utama & Mekanisme Kerja

Sistem bekerja berdasarkan **Tiga Lapis Pemicu Bahaya (*Tri-Layer Trigger Mechanism*)**:

### A. Automatic Anomaly & Impact Trigger (Sensor Fusion)

- **Kombinasi Sensor:** PPG Heart Rate Sensor + IR Temperature Sensor + 6-Axis Gyro/Accelerometer.
- **Mekanisme:**
  - **Kecelakaan:** Pembacaan lonjakan akselerasi/guncangan ekstrem mendadak (*high G-force impact*) yang diikuti dengan ketidakberdayaan (posisi statis berulang).
  - **Pembegalan / Penyerangan:** Pembacaan lonjakan detak jantung (*heart rate spike*) mendadak akibat adrenalin tinggi yang dikombinasikan dengan pola gerakan tangan yang kacau/defensif.

### B. Offline Voice Recognition Trigger (TinyML)

- **Kombinasi Sensor:** Digital I2S Microphone + Microcontroller dengan TinyML / Edge Impulse model.
- **Mekanisme:**
  - Pengguna mendaftarkan sampel suara/kata kunci darurat (seperti "Tolong!", "Begal!", atau kata sandi khusus) saat konfigurasi awal.
  - Model Machine Learning ringan berjalan secara *offline* di mikroprosesor untuk mendeteksi frekuensi dan pola intonasi kata kunci secara presisi tanpa ketergantungan koneksi internet.

### C. Manual Panic Button Trigger

- **Mekanisme:** Tombol fisik dedikasi pada *casing* jam yang dirancang untuk ditekan (atau ditahan 2 detik) saat pengguna menyadari potensi ancaman sebelum kontak fisik terjadi.

---

## 5. Spesifikasi Teknis Hardware & Software

### 5.1 Perangkat Keras (Hardware Stack)

- **Main Microcontroller:** ESP32-S3 (Dual-core 32-bit LX7, mendukung akselerasi vector untuk AI/TinyML, Wi-Fi & Bluetooth Low Energy).
- **Biometric Sensor:** MAX30102 (Pulse Oximeter & Heart Rate) + MLX90614 / DS18B20 (Infrared Non-contact Temperature).
- **Kinematic Sensor:** MPU6050 / MPU9250 (3-Axis Gyroscope + 3-Axis Accelerometer).
- **Audio Input:** INMP441 Omnidirectional Digital I2S Microphone module.
- **GPS & Cellular Telemetry:** SIM7600E-H (4G LTE + GPS Module) untuk komunikasi data independen tanpa bergantung pada HP korban.
- **Power Management:** LiPo Battery 3.7V + TP4056 Charger Module + Voltage Regulator.

### 5.2 Perangkat Lunak & Arsitektur Sistem (Software Stack)

- **Embedded Firmware:** C++ via ESP-IDF / Arduino IDE, TinyML (Edge Impulse C++ SDK) untuk klasifikasi audio *on-device*.
- **Communication Protocols:** MQTT (Message Queuing Telemetry Transport) untuk pengiriman telemetry data rendah daya, WebSocket untuk *live audio streaming*.
- **Mobile Application (Companion App):** Flutter / React Native (Lintas platform Android & iOS).
- **Backend Server:** Node.js / Go + Firebase Cloud Messaging (FCM) untuk pengiriman *high-priority notification*.

---

## 6. Metodologi Penelitian & Pengembangan

1. **Studi Literatur & Analisis Kebutuhan:** Analisis ambang batas fisiologis manusia saat panik (*fight-or-flight response*) dan respons benturan fisik (*impact threshold*).
2. **Perancangan Hardware Prototipe:** Perakitan modul sensor, pengujian konsumsi daya (*power profiling*), dan pembuatan wadah (*enclosure 3D print*).
3. **Pengembangan Model TinyML & Algoritma Fusion:**
   - Pelatihan model pemroses suara (*Keyword Spotting*) menggunakan dataset teriakan darurat.
   - Pembuatan logika *Threshold & State Machine* untuk menggabungkan variabel *heart rate*, *gyro*, dan *suhu*.
4. **Pengembangan Backend & Mobile App:** Pembuatan antarmuka aplikasi penerima, integrasi peta (*Google Maps API*), serta modul pemutar audio *stream*.
5. **Pengujian Sistem & Validasi:**
   - **Pengujian Akurasi Trigger:** Menguji persentase *True Positive* dan *False Positive* pada skenario simulasi.
   - **Pengujian Latensi:** Mengukur durasi waktu dari pemicuan bahaya hingga sinyal diterima di HP kerabat.
   - **Pengujian Baterai & Ketahanan:** Mengukur *battery life* pada mode *standby* vs *panic mode*.

---

## 7. Tantangan Teknis & Solusi Pengembangan

| Tantangan Teknis | Dampak | Solusi Yang Ditawarkan |
|---|---|---|
| **False Alarm (Pemicu Palsu)** | Terjadi sinyal bahaya palsu saat pengguna berolahraga atau berteriak kaget. | Implementasi **Grace Period (5–10 Detik)** berupa getaran kuat haptik di jam. Pengguna dapat menekan tombol pembatalan sebelum data terkirim. |
| **Konsumsi Baterai Tinggi** | GPS dan Microphone *always-on* menguras daya baterai dalam waktu singkat. | Skema **Duty Cycling**: GPS & LTE berada dalam mode *deep sleep* dan baru diaktifkan penuh saat status *Panic Mode* terpicu. |
| **Konektivitas Lemah / Offline** | Area penculikan/pembegalan mengalami *blank spot* jaringan 4G. | **SMS Fallback Mechanism**: Perangkat otomatis mengirimkan koordinat GPS terakhir melalui jaringan SMS dasar jika jalur data internet terputus. |

---

## 8. Novelty & Kontribusi Ilmiah

- **Multi-Modal Emergency Fusion:** Penggabungan simultan antara sinyal fisiologis, respons gerakan tubuh, dan bukti audio dalam satu *device wearable*.
- **Embedded Edge-AI Safety:** Mengabaikan ketergantungan pemrosesan *cloud* untuk pengenalan kata kunci suara sehingga meningkatkan kecepatan respons (*low latency emergency response*).
- **Continuous Contextual Evidence Gathering:** Tidak hanya berfungsi sebagai penanda lokasi, melainkan sebagai alat pengumpul bukti digital (*digital evidence*) secara *real-time* untuk membantu pihak berwajib atau keluarga.

---

## 9. Rencana Jadwal Pelaksanaan (Roadmap)

- **Bulan 1:** Studi Literatur, Pembelian Modul Hardware, dan Perancangan Skematik Elektronika.
- **Bulan 2:** Pengumpulan Dataset Suara, Training Model TinyML, dan Pemrograman Firmware Sensor Fusion.
- **Bulan 3:** Pengembangan Mobile App (Companion App), Backend Server, dan Integrasi MQTT/WebSocket.
- **Bulan 4:** Pengujian Integrasi Terpadu, Evaluasi Latensi & Akurasi, Refinement Enclosure, serta Penyusunan Laporan/Jurnal.

---

## 10. Rekomendasi Topik Dosen Pembimbing

Rencana penelitian ini mencakup beberapa domain keilmuan yang dapat disesuaikan dengan kepakaran Dosen Pembimbing:

1. **Sistem Terdistribusi / Internet of Things (IoT):** Fokus pada arsitektur komunikasi data, konsumsi daya, dan integrasi multi-sensor.
2. **Artificial Intelligence / Machine Learning (TinyML):** Fokus pada pengembangan dan optimasi model *voice recognition* pada perangkat *resource-constrained*.
3. **Mobile & Ubiquitous Computing:** Fokus pada aplikasi pendamping *real-time*, pemetaan GPS, serta penanganan *high-priority notification*.
