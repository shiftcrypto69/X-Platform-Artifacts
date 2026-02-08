# 📦 X-Platform-Artifacts: Engineering The Delivery

![Release](https://img.shields.io/badge/Release-v1.0.0-orange?style=for-the-badge)
![Ecosystem](https://img.shields.io/badge/Artifacts-DEB%20%7C%20APK%20%7C%20IPA-brightgreen?style=for-the-badge)
![Status](https://img.shields.io/badge/Focus-Distribution--Engineering-blue?style=for-the-badge)

Direka secara sistematik untuk repository X-Platform-Artifacts dan berfungsi sebagai manual operasi (SOP) untuk anda menukarkan kod mentah kepada fail yang boleh dipasang (installable packages).

> **"Code is useless if it cannot be deployed."** > Repository ini adalah pusat dokumentasi teknikal dan eksperimen untuk membina, membungkus (packaging), dan mengedarkan perisian merentas platform utama: **Linux**, **Android**, dan **iOS**.

---

## 🧭 Navigasi Roadmap

Sebelum kita memodifikasi kernel di `AOSP-Kernel-Lab`, kita mesti mahir dalam pengurusan fail dan struktur binari di sini:

1.  **Struktur Fail System:** Memahami lokasi standard `/usr/bin`, `/etc`, dan `/opt`.
2.  **Metadata & Dependencies:** Belajar cara memberitahu sistem operasi apa yang diperlukan oleh aplikasi kita.
3.  **Kitaran Hayat Kompilasi:** Dari kod sumber (C++/Java/Web) -> Binari -> Artifact.

---

## 🛠️ Modul Pembelajaran Teknikal

### 1. Ekosistem Debian (`.deb`)
Piawaian untuk Ubuntu, Kali Linux, dan Debian. Fokus kepada penggunaan `dpkg` dan `apt`.
* **Struktur Wajib:** Folder `DEBIAN` yang mengandungi fail `control`.
* **Perintah Utama:**
    ```bash
    # Membina pakej dari folder
    dpkg-deb --build <nama-folder>
    ```

### 2. Ekosistem Android (`.apk` / `.aab`)
Langkah awal sebelum masuk ke tahap **AOSP Modding**.
* **Struktur:** Memahami `classes.dex`, `resources.arsc`, dan `AndroidManifest.xml`.
* **Proses Signing:** Menggunakan `keytool` dan `apksigner` untuk keselamatan integriti aplikasi.

### 3. Ekosistem Apple (`.ipa`)
Memahami sistem fail Darwin dan struktur bundle `.app`.
* **Fokus:** Mach-O binaries dan *Code Signing entitlements*.

---

## 🧪 Latihan Praktikal: Pakej Debian Pertama (WSL)

Ikuti langkah ini dalam terminal **Ubuntu-WSL** anda untuk memahami konsep *Artifact*:

### Langkah 1: Bina Struktur
```bash
mkdir -p my-artifact/DEBIAN
mkdir -p my-artifact/usr/local/bin

Langkah 2: Cipta Fail Metadata (control)
Fail ini sangat kritikal. Gunakan perintah ini:
cat <<EOF > my-artifact/DEBIAN/control
Package: mastery-tool
Version: 1.0.0
Section: utils
Priority: optional
Architecture: all
Maintainer: shiftcrypto69
Description: Alat pertama hasil pembelajaran Mastery-Core.
EOF

Langkah 3: Bina Fail Binari
dpkg-deb --build my-artifact

Hasilnya: Anda akan mendapat fail my-artifact.deb yang boleh dipasang pada mana-mana sistem Debian!
📊 Matlamat Pencapaian (Milestones)
 * [ ] Level 1: Berjaya membina fail .deb secara manual.
 * [ ] Level 2: Berjaya melakukan sideload .apk yang dibina sendiri ke peranti Android.
 * [ ] Level 3: Membina skrip automasi (CI/CD) untuk membungkus aplikasi secara automatik.
🔗 Hubungan Projek
Projek ini adalah sebahagian daripada ekosistem Mastery Core:
 * Pusat Kawalan: Mastery-Core-Central
 * Asas Fizikal: Ground-Zero-Semiconductor
Maintainer: shiftcrypto69
“Building tools today to build systems tomorrow.”

---

