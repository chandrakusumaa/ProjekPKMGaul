# Laporan Analisis Kelayakan dan Perencanaan Proyek PKM-KC: Smart Wearable Safety & Emergency Detection System

## Executive Summary dan Profil Proyek

Inovasi perangkat *Smart Wearable Safety & Emergency Detection System* dirancang untuk mengatasi peningkatan angka kejahatan jalanan, aksi pembegalan, dan kecelakaan lalu lintas tunggal pada pengendara motor melalui pendekatan pemicu darurat berlapis. Perangkat ini menggabungkan pendeteksian kondisi darurat secara otomatis menggunakan analisis biometrik, kinematik tubuh, serta pengenalan kata kunci suara (*Keyword Spotting*) berbasis AI tertanam (*TinyML*). Sistem terhubung secara *real-time* ke aplikasi pendamping (*companion app*) pada telepon pintar milik kerabat terdekat melalui jaringan telemetri seluler independen.

Proyek ini diajukan di bawah skema Program Kreativitas Mahasiswa Karsa Cipta (PKM-KC) oleh tim mahasiswa Program Studi Teknik Informatika, Universitas Pembangunan Nasional "Veteran" Jakarta. Evaluasi mendalam ini menganalisis rancangan arsitektur hardware, model integrasi sensor, potensi risiko teknis, serta kelayakan Rencana Anggaran Biaya (RAB) realistis sebesar Rp 6.500.000 yang difokuskan secara eksklusif untuk pembuatan **1 unit prototipe fisik alat** beserta pengujian teknisnya terhadap regulasi resmi Kementerian Pendidikan, Kebudayaan, Riset, dan Teknologi.

| Parameter Proyek | Spesifikasi dan Target Perencanaan |
|---|---|
| **Judul Proyek** | Smart Wearable Safety & Emergency Detection System Berbasis Biometric, Kinematik, dan Voice Recognition |
| **Skema Pengajuan** | Program Kreativitas Mahasiswa - Karsa Cipta (PKM-KC) |
| **Institusi Pengusul** | Universitas Pembangunan Nasional "Veteran" Jakarta |
| **Dimensi Modul Target** | 18 x 28 x 7 mm, Estimasi Berat 10–12 gram |
| **Pemroses Utama** | ESP32-S3 (Dual-core 32-bit LX7, Vector Acceleration) |
| **Konektivitas Telemetri** | SIM7600E-H (4G LTE + GPS Module) Independen |
| **Modalitas Deteksi** | MPU6050 (Kinematik), MAX30102 & MLX90614 (Biometric), INMP441 (Audio TinyML) |
| **Total Usulan Anggaran** | Rp 6.500.000 (Eksklusif Produksi 1 Unit Prototipe Alat) |
| **Durasi Program** | 4 Bulan Pelaksanaan |

---

## Analisis Kesesuaian Kategori dan Kepatuhan Regulasi PKM-KC

Kategori PKM-KC ditujukan sebagai wadah bagi mahasiswa untuk mewujudkan ide konstruktif berbasis karsa dan nalar yang menghasilkan prototipe fungsional berskala 1:1. Produk yang dihasilkan harus memiliki spesifikasi non-generik atau belum tersedia di pasar komersial dalam bentuk yang identik. Penggabungan sensor fisiologis, analisis pergerakan tubuh, serta ekstraksi fitur suara *offline* pada sebuah *smartwatch safety* memenuhi kriteria karsa cipta karena menghadirkan kebaruan fungsi yang tidak dimiliki oleh *smartwatch* kesehatan umum.

Berdasarkan Panduan Penyusunan Proposal PKM Belmawa, besaran alokasi pendanaan untuk proposal yang lolos seleksi berada pada kisaran Rp 6.000.000 hingga Rp 10.000.000 per judul. Usulan biaya proyek sebesar Rp 6.500.000 secara tepat berada dalam batas koridor pendanaan Belmawa dan memenuhi syarat batas minimum pendanaan. Pembatasan anggaran secara ketat pada ranah operasional produksi 1 unit prototipe dan peniadaan biaya non-teknis (seperti promosi dan ATK) mendukung efisiensi belanja prototipe.

