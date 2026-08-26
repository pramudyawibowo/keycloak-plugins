# 🛡️ Keycloak Plugins & Themes

Kumpulan plugin dan tema siap pakai untuk Keycloak.

## 📦 1. Keycloak 26 Tailwind Theme & Internal CAPTCHA

- **File JAR**: [`keycloak-captcha-tailwind-theme-26.0.0.jar`](keycloak-captcha-tailwind-theme-26.0.0.jar)
- **Kompatibilitas**: Keycloak 26.x (Quarkus)
- **Fitur**:
  - Tema Login modern berbasis **Tailwind CSS** (Dark Glassmorphism, Responsive, Multi-bahasa ID & EN).
  - Provider **Internal Image CAPTCHA (Alfanumerik Acak)** tanpa pihak ketiga (dilengkapi tombol Refresh & Audio Accessibility).

### 🚀 Cara Download Langsung di Kubernetes (initContainer)

```bash
wget -O /opt/keycloak/providers/keycloak-captcha-tailwind-theme-26.0.0.jar \
  https://raw.githubusercontent.com/pramudyawibowo/keycloak-plugins/main/keycloak-captcha-tailwind-theme-26.0.0.jar
```

atau menggunakan `curl`:

```bash
curl -sSL -o /opt/keycloak/providers/keycloak-captcha-tailwind-theme-26.0.0.jar \
  https://raw.githubusercontent.com/pramudyawibowo/keycloak-plugins/main/keycloak-captcha-tailwind-theme-26.0.0.jar
```
