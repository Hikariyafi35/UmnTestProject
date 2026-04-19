# 🐠 Aquascape Technical Test

Project ini adalah game simulasi **Aquascape 2D** yang dibuat menggunakan **Unity**.

Gameplay utama mengubah file gambar **`.png`** yang dimasukkan ke folder tertentu menjadi objek di dalam game secara **real-time**.

Objek yang dapat di-spawn:

* 🐟 **Fish** → entitas hidup dengan movement dan behavior
* 🗑️ **Trash** → sampah yang mengapung di aquarium

Project dibuat dengan arsitektur modular dan sistem konfigurasi eksternal agar mudah diubah tanpa rebuild.

---

## 🎮 Versi Unity

* **Developed With:** `Unity 6000.3.0f1`
* **Compatible With:** `Unity 6000.3.12f1`

> Keduanya berada pada branch versi **6000.3.x**

---

## ✨ Fitur Utama

### 📂 1. Sistem Spawn Berbasis File (Real-Time)

Aplikasi memantau folder menggunakan **FileSystemWatcher**.

Saat file `.png` baru dimasukkan ke folder, objek akan otomatis muncul di dalam game saat runtime.

#### Format Nama File

```text id="rmf2af"
FISH_[TYPE]_[YYYYMMDDHHMMSS].png
TRASH_[TYPE]_[YYYYMMDDHHMMSS].png
```

#### Contoh

```text id="1e1x6e"
FISH_MACKEREL_20260401165920.png
FISH_NEMO_20260401170000.png
TRASH_BOTTLE_20260401170100.png
TRASH_CAN_20260401170200.png
```

---

### 🐟 2. Behavior Fish

Fish memiliki fitur:

* Bergerak berenang secara acak
* Kecepatan minimum & maksimum yang dapat diatur
* Sistem hunger meter
* Mencari makanan terdekat saat lapar
* Berhenti makan saat kenyang
* Kabur sementara saat diklik
* Sound effect saat diklik / makan

---

### 🗑️ 3. Behavior Trash

Trash memiliki fitur:

* Bergerak mengapung secara acak
* Mantul saat mengenai dinding
* Terdorong saat terkena tabrakan ikan

---

### 🖱️ 4. Interaksi Player

| Aksi                  | Hasil                |
| --------------------- | -------------------- |
| Klik kiri area kosong | Spawn makanan        |
| Klik kiri fish        | Fish takut dan kabur |
| Klik kiri trash       | Menghapus trash      |

---

## ⚙️ Sistem Konfigurasi

Nilai gameplay dapat diubah tanpa rebuild menggunakan file:

```text id="d3a8sq"
config.json
```

File diletakkan di folder yang sama dengan file **`.exe`**.

---

## 📁 Contoh Struktur Build

```text id="39iq7w"
Aquascape.exe
config.json
InputFolder/
```

---

## 🧾 Contoh config.json

```json id="6mbk4e"
{
  "watchFolder": "",

  "fishMinSpeed": 1.5,
  "fishMaxSpeed": 3.0,
  "fishDetectionRadius": 15,

  "fishScareDuration": 6,
  "fishScareSpeedMultiplier": 12,
  "scareForce": 8,

  "hungerDecreasePerSecond": 10,
  "hungerCooldown": 5,

  "foodFallSpeed": 1.5,

  "pushForce": 2,

  "masterVolume": 1,
  "fishClickVolume": 0.8,
  "fishEatVolume": 0.7
}
```

---

## 📂 Folder Watcher

Saat game dijalankan, sistem akan membaca lokasi folder dari:

### Opsi 1 (Disarankan)

Isi path custom pada `config.json`

```json id="1sp0vy"
"watchFolder": "D:/AquascapeInput"
```

Game akan memantau folder tersebut.

### Opsi 2

Jika `watchFolder` dikosongkan:

```json id="o3vsu4"
"watchFolder": ""
```

Game otomatis menggunakan folder default:

```text id="6w9s85"
InputFolder/
```

Folder akan dibuat otomatis jika belum ada.

---

## 🚀 Cara Menjalankan

### Build Version

1. Jalankan **Aquascape.exe**
2. Buka folder watcher
3. Masukkan file `.png` sesuai format nama
4. Objek akan otomatis muncul

### Unity Project

1. Clone repository
2. Buka project menggunakan Unity `6000.3.0f1` atau `6000.3.12f1`
3. Buka sample scene
4. Tekan **Play**

---

## 🧠 Struktur Script

```text id="pdpt3y"
Scripts/
├── Fish/
│   ├── FishMovement.cs
│   ├── Hunger.cs
│   └── Velocity.cs
│
├── Trash/
│   └── TrashMovement.cs
│
├── ConfigManager.cs
├── Interaction.cs
├── TestWatcher.cs
├── Exit.cs
└── SpawnMapping.cs
```

---

## 📌 Tanggung Jawab Script

### TestWatcher.cs

* Monitoring folder
* Scan file lama saat start
* Load PNG runtime
* Membuat sprite
* Spawn Fish / Trash
* Posisi spawn tidak overlap
* Membaca lokasi folder dari config atau default folder

### FishMovement.cs

* Gerakan ikan
* AI mencari makanan
* State takut
* Sound effect

### Hunger.cs

* Hunger meter
* Cooldown setelah kenyang

### TrashMovement.cs

* Gerakan mengapung
* Mantul dari dinding
* Reaksi dorongan tabrakan

### Interaction.cs

* Mengatur klik mouse player

### ConfigManager.cs

* Membaca file konfigurasi eksternal

---

## 📄 Format File yang Didukung

```text id="xh3fdk"
.png
```

---

## ⚠️ File Tidak Valid

Nama file yang salah akan diabaikan secara aman.

Contoh:

```text id="xj5v90"
fish.png
abc.png
gambar_test.png
```

---

## 🛠️ Teknologi yang Digunakan

* Unity Engine
* C#
* FileSystemWatcher
* JsonUtility
* Unity Input System

---

## 🤖 Disclosure Penggunaan AI

AI yang digunakan:
* Chat GPT

digunakan untuk:
* Diskusi arsitektur
* Bantuan debugging
* Review logic
* Penyusunan dokumentasi

Seluruh implementasi, integrasi, testing, balancing, dan finalisasi project dilakukan secara manual.

---