---

## Evaluasi Rencana Anggaran Biaya Berdasarkan Realitas Harga Pasar (1 Unit Prototipe)

Rencana Anggaran Biaya (RAB) disusun berdasarkan kebutuhan produksi **1 unit prototipe alat** dengan mengacu pada harga komponen riil di marketplace (seperti Tokopedia untuk modul SIM7600E-H 4G LTE seharga Rp 1.412.000/unit). Seluruh biaya administrasi non-produksi ditiadakan 100% sehingga anggaran teralokasi khusus untuk pembuatan hardware, pabrikasi PCB, pencetakan enklosur, konektivitas cloud, dan pengujian lapangan.

### Rekapitulasi Alokasi Kategori Belmawa

| Kategori Pengeluaran Belmawa | Total Usulan (Rp) | Proporsi Usulan (%) | Batas Maksimum Pedoman (%) | Status Kepatuhan Regulasi |
|---|---|---|---|---|
| **Bahan Habis Pakai (Komponen Alat 1 Unit)** | 3.167.000 | 48,72% | Maksimal 60,00% | Sesuai Aturan (Sangat Aman di Bawah Limit) |
| **Sewa dan Jasa (Manufaktur Hardware)** | 950.000 | 14,62% | Maksimal 15,00% | Sesuai Aturan |
| **Transportasi Lokal (Uji Coba Lapangan)** | 1.883.000 | 28,97% | Maksimal 30,00% | Sesuai Aturan |
| **Lain-lain (Konektivitas Cloud & Server)** | 500.000 | 7,69% | Maksimal 15,00% | Sesuai Aturan |
| **Total Anggaran Keseluruhan** | **6.500.000** | **100,00%** | **100,00%** | **Sesuai Regulasi PKM** |

### Detail Harga Komponen Produksi Alat (Bahan Habis Pakai — Kebutuhan 1 Unit Prototipe)

| Nama Komponen / Layanan | Spesifikasi / Deskripsi | Qty | Harga Satuan (Rp) | Total (Rp) | Acuan Toko Online |
|---|---|---|---|---|---|
| ESP32-S3 N16R8 | Dual-core 32-bit, Vector Acceleration, 16MB Flash, 8MB PSRAM | 1 Pcs | 120.000 | 120.000 | Tokopedia / Shopee |
| SIM7600E-H 4G LTE + GPS | Modul Seluler 4G LTE + Antena GPS & SIM Card | 1 Pcs | 1.412.000 | 1.412.000 | Tokopedia (Toko SIM7600E-H 4G) |
| MAX30102 Pulse Oximeter | Sensor Detak Jantung & SpO2 I2C | 1 Pcs | 45.000 | 45.000 | Tokopedia / Shopee |
| MPU6050 | Sensor Gyroscope & Accelerometer 6-Axis | 1 Pcs | 25.000 | 25.000 | Tokopedia / Shopee |
| MLX90614-DCC | Sensor Suhu Tubuh Non-contact Infrared | 1 Pcs | 125.000 | 125.000 | Tokopedia / Shopee |
| INMP441 Digital Microphone | Omnidirectional I2S Digital Mic Module | 1 Pcs | 35.000 | 35.000 | Tokopedia / Shopee |
| Baterai LiPo 3.7V 300mAh | Baterai Lithium Polymer + BMS Protection Board | 1 Pcs | 45.000 | 45.000 | Tokopedia / Shopee |
| TP4056 Charger Module | Charger Board Type-C dengan Proteksi Baterai | 1 Pcs | 10.000 | 10.000 | Tokopedia / Shopee |
| Custom PCB Prototyping | Cetak PCB Double Layer (JLCPCB / Local PCB Fast) | 1 Paket | 400.000 | 400.000 | Jasa Cetak PCB |
| Material Casing & Component Set | Resistor, Cap, Button, Filament 3D & Strap | 1 Paket | 450.000 | 450.000 | Tokopedia / Shopee |
| Kartu Perdana & Kuota Data | SIM Card Seluler Multi-operator + Paket Data 4 Bulan | 1 Pcs | 150.000 | 150.000 | Marketplace Seluler |
| Perlengkapan Perakitan & Testbed | Breadboard, Cable Header, Timah, Solder Kit | 1 Paket | 350.000 | 350.000 | Tokopedia / Shopee |
| **Subtotal Bahan Habis Pakai** | | | | **Rp 3.167.000** | *(48,72% dari total)* |

