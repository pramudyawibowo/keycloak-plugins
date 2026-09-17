# 🛡️ Keycloak 26 Tailwind Custom Theme & Internal Slider Puzzle CAPTCHA (.JAR)

File `.jar` bundle mandiri (*all-in-one*) untuk **Keycloak 26 (Latest Quarkus)** yang berisi:
1. **Custom Login Theme** modern berbasis **Tailwind CSS** (mencakup seluruh halaman autentikasi).
2. **Internal Slider Jigsaw Puzzle CAPTCHA SPI Provider** (verifikasi geser kepingan puzzle jigsaw tanpa pihak ketiga, tanpa tebak huruf/angka).

---

## 📦 Lokasi File .JAR Siap Pasang

File hasil kompilasi Maven yang siap langsung disalin ke server dev Keycloak Anda:
```text
target/keycloak-captcha-tailwind-theme-26.0.0.jar
```

---

## 🚀 Cara Instalasi di Server Dev Keycloak 26

### Langkah 1: Salin File .JAR ke Direktori `providers/`
Salin file `.jar` ke folder `providers/` pada instalasi Keycloak 26 Anda di server dev:
```bash
cp target/keycloak-captcha-tailwind-theme-26.0.0.jar /path/to/keycloak-26/providers/
```

### Langkah 2: Jalankan / Rebuild Keycloak
Jika menjalankan Keycloak dalam mode production atau dev:
```bash
# Untuk mode dev:
bin/kc.sh start-dev

# Atau jika mode optimized build:
bin/kc.sh build
bin/kc.sh start
```
*(Keycloak akan secara otomatis mendeteksi tema `captcha-tailwind` dan provider `Internal Slider Puzzle CAPTCHA` dari dalam file `.jar`)*.

---

## ⚙️ Cara Mengaktifkan Tema & CAPTCHA di Admin Console

### 1. Mengaktifkan Tema Login (Tailwind)
1. Buka **Keycloak Admin Console** (`http://<server-ip>:8080/admin`).
2. Masuk ke realm Anda (misalnya `master` atau realm custom Anda).
3. Buka menu **Realm Settings** > tab **Localization** atau **Themes**.
4. Pada dropdown **Login theme**, pilih **`captcha-tailwind`**.
5. Klik **Save**.

---

### 2. Mengaktifkan Server-Side CAPTCHA pada Authentication Flow
Untuk memproteksi form login dengan validasi backend ketat:
1. Buka menu **Authentication** > tab **Flows**.
2. Pilih atau duplikat alur login (misalnya **Browser flow**).
3. Klik tombol **Add step** / **Add execution**.
4. Cari dan pilih provider **`Internal Slider Puzzle CAPTCHA`**.
5. Ubah requirement-nya menjadi **`REQUIRED`** (atau `ALTERNATIVE` sesuai kebutuhan).
6. Simpan konfigurasi flow.

Untuk memproteksi registrasi user baru:
1. Buka alur **Registration flow**.
2. Tambahkan step **`Internal Slider Puzzle CAPTCHA (Registration)`** sebagai **`REQUIRED`**.

---

## 🎨 Fitur Tema & Slider Puzzle CAPTCHA

- **Tailwind CSS Modern Dark Glassmorphism**: Tampilan modern, bersih, responsif, dan elegan.
- **Internal Slider Jigsaw Puzzle CAPTCHA (No 3rd Party)**:
  - Tanpa tebak teks / huruf / angka: Pengalaman pengguna (*user experience*) yang sangat interaktif dan menyenangkan.
  - Gambar latar belakang vektor artistik dengan lubang kepingan puzzle jigsaw dan irisan kepingan presisi.
  - Mendukung drag mouse pada PC/desktop, sentuhan jari (*touch screen*) pada mobile/smartphone, dan tombol panah keyboard.
  - Efek snap magnetik saat kepingan pas masuk ke dalam lubang.
  - Indikator feedback visual: hijau glowing & centang `✓` saat pas, merah getar (*shake*) saat meleset.
  - Tombol **Refresh** cepat untuk mengacak ulang gambar dan posisi lubang secara instan.
  - Validasi koordinat backend di Keycloak SPI dengan token enkripsi SHA-256 (tahan bot).
- **Cakupan Halaman Lengkap**:
  - `login.ftl` (Login + CAPTCHA)
  - `register.ftl` (Registrasi + CAPTCHA)
  - `logout-confirm.ftl` (Konfirmasi Logout)
  - `login-reset-password.ftl` (Reset Password + CAPTCHA)
  - `login-update-password.ftl` (Force Update Password)
  - `login-update-profile.ftl` (Update Profil Pengguna)
  - `login-verify-email.ftl` (Instruksi Verifikasi Email)
  - `login-page-expired.ftl` (Sesi Kedaluwarsa)
  - `login-totp.ftl` & `login-config-totp.ftl` (2FA OTP & QR Code)
  - `error.ftl`, `info.ftl`, `terms.ftl`
- **Multi-Bahasa**:
  - Bahasa Indonesia (`messages_id.properties`)
  - Bahasa Inggris (`messages_en.properties`)

---

## 🛠️ Cara Rebuild JAR (Jika Ada Perubahan di Kemudian Hari)

Jika Anda memodifikasi template FTL atau stylesheet di kemudian hari:
1. Recompile Tailwind:
   ```bash
   npx @tailwindcss/cli -i src/styles/input.css -o src/main/resources/theme/captcha-tailwind/login/resources/css/tailwind.css --minify
   ```
2. Build JAR dengan Maven:
   ```bash
   mvn clean package
   ```
File JAR baru akan selalu terbuat di `target/keycloak-captcha-tailwind-theme-26.0.0.jar`.
