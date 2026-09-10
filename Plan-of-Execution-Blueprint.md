# Plan of Execution (Blueprint Realisasi Proyek)

**Smart Wearable Safety & Emergency Detection System**

> Rencana Operasional & Perencanaan Proyek Lengkap (*Project Execution Blueprint*) ini disusun untuk merealisasikan *Smart Wearable Safety & Emergency Detection System*, dan dirancang agar dapat diajukan dalam skema **Program Kreativitas Mahasiswa Karsa Cipta (PKM-KC)** maupun proyek riset tingkat akhir/skripsi.

---

## 1. Konsep Lengkap & Bentuk Fisik (Form Factor)

### 1.1 Konsep Utama Produk

Perangkat ini dirancang sebagai **Smart Safety Armband / Wristband Ergonomis** yang memadukan fungsi keselamatan, pemrosesan AI lokal (*Edge-AI*), serta telemetri independen tanpa bergantung pada *smartphone* korban.

- **Target Dimensi Prototipe Realistis:** 40 × 35 × 12 mm (Berat ± 25–30 gram). Penyesuaian dimensi ini diambil agar modul *breakout* komersial (seperti SIM7600E-H, ESP32-S3, dan sensor biometrik) dapat terpasang rapi dalam satu *enclosure*.

- **Tata Letak Komponen:**
  - **Sisi Atas (Top Face):** Tombol Darurat Manual SOS (*Panic Button*), LED Indikator Status, dan lubang Mikrofon Digital I2S (INMP441) untuk *Keyword Spotting*.
  - **Sisi Bawah (Underside / Skin-Contact):** Sensor Optik PPG (MAX30102) dan Sensor Suhu IR (MLX90614) yang menempel langsung pada kulit.
  - **Sistem Pengikat (Strap):** Tali silikon/velcro fleksibel yang ergonomis, dipasang di lengan atas (*armband*) atau pergelangan tangan (*wristband*) bagi pengendara sepeda motor.

**Tata Letak Prototipe 3D:**

```
+-----------------------------------------------+
| [INMP441 Mic]        [LED Indikator]           |  <- Sisi Atas
|              [ SOS BUTTON ]                    |
+-----------------------------------------------+
| [ESP32-S3 & SIM7600E-H]                        |  <- Bagian Dalam (PCB)
| [LiPo Battery 300mAh]                          |
+-----------------------------------------------+
| [MAX30102 PPG]       [MLX90614 IR Temp]        |  <- Sisi Bawah (Kulit)
+-----------------------------------------------+
```

---

## 2. Arsitektur Logika Sensor Fusion & State Machine

Sistem tidak hanya mengandalkan satu nilai pemicu, melainkan mengkombinasikan variabel fisiologis dan gerak tubuh menggunakan **Finite State Machine (FSM)** untuk mencegah *False Alarm*:

```
+---------------------------------------------+
|          STANDBY / MONITORING                |
|  - Sensor Aktif (Low Power)                  |
|  - GPS/LTE Deep Sleep (< 2 mA)                |
+---------------------------------------------+
                      |
      +---------------+----------------+
      |               |                |
[Deteksi Impact  [Spike HR +      [Keyword Voice
   G-Force]       Motion Kacau]      Match]
      |               |                |
      +---------------+----------------+
                      |
                      v
+---------------------------------------------+
|       EVALUASI GRACE PERIOD (8 detik)         |
|  - Jam Bervibrasi Kuat (Haptic)               |
|  - Pengguna Batal = Tekan Tombol              |
+---------------------------------------------+
                      |
            (Tidak Dibatalkan Pengguna)
                      |
                      v
+---------------------------------------------+
|                 PANIC MODE                    |
|  - Bangkitkan SIM7600E (LTE & GPS)            |
|  - Kirim MQTT Telemetry + Stream              |
|  - SMS Fallback (Jika Internet Terputus)      |
+---------------------------------------------+
```

---

## 3. Rencana Anggaran Biaya (RAB) Realistis

Rencana Anggaran Biaya ini disusun berdasarkan **harga riil di *e-commerce* / Tokopedia / Shopee** dengan efisiensi maksimal (sesuai standar pagu PKM-KC Belmawa kisaran Rp 6.000.000 – Rp 8.000.000).

### Bahan Habis Pakai