### Detail Biaya Jasa Manufaktur, Transportasi, dan Infrastruktur Server

| Jenis Pengeluaran Jasa / Operasional | Kuantitas | Harga Satuan (Rp) | Total Harga (Rp) | Keterangan Fungsi |
|---|---|---|---|---|
| Jasa Desain Layout PCB Wearable | 1 paket | 400.000 | 400.000 | Optimasi kompresi ukuran PCB agar muat di wristband |
| Jasa Assembly SMT PCB & Stencil | 1 paket | 300.000 | 300.000 | Pemasangan komponen micro SMD secara presisi |
| Jasa 3D Print Enclosure High Detail | 1 paket | 250.000 | 250.000 | Pencetakan casing fisik wearable halus & tahan air |
| Transportasi Lokal Operasional | 1 paket | 1.883.000 | 1.883.000 | Pengadaan bahan, koordinasi lab, & uji lapangan |
| Cloud Server MQTT/WebSocket | 4 bulan | 125.000 | 500.000 | Sewa broker server data stream real-time & database |
| **Subtotal Jasa & Operasional** | | | **Rp 3.333.000** | *(51,28% dari total)* |
| **TOTAL KESELURUHAN RAB** | | | **Rp 6.500.000** | **Eksklusif Produksi 1 Unit Alat** |

---

## Analisis Kelayakan Teknis Hardware, Sensor Fusion, dan TinyML

### Spesifikasi Antarmuka Perangkat Keras

Perangkat utama mengintegrasikan mikrokontroller ESP32-S3 dengan lima sensor dan modul komunikasi seluler independen. ESP32-S3 mengeksekusi pengolahan sinyal digital dan model pemrosesan vektor untuk mendukung pembelajaran mesin di tingkat *embedded* (*TinyML*).

| Modul Hardware | Jenis Antarmuka | Parameter Sinyal Terukur | Peran Pemrosesan Utama |
|---|---|---|---|
| **ESP32-S3 MCU** | Internal Bus / SPI | Vektor Neural Acceleration | Pemrosesan Sensor Fusion dan inferensi model TinyML |
| **MAX30102** | I2C (Alamat 0x57) | Photoplethysmogram (PPG) | Pengukuran lonjakan detak jantung (HR) dan kadar SpO2 |
| **MLX90614** | SMBus / I2C | Radiasi Termal Inframerah | Pengukuran suhu kulit sebagai penanda tingkat stres |
| **MPU6050** | I2C (Alamat 0x68) | Akselerasi 3-Axis & Gyro 3-Axis | Deteksi benturan fisik (G-force) dan orientasi tubuh |
| **INMP441** | I2S Digital Interface | Audio PCM 16 kHz / 24-bit | Input gelombang suara untuk klasifikasi kata kunci darurat |
| **SIM7600E-H** | UART (AT Commands) | 4G LTE Packets & GPS NMEA | Transmisi telemetri MQTT/WSS dan pelacakan koordinat |

### Formulasi Algoritma Sensor Fusion dan TinyML

Pengenalan kondisi bahaya dilakukan menggunakan kombinasi sinyal kinematik, biometrik, dan analisis frekuensi audio yang diatur oleh logika *State Machine* multivariat.

