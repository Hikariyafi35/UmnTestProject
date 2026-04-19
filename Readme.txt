# Aquascape Technical Test - README

## Gambaran Umum

Project ini adalah game simulasi **Aquascape 2D** yang dibuat menggunakan Unity.
Gameplay utama mengubah file gambar `.png` yang dimasukkan ke folder tertentu menjadi objek di dalam game secara real-time.

Objek yang dapat di-spawn:

* **Fish** → entitas hidup dengan movement dan behavior
* **Trash** → sampah yang mengapung di aquarium

Project dibuat dengan arsitektur modular dan sistem konfigurasi eksternal agar mudah diubah tanpa rebuild.

---

# Versi Unity

Dikembangkan menggunakan:

```text id="i1"
Unity 6000.3.0f1
```

Kompatibel dengan versi yang diminta:

```text id="i2"
Unity 6000.3.12f1
```

(Keduanya berada pada branch versi `6000.3.x`)

---

# Fitur Utama

## 1. Sistem Spawn Berbasis File (Real-Time)

Aplikasi memantau folder menggunakan `FileSystemWatcher`.

Saat file `.png` baru dimasukkan ke folder, objek akan otomatis muncul di dalam game saat runtime.

### Format Nama File

```text id="i3"
FISH_[TYPE]_[YYYYMMDDHHMMSS].png
TRASH_[TYPE]_[YYYYMMDDHHMMSS].png
```

### Contoh

```text id="i4"
FISH_MACKEREL_20260401165920.png
FISH_NEMO_20260401170000.png
TRASH_BOTTLE_20260401170100.png
TRASH_CAN_20260401170200.png
```

---

## 2. Behavior Fish

Fish memiliki fitur:

* Bergerak berenang secara acak
* Kecepatan minimum & maksimum yang dapat diatur
* Sistem hunger meter
* Mencari makanan terdekat saat lapar
* Berhenti makan saat kenyang
* Kabur sementara saat diklik
* Sound effect saat diklik / makan

---

## 3. Behavior Trash

Trash memiliki fitur:

* Bergerak mengapung secara acak
* Mantul saat mengenai dinding
* Terdorong saat terkena tabrakan ikan

---

## 4. Interaksi Player

### Klik Kiri Area Kosong

Spawn makanan pada posisi kursor.

### Klik Kiri Fish

Fish akan takut dan kabur sementara.

### Klik Kiri Trash

Menghapus objek trash.

---

# Sistem Konfigurasi

Nilai gameplay dapat diubah tanpa rebuild menggunakan file:

```text id="i5"
config.json
```

File diletakkan di folder yang sama dengan `.exe`.

---

# Contoh Struktur Build

```text id="i6"
Aquascape.exe
config.json
InputFolder/
```

---

# Contoh config.json

```json id="i7"
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

# Pengaturan Folder Watcher

## Opsi 1 (Disarankan)

Biarkan:

```json id="i8"
"watchFolder": ""
```

Game otomatis menggunakan folder:

```text id="i9"
InputFolder/
```

---

## Opsi 2

Gunakan folder custom:

```json id="i10"
"watchFolder": "D:/AquascapeInput"
```

---

# Cara Menjalankan (Build)

1. Jalankan `Aquascape.exe`
2. Buka folder watcher
3. Masukkan file `.png` sesuai format nama
4. Objek akan otomatis muncul

---

# Cara Menjalankan (Project Unity)

1. Clone repository
2. Buka project menggunakan Unity `6000.3.0f1` atau `6000.3.12f1`
3. Buka scene utama
4. Tekan Play

---

# Struktur Script

```text id="i11"
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

# Tanggung Jawab Script

## TestWatcher.cs

Mengatur:

* Monitoring folder
* Scan file lama saat start
* Load PNG runtime
* Membuat sprite
* Spawn Fish / Trash
* Posisi spawn tidak overlap

## FishMovement.cs

Mengatur:

* Gerakan ikan
* AI mencari makanan
* State takut
* Sound effect

## Hunger.cs

Mengatur:

* Hunger meter
* Cooldown setelah kenyang

## TrashMovement.cs

Mengatur:

* Gerakan mengapung
* Mantul dari dinding
* Reaksi dorongan tabrakan

## Interaction.cs

Mengatur klik mouse player.

## ConfigManager.cs

Membaca file konfigurasi eksternal.

---

# Format File yang Didukung

Hanya:

```text id="i12"
.png
```

---

# File Tidak Valid

Nama file yang salah akan diabaikan secara aman.

Contoh:

```text id="i13"
fish.png
abc.png
gambar_test.png
```

---

# Teknologi yang Digunakan

* Unity Engine
* C#
* FileSystemWatcher
* JsonUtility
* Unity Input System

---

# Disclosure Penggunaan AI

AI digunakan untuk:

* Diskusi arsitektur
* Bantuan debugging
* Review logic
* Penyusunan dokumentasi

Seluruh implementasi, integrasi, testing, balancing, dan finalisasi project dilakukan secara manual.

---

# Submission

Disiapkan untuk:

```text id="i14"
Technical Test Game Developer 2026
```
