````md
# 🐠 Aquascape Technical Test - Unity Project

<p align="center">
  <img src="https://img.shields.io/badge/Unity-6000.3.0f1-black?style=for-the-badge&logo=unity" />
  <img src="https://img.shields.io/badge/Platform-Windows-blue?style=for-the-badge&logo=windows" />
  <img src="https://img.shields.io/badge/Language-C%23-purple?style=for-the-badge&logo=csharp" />
</p>

<h1 align="center">🐟 Aquascape Simulation Game</h1>

<p align="center">
Realtime file-based spawning system that converts external <b>.png</b> files into live in-game entities.
</p>

---

## 📌 Overview

Project ini adalah game simulasi **Aquascape 2D** yang dibuat menggunakan **Unity**.

Gameplay utama mengubah file gambar **`.png`** yang dimasukkan ke folder tertentu menjadi objek di dalam game secara **real-time**.

Objek yang dapat di-spawn:

- 🐟 **Fish** → entitas hidup dengan AI movement & hunger system  
- 🗑 **Trash** → sampah mengapung di aquarium  

---

## 🎮 Main Features

### 🖼 Realtime File Spawning

Menggunakan **FileSystemWatcher** untuk memantau folder.

Saat file baru dimasukkan:

```text
FISH_[TYPE]_[TIMESTAMP].png
TRASH_[TYPE]_[TIMESTAMP].png
````

Contoh:

```text
FISH_NEMO_20260401170000.png
TRASH_BOTTLE_20260401170100.png
```

➡️ Objek langsung spawn di game tanpa rebuild.

---

### 🐟 Fish Behavior

* Random swimming movement
* Hunger system
* Search nearest food
* Stop eating when full
* Scare / flee when clicked
* Sound effect interaction

---

### 🗑 Trash Behavior

* Floating movement
* Bounce from wall
* Pushed by fish collision

---

### 🖱 Player Interaction

| Action                | Result             |
| --------------------- | ------------------ |
| Left Click Empty Area | Spawn food         |
| Left Click Fish       | Fish scared & flee |
| Left Click Trash      | Destroy trash      |

---

## ⚙️ Config System

Gameplay dapat diubah tanpa rebuild menggunakan:

```text
config.json
```

Contoh:

```json
{
  "watchFolder": "",
  "fishMinSpeed": 1.5,
  "fishMaxSpeed": 3,
  "fishDetectionRadius": 15
}
```

---

## 📂 Build Structure

```text
Aquascape.exe
config.json
InputFolder/
```

---

## 🚀 How To Run

### Build Version

1. Jalankan **Aquascape.exe**
2. Buka folder watcher
3. Masukkan file `.png`
4. Objek spawn otomatis

### Unity Project

1. Clone repository
2. Open with **Unity 6000.3.0f1**
3. Press **Play**

---

## 🧠 Script Architecture

```text
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
```

---

## 🛠 Tech Stack

<p align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/csharp/csharp-original.svg" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/unity/unity-original.svg" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/vscode/vscode-original.svg" height="40"/>
</p>

---

## 🤖 AI Usage Disclosure

AI digunakan untuk:

* Diskusi arsitektur
* Debugging guidance
* Code review suggestion
* Dokumentasi

Seluruh implementasi, integrasi, dan finalisasi dilakukan secara manual.

---

## 👨‍💻 Developer

**Hikari Aufa Yafi**
Game Programmer | Unity Developer

<p align="left">
  <a href="https://www.linkedin.com/in/hikariaufa/">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" height="35"/>
  </a>
</p>
```