Deteksi kecelakaan lalu lintas ditentukan oleh lonjakan magnitudo akselerasi total:

```
A_mag = √(a_x² + a_y² + a_z²)
```

yang melampaui ambang batas benturan fisik (`A_mag > T_impact`), dilanjutkan dengan kondisi hilangnya pergerakan tubuh (`V_motion ≈ 0`) selama periode waktu tertentu (`t_immobile > 5 detik`), sehingga kondisi kecelakaan dirumuskan sebagai:

```
Condition_Accident = (A_mag > T_impact) ∧ ( ∫[t0, t0+Δt] |ω| dt < T_still )
```

Deteksi tindakan pembegalan atau penyerangan memanfaatkan respons fisiologis *fight-or-flight*. Logika sistem mengidentifikasi lonjakan frekuensi detak jantung secara mendadak (`ΔHR/Δt > T_spike`) akibat pelepasan adrenalin, yang terjadi bersamaan dengan tingkat variasi gerakan tangan bertipe defensif (`STD(a_kinematic) > T_defensive`).

Pengenalan suara secara *offline* (*Keyword Spotting*) memproses sinyal audio digital dari mikrofon INMP441. Sinyal diubah ke dalam bentuk representasi frekuensi *Mel-Frequency Cepstral Coefficients* (MFCC) secara berkala. Matriks MFCC kemudian diumpankan ke model *Convolutional Neural Network* 1D yang telah terkompresi menggunakan Edge Impulse C++ SDK. Model berjalan secara lokal pada mikrokontroller ESP32-S3, dan akan mengaktifkan status darurat jika skor probabilitas inferensi kata kunci (seperti "Tolong" atau "Begal") melebihi nilai 0,85.

### Tantangan Integrasi Dimensi dan Manajemen Daya Baterai

Dokumen perancangan visual menetapkan target ukuran casing sebesar 18 x 28 x 7 mm dengan berat total 10–12 gram. Analisis rekayasa fisik menunjukkan bahwa target dimensi tersebut terlalu kecil untuk prototipe yang dibangun dari modul-modul komersial lepas. Referensi riset perangkat *wearable armband* mencatat bahwa modul optik komersial seperti Polar Verity Sense memiliki ukuran 30 x 30 x 9,5 mm dengan berat sensor 5 gram. Penggunaan modul breakout SIM7600E-H standar yang berukuran 30 x 30 mm menyebabkan ukuran casing realistis untuk prototipe awal PKM-KC berada pada kisaran 40 x 35 x 12 mm. Dimensi target 18 x 28 x 7 mm hanya dapat dicapai melalui pembuatan custom *Rigid-Flex Multi-layer PCB* yang membutuhkan biaya pabrikasi tinggi di luar batasan anggaran PKM.

Dari perspektif konsumsi daya, penggunaan baterai LiPo 3,7V 300 mAh menyediakan total energi teoritis sebesar 1,11 Wh. Transmisi data seluler 4G pada modul SIM7600 membutuhkan arus rata-rata ≈ 200–250 mA (0,825 Watt), sedangkan pemrosesan kontinu ESP32-S3 beserta inferensi AI mengonsumsi arus ≈ 100–150 mA (0,412 Watt). Jika seluruh modul berada pada kondisi aktif penuh (*always-on*), baterai akan habis dalam waktu kurang dari 1 jam.

Untuk mengatasi keterbatasan daya, sistem harus menerapkan teknik *Duty Cycling*. Modul SIM7600 dan GPS diposisikan pada mode *Deep Sleep* (< 2 mA) selama kondisi normal. Modul telemetri hanya diaktifkan secara penuh saat pemicu otomatis (kinematik/biometrik), pemicu suara TinyML, atau tombol darurat manual mendeteksi adanya status bahaya.

---

## Analisis Kebaruan dan Perbandingan Kompetitif

Sistem ini menawarkan keunggulan operasional jika dibandingkan dengan *smartwatch* kesehatan komersial maupun alat keamanan personal konvensional.