| Nama Komponen / Layanan | Spesifikasi / Deskripsi | Qty | Harga Satuan (Rp) | Total (Rp) |
|---|---|---|---|---|
| ESP32-S3 N16R8 | Dual-core 32-bit, Vector Acceleration, 16MB Flash, 8MB PSRAM | 3 Pcs | 120.000 | 360.000 |
| SIM7600E-H 4G LTE + GPS | Modul Seluler 4G LTE + Antena GPS & SIM Card | 2 Pcs | 480.000 | 960.000 |
| MAX30102 Pulse Oximeter | Sensor Detak Jantung & SpO2 I2C | 3 Pcs | 45.000 | 135.000 |
| MPU6050 | Sensor Gyroscope & Accelerometer 6-Axis | 3 Pcs | 25.000 | 75.000 |
| MLX90614-DCC | Sensor Suhu Tubuh Non-contact Infrared | 2 Pcs | 125.000 | 250.000 |
| INMP441 Digital Microphone | Omnidirectional I2S Digital Mic Module | 3 Pcs | 35.000 | 105.000 |
| Baterai LiPo 3.7V 300mAh | Baterai Lithium Polymer + BMS Protection Board | 3 Pcs | 45.000 | 135.000 |
| TP4056 Charger Module | Charger Board Type-C dengan Proteksi Baterai | 3 Pcs | 10.000 | 30.000 |
| Custom PCB Prototyping | Cetak PCB Double Layer (JLCPCB / Local PCB Fast) | 1 Paket | 350.000 | 350.000 |
| Komponen Pasif & Casing | Resistor, Cap, Buzzer, Button, Filament 3D Printing | 1 Paket | 450.000 | 450.000 |
| Kartu Perdana & Kuota Data | SIM Card Seluler Multi-operator + Paket Data 4 Bulan | 2 Pcs | 100.000 | 200.000 |
| **Subtotal Bahan Habis Pakai** | | | | **Rp 3.500.000** |

### Sewa & Jasa

| Nama Komponen / Layanan | Spesifikasi / Deskripsi | Qty | Harga Satuan (Rp) | Total (Rp) |
|---|---|---|---|---|
| Jasa Manufaktur Enclosure | 3D Printing Resin/SLA Precision (Bentuk Wristband) | 1 Paket | 450.000 | 450.000 |
| Jasa Assembly & Solder PCB | SMD & Through-Hole Soldering Prototipe | 1 Paket | 500.000 | 500.000 |
| **Subtotal Sewa & Jasa** | | | | **Rp 950.000** |

### Transportasi

| Nama Komponen / Layanan | Spesifikasi / Deskripsi | Qty | Harga Satuan (Rp) | Total (Rp) |
|---|---|---|---|---|
| Pengujian Lapangan & Uji Coba | Transportasi pengujian lapangan (Area rawan/simulasi jalan) | 1 Paket | 1.850.000 | 1.850.000 |

### Lain-lain

| Nama Komponen / Layanan | Spesifikasi / Deskripsi | Qty | Harga Satuan (Rp) | Total (Rp) |
|---|---|---|---|---|
| Cloud Server & FCM Service | Hosting Cloud VPS (AWS/DigitalOcean) 4 Bulan + Domain | 1 Paket | 200.000 | 200.000 |

### Total Keseluruhan (RAB)

| Kategori | Subtotal (Rp) |
|---|---|
| Bahan Habis Pakai | 3.500.000 |
| Sewa & Jasa | 950.000 |
| Transportasi | 1.850.000 |
| Lain-lain | 200.000 |
| **TOTAL** | **Rp 6.500.000** |

---

## 4. Jangka Waktu & Timeline Pelaksanaan (4 Bulan / 16 Minggu)

### Phase 1: Desain & Analisis (Minggu 1–4)

| Kegiatan | M1 | M2 | M3 | M4 |
|---|---|---|---|---|
| Studi Literatur & Dataset Audio | X | X | | |
| Desain Skematik & PCB Layout | | X | X | |
| Desain 3D Enclosure Armband | | | X | X |

### Phase 2: Fabrikasi & TinyML (Minggu 4–7)

| Kegiatan | M4 | M5 | M6 | M7 |
|---|---|---|---|---|
| Order & Fabrikasi PCB & Casing | X | X | | |
| Training Model Keyword Spotting | X | X | X | |
| Coding Firmware Sensor Fusion | | X | X | X |

### Phase 3: App & Integrasi Cloud (Minggu 6–10)

| Kegiatan | M6 | M7 | M8 | M9 | M10 |
|---|---|---|---|---|---|
| Setup Cloud MQTT Broker & Server | X | X | | | |
| Flutter Companion App Dev | | X | X | X | |
| Integrasi Hardware + Cloud + App | | | | X | X |

### Phase 4: Uji Coba & Evaluasi (Minggu 11–16)

| Kegiatan | M11 | M12 | M13 | M14 | M15 | M16 |
|---|---|---|---|---|---|---|
| Pengujian Akurasi Trigger & Latensi | X | X | | | | |
| Testing Konsumsi Daya (Battery) | X | X | | | | |
| Penyusunan Laporan & Jurnal PKM | | | X | X | X | X |

