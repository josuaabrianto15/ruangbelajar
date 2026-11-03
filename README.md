# Ruang Belajar

Website Ruang Belajar dibangun dengan Laravel 13 dan Vite untuk manajemen konten program belajar.

## Requirements

- PHP >= 8.3
- Composer
- Node.js & NPM
- SQLite (atau database lain sesuai konfigurasi)

## Cara Menjalankan Aplikasi

### Opsi 1: Menggunakan Laragon (Recommended untuk Windows)

1. **Install dan Jalankan Laragon**
   - Download dan install Laragon dari [laragon.org](https://laragon.org/)
   - Start Laragon

2. **Clone atau Letakkan Project**
   ```bash
   # Project sudah ada di: C:\laragon\www\ruangbelajar-main
   ```

3. **Buka Terminal Laragon**
   - Klik tombol "Terminal" di Laragon, atau
   - Klik kanan icon Laragon di system tray → Terminal

4. **Masuk ke Direktori Project**
   ```bash
   cd C:\laragon\www\ruangbelajar-main
   ```

5. **Install Dependencies**
   ```bash
   # Install PHP dependencies
   composer install

   # Install Node.js dependencies
   npm install
   ```

6. **Setup Database**
   ```bash
   # Jalankan migrasi database
   php artisan migrate

   # (Opsional) Seed data awal
   php artisan db:seed

   # Buat akun admin
   php artisan db:seed --class=AdminSeeder
   ```

7. **Build Frontend Assets**
   ```bash
   npm run build
   ```

8. **Jalankan Development Server**
   ```bash
   # Opsi 1: Server sederhana
   php artisan serve

   # Opsi 2: Development lengkap dengan queue, logs, dan vite
   composer run dev
   ```

9. **Akses Website**
   - Buka browser dan akses: **http://localhost:8000**
   - Untuk admin panel: **http://localhost:8000/admin/login**

### Opsi 2: Menggunakan Command Line Manual

Jika PHP dan Composer sudah ada di PATH sistem Anda:

```bash
# 1. Masuk ke direktori project
cd C:\laragon\www\ruangbelajar-main

# 2. Install dependencies
composer install
npm install

# 3. Setup environment (jika belum ada .env)
cp .env.example .env
php artisan key:generate

# 4. Setup database
php artisan migrate
php artisan db:seed --class=AdminSeeder

# 5. Build assets
npm run build

# 6. Jalankan server
php artisan serve
```

### Opsi 3: Menggunakan Path Lengkap (Jika PHP tidak di PATH)

```powershell
# Install dependencies
C:\laragon\bin\php\php-8.3.30-Win32-vs16-x64\php.exe C:\laragon\bin\composer\composer.phar install
C:\laragon\bin\nodejs\node-v22\npm.cmd install

# Setup database
C:\laragon\bin\php\php-8.3.30-Win32-vs16-x64\php.exe artisan migrate
C:\laragon\bin\php\php-8.3.30-Win32-vs16-x64\php.exe artisan db:seed --class=AdminSeeder

# Build assets
C:\laragon\bin\nodejs\node-v22\npm.cmd run build

# Jalankan server
C:\laragon\bin\php\php-8.3.30-Win32-vs16-x64\php.exe artisan serve
```

## Kredensial Admin Default

Setelah menjalankan `AdminSeeder`, gunakan kredensial berikut untuk login:

- **Email:** `admin@ruangbelajar.id`
- **Password:** `admin123`

⚠️ **Penting:** Segera ganti password setelah login pertama kali untuk keamanan!

## Struktur Project

```
ruangbelajar-main/
├── app/
│   ├── Http/Controllers/
│   │   ├── Admin/          # Controller untuk admin panel
│   │   └── User/           # Controller untuk frontend user
│   └── Models/             # Eloquent models
├── database/
│   ├── migrations/         # Database migrations
│   └── seeders/            # Database seeders
├── public/                 # Public assets
├── resources/
│   ├── views/              # Blade templates
│   ├── js/                 # JavaScript files
│   └── css/                # CSS files
└── routes/
    └── web.php             # Web routes
```

## Perintah Berguna

```bash
# Menjalankan migrasi
php artisan migrate

# Rollback migrasi terakhir
php artisan migrate:rollback

# Refresh database (reset & migrate ulang)
php artisan migrate:fresh

# Seed database dengan data dummy
php artisan db:seed

# Clear cache
php artisan cache:clear
php artisan config:clear
php artisan view:clear

# Generate sitemap
php artisan sitemap:generate

# Development mode dengan hot reload
npm run dev

# Build untuk production
npm run build
```

## Troubleshooting

### Error: "composer: command not found"
- Pastikan Laragon sudah berjalan
- Gunakan terminal bawaan Laragon, atau
- Tambahkan Laragon ke PATH sistem Windows

### Error: Database tidak ditemukan
```bash
# Pastikan file database.sqlite ada
touch database/database.sqlite

# Jalankan migrasi ulang
php artisan migrate
```

### Port 8000 sudah digunakan
```bash
# Gunakan port lain
php artisan serve --port=8001
```

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