| Parameter Evaluasi | Smartwatch Kesehatan Komersial | Alat Keamanan Konvensional | System Smart Wearable PKM-KC |
|---|---|---|---|
| **Mekanisme Pemicuan** | Interaksi fisik manual (menekan tombol berkali-kali) | Manual (menekan tombol panic / menarik tuas) | **Tri-Layer Fusion** (Otomatis Sensor Fusion + Voice TinyML + Manual) |
| **Deteksi Suara Darurat** | Tergantung koneksi cloud (Siri / Google Assistant) | Tidak tersedia | **Offline Keyword Spotting** langsung pada mikrokontroller |
| **Kelengkapan Bukti** | Hanya pesan teks koordinat GPS satu kali | Sirine lokal tanpa transmisi data | **Continuous Evidence** (Live Audio Streaming, Biometric Feed, GPS) |
| **Ketergantungan Ponsel** | Sangat tinggi (Membutuhkan koneksi Bluetooth ponsel) | Berdiri sendiri tanpa komunikasi jarak jauh | **Independen** via modul seluler 4G LTE terintegrasi |

Kebaruan ilmiah dari proyek ini terletak pada integrasi algoritma *Sensor Fusion* berbasis fisiologis dan kinematik dengan pengenalan suara *on-device* yang beroperasi pada sistem hemat daya. Pendekatan ini memangkas latensi pemicuan sinyal darurat menjadi di bawah 2 detik tanpa tergantung pada pemrosesan server *cloud* atau jaringan telepon pintar korban.

---

## Matriks Analisis Risiko Teknis dan Solusi Mitigasi

Proses rekayasa perangkat *smart wearable safety* memiliki beberapa potensi kendala teknis dalam implementasinya. Matriks berikut mengidentifikasi risiko utama beserta solusi rancangan yang diterapkan:

| Potensi Risiko Teknis | Tingkat Dampak | Akar Penyebab Masalah | Solusi Mitigasi Sistem |
|---|---|---|---|
| **Pemicu Palsu (False Alarm)** | Tinggi | Peningkatan detak jantung akibat olahraga atau teriakan tanpa ancaman. | **Grace Period (5–10 Detik)** berupa getaran haptik. Pengguna dapat membatalkan pengiriman sinyal. |
| **Konsumsi Daya Berlebih** | Tinggi | Penggunaan modul SIM7600 dan mikrofon secara terus-menerus. | **Duty Cycling State Machine**. Modul SIM7600 dipertahankan dalam kondisi deep sleep hingga terjadi pemicuan. |
| **Area Blank Spot Seluler** | Sedang | Area geografis tidak terjangkau sinyal jaringan data 4G. | **SMS Fallback Mechanism**. Sistem otomatis mengirimkan koordinat GPS via SMS jika koneksi internet terputus. |
| **Artefak Gerakan PPG** | Sedang | Pergerakan pergelangan tangan mengganggu pembacaan sensor MAX30102. | Penerapan **Digital Bandpass Filter** dan penyesuaian gain LED otomatis pada firmware. |

---

## Rencana Kerja dan Roadmap Pelaksanaan Proyek

Pelaksanaan proyek dirancang berlangsung selama 4 bulan untuk memenuhi luaran wajib PKM-KC, mencakup prototipe fungsional, laporan akhir, dan artikel ilmiah.

### Bulan Pertama: Perancangan Sistem dan Pengadaan Komponen

Kegiatan berfokus pada studi literatur mengenai ambang batas respons fisiologis manusia saat panik serta respons benturan fisik. Tim melakukan pengadaan modul hardware berdasarkan daftar belanja marketplace untuk 1 unit prototipe, pengujian fungsionalitas sensor pada *breadboard*, serta perancangan skematik rangkaian dan sketsa awal enklosur 3D.

### Bulan Kedua: Pengembangan Firmware, Model TinyML, dan Sensor Fusion