---

## 5. Langkah-Langkah Implementasi Eksekusi (Step-by-Step)

### Langkah 1: Pengumpulan Data & Pelatihan Model TinyML (Keyword Spotting)

1. **Rekam Data Audio:** Kumpulkan minimal 500–1.000 sampel rekaman suara kata kunci darurat ("Tolong!", "Begal!", "Sosis!" [kata sandi]) serta sampel *background noise* (suara angin motor, lalu lintas).
2. **Edge Impulse Studio:** *Upload* dataset ke platform Edge Impulse. Lakukan ekstraksi fitur menggunakan MFE (Mel-Filterbank Energy).
3. **Training & Quantization:** Latih model Neural Network (CNN) 1D. Lakukan *quantization* menjadi format INT8 agar bobot model < 100 KB dan ringan dieksekusi di ESP32-S3.
4. **Deploy C++ SDK:** Ekspor model menjadi pustaka C++ SDK dan masukkan ke dalam proyek firmware ESP-IDF/Arduino.

### Langkah 2: Fabrikasi Hardware & Pemrograman Firmware

1. **Rancang PCB:** Buat skematik di KiCad/EasyEDA. Hubungkan ESP32-S3 dengan MAX30102 (I2C), MPU6050 (I2C), INMP441 (I2S), MLX90614 (I2C), dan SIM7600E-H (UART).
2. **Implementasi Logic Fusion:** Tulis kode pemrosesan sensor di mana data *gyroscope* dipindai terus-menerus. Jika terjadi guncangan > 4G atau detak jantung melompat tiba-tiba di atas 130 BPM, aktifkan *State Grace Period*.
3. **Optimasi Power Management (Duty Cycling):** Set modul SIM7600E-H dan GPS dalam mode *Power Save / Deep Sleep*. Buat interrupt dari ESP32-S3 untuk menyalakan modul 4G hanya saat pemicu darurat aktif.

### Langkah 3: Pengembangan Aplikasi Pendamping (*Companion App*) & Cloud

1. **Backend Real-Time:** Gunakan Broker MQTT (mis. Mosquitto / EMQX) untuk *telemetry ingestion* berlatensi rendah (< 1 detik).
2. **Pengembangan Aplikasi (Flutter):**
   - Implementasikan *High-Priority Notification* (menggunakan FCM & Awesome Notifications) agar aplikasi tetap berbunyi keras meskipun HP penerima dalam kondisi *Silent/Do Not Disturb*.
   - Integrasikan Google Maps SDK untuk menampilkan pergerakan koordinat korban secara *live*.
   - Buat pemutar aliran suara (*Audio Stream Player*) untuk mendengarkan bukti kondisi TKP secara *real-time*.

### Langkah 4: Pengujian & Validasi Kinerja (Benchmarking)

1. **Uji Latensi Kirim:** Ukur interval waktu sejak pemicu terdeteksi di *wearable* hingga notifikasi muncul di HP kerabat (Target: < 3 detik).
2. **Uji Akurasi (Confusion Matrix):** Hitung rasio *True Positive* vs *False Positive* pada skenario:
   - Orang berolahraga lari (pembacaan HR tinggi tapi tidak ada *impact*).
   - Jatuh/Kecelakaan motor simulasi.
   - Teriakan darurat di jalanan bising.
3. **Uji Daya Baterai:** Pastikan baterai 300mAh mampu bertahan minimal 14–18 jam dalam kondisi *Standby* harian.

---

## 6. Kesimpulan Perencanaan Proyek

Proyek **Smart Wearable Safety & Emergency Detection System** ini memiliki kelayakan eksekusi (*technical feasibility*) yang sangat tinggi untuk diimplementasikan oleh mahasiswa Teknik Informatika.

1. **Realisme Desain & Hardware:** Penyesuaian dimensi fisik menjadi 40 × 35 × 12 mm dalam bentuk *Smart Armband* menjamin bahwa alat ini dapat diproduksi menggunakan komponen lepas komersial tanpa kendala *overheating* atau ukuran yang terlalu ekstrem.
2. **Efisiensi Biaya:** Dengan total anggaran **Rp 6.500.000**, seluruh kebutuhan prototipe, pembuatan aplikasi, hingga uji coba lapangan tercukupi secara presisi dan patuh terhadap regulasi pendanaan PKM Belmawa Kemdikbudristek.
3. **Nilai Kebaruan (Novelty):** Kombinasi pemicu multi-moda (*Biometric + Kinematic + Edge-AI Voice Spotting*) independen berbasis 4G menjadikan inovasi ini relevan, solutif, dan memiliki daya tawar tinggi saat dipresentasikan di hadapan dosen pembimbing maupun penguji PIMNAS.