Kegiatan berfokus pada pengumpulan dataset audio suara teriakan dan kata kunci darurat. Model *Keyword Spotting* dilatih menggunakan platform Edge Impulse dan dikompilasi ke dalam format C++ SDK. Pemrograman *firmware* pada ESP32-S3 dilakukan untuk mengimplementasikan algoritma *Sensor Fusion* dan logika *State Machine*.

### Bulan Ketiga: Integrasi Hardware, Server Backend, dan Aplikasi Pendamping

Kegiatan berfokus pada pabrikasi PCB prototipe, perakitan komponen SMD, dan pencetakan casing menggunakan *3D printing*. Tim membangun server backend berbasis MQTT/WebSocket dan mengembangkan antarmuka aplikasi pendamping untuk menerima notifikasi darurat serta menampilkan data telemetri.

### Bulan Keempat: Pengujian Sistem, Evaluasi, dan Penyusunan Laporan

Kegiatan berfokus pada pengujian integrasi secara menyeluruh. Pengujian mencakup pengukuran tingkat akurasi pemicu (*True Positive* vs *False Positive*), evaluasi latensi pengiriman data, dan pengujian ketahanan baterai pada berbagai mode operasional. Tahap akhir diisi dengan penyusunan Laporan Kemajuan, Laporan Akhir, dan Artikel Ilmiah. Seluruh aktivitas harian dicatat secara rutin pada portal SIMBelmawa.

---

## Kesimpulan dan Rekomendasi Strategis

### Kesimpulan Kelayakan

Rencana pengembangan *Smart Wearable Safety & Emergency Detection System* memiliki kelayakan teknis dan kebaruan ilmiah yang kuat untuk diajukan pada skema PKM-KC. Penggunaan metode pemicu berlapis berbasis *Sensor Fusion* dan *TinyML* memberikan solusi atas keterbatasan *smartwatch* konvensional. Penyesuaian total RAB menjadi Rp 6.500.000 khusus untuk **1 unit prototipe fisik** menjadikan proposal 100% patuh pada aturan Belmawa sekaligus sangat realistis dan hemat untuk diimplementasikan.

### Rekomendasi Langkah Perbaikan

1. **Mempertahankan Formulasi RAB 1 Unit Rp 6.500.000:** Jaga alokasi Bahan Habis Pakai pada 48,72% (Rp 3.167.000), Sewa/Jasa Manufaktur 14,62% (Rp 950.000), Transportasi Lokal Pengujian 28,97% (Rp 1.883.000), dan Server Cloud 7,69% (Rp 500.000).
2. **Penyesuaian Spesifikasi Dimensi Prototipe:** Ubah klaim dimensi prototipe pada dokumen dari 18 x 28 x 7 mm menjadi 40 x 35 x 12 mm untuk mencerminkan batasan penggunaan modul komponen komersial lepas.
3. **Penegasan Pemrosesan Suara Offline:** Perjelas pada proposal bahwa proses inferensi kata kunci suara berjalan penuh secara *offline* di mikrokontroller tanpa membutuhkan koneksi internet, guna menonjolkan nilai kebaruan (*novelty*) sistem.
4. **Detailing Manajemen Daya:** Sertakan penjelasan skema *Duty Cycling* pada bab metodologi proposal untuk membuktikan bahwa penggunaan baterai LiPo 300 mAh mampu menopang operasional perangkat.

### Karya yang Dikutip

1. RAB_PKM_KC_Smart_Wearable.xlsx
2. 3. Pedoman-PKM-KC-2023, https://unej.ac.id/wp-content/uploads/2023/02/3.-Pedoman-PKM-KC-2023.pdf
3. Panduan Proposal PKM 2025 | PDF - Scribd, https://id.scribd.com/document/901576489/Template-PKM-RE-2025
4. PKM SKEMA Karsa Cipta - Universitas Merdeka Surabaya, https://unmerbaya.ac.id/file/page/2022/03/pkm_skema_karsa_cipta.pdf
