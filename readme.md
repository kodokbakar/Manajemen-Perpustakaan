# Sistem Manajemen Perpustakaan Web 📚

![Laravel](https://img.shields.io/badge/Laravel-11.x-red.svg)
![Vue.js](https://img.shields.io/badge/Vue.js-3.x-green.svg)
![PHP](https://img.shields.io/badge/PHP-8.2+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

Sistem Manajemen Perpustakaan Web adalah aplikasi fullstack yang dibangun dengan Laravel (backend) dan Vue.js (frontend) untuk mengelola operasional perpustakaan secara digital.

## 🌟 Fitur Utama

### 📖 Manajemen Buku
- ✅ Tambah, edit, hapus, dan lihat daftar buku
- 📸 Upload sampul buku dengan Intervention Image
- 🏷️ Kategorisasi buku
- 📊 Manajemen stok buku
- 🔍 Pencarian dan filter buku

### 👥 Manajemen Anggota
- 👤 Registrasi dan profil anggota
- 📝 Riwayat peminjaman anggota
- ✏️ Edit data anggota

### 📅 Manajemen Peminjaman
- 📚 Proses peminjaman buku
- ↩️ Proses pengembalian buku
- 📋 Riwayat peminjaman
- ⏰ Tracking tanggal jatuh tempo

### 🗂️ Manajemen Kategori
- 📁 Tambah, edit, hapus kategori buku
- 🔗 Organisasi buku berdasarkan kategori

### 📊 Laporan dan Dashboard
- 📈 Dashboard admin dengan statistik
- 📋 Laporan peminjaman
- 📊 Visualisasi data dengan Chart.js

### 🔐 Autentikasi & Otorisasi
- 🔑 Login/logout untuk admin dan anggota
- 🛡️ API authentication dengan Laravel Sanctum
- 👮 Role-based access control

## 🏗️ Arsitektur Sistem

```
web_perpustakaan/
├── backend/          # Laravel API Backend
│   ├── app/
│   │   ├── Http/Controllers/
│   │   └── Models/
│   ├── database/
│   │   ├── migrations/
│   │   └── seeders/
│   └── routes/
└── frontend/         # Vue.js Frontend
    ├── src/
    │   ├── components/
    │   ├── views/
    │   ├── router/
    │   └── services/
    └── public/
```

## 🛠️ Teknologi yang Digunakan

### Backend
- **Framework**: Laravel 11.x
- **Database**: SQLite (dapat diganti dengan MySQL/PostgreSQL)
- **Authentication**: Laravel Sanctum
- **Image Processing**: Intervention Image
- **API**: RESTful API

### Frontend
- **Framework**: Vue.js 3.x
- **Routing**: Vue Router 4.x
- **State Management**: Vuex 4.x
- **HTTP Client**: Axios
- **UI Framework**: Bootstrap 5.x
- **Charts**: Chart.js
- **Build Tool**: Vue CLI

## 📋 Prasyarat

Pastikan sistem Anda telah terinstal:

- **PHP** >= 8.2
- **Composer** 
- **Node.js** >= 16.x
- **npm** atau **yarn**
- **SQLite** (atau database lain sesuai konfigurasi)

## 🚀 Instalasi

### 1. Clone Repository
```bash
git clone https://github.com/kodokbakar/Manajemen-Perpustakaan.git
cd web_perpustakaan
```

### 2. Setup Backend (Laravel)
```bash
cd backend

# Install dependencies
composer install

# Copy environment file
cp .env.example .env

# Generate application key
php artisan key:generate

# Jalankan migrasi dan seeder
php artisan migrate --seed

# Generate Sanctum secret key
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"

# Start development server
php artisan serve
```

Backend akan berjalan di `http://localhost:8000`

### 3. Setup Frontend (Vue.js)
```bash
cd frontend

# Install dependencies
npm install

# Start development server
npm run serve
```

Frontend akan berjalan di `http://localhost:8080`

## ⚙️ Konfigurasi

### Database
Aplikasi ini menggunakan SQLite secara default. Untuk menggunakan database lain:

1. Edit file `.env` di folder backend
2. Sesuaikan konfigurasi database:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=perpustakaan_db
DB_USERNAME=root
DB_PASSWORD=
```

### API Endpoint
Pastikan frontend terhubung dengan backend dengan benar di file `frontend/src/services/api.js`:
```javascript
const API_BASE_URL = 'http://localhost:8000/api';
```

## 📚 API Documentation

### Authentication
- `POST /api/login` - Login pengguna
- `POST /api/logout` - Logout pengguna
- `POST /api/register` - Registrasi anggota baru

### Books
- `GET /api/books` - Ambil semua buku
- `POST /api/books` - Tambah buku baru
- `GET /api/books/{id}` - Detail buku
- `PUT /api/books/{id}` - Update buku
- `DELETE /api/books/{id}` - Hapus buku

### Categories
- `GET /api/categories` - Ambil semua kategori
- `POST /api/categories` - Tambah kategori baru
- `PUT /api/categories/{id}` - Update kategori
- `DELETE /api/categories/{id}` - Hapus kategori

### Members
- `GET /api/members` - Ambil semua anggota
- `POST /api/members` - Tambah anggota baru
- `GET /api/members/{id}` - Detail anggota
- `PUT /api/members/{id}` - Update anggota

### Loans
- `GET /api/loans` - Ambil semua peminjaman
- `POST /api/loans` - Buat peminjaman baru
- `PUT /api/loans/{id}/return` - Kembalikan buku

## 🗄️ Struktur Database

### Tables
- **users** - Data pengguna sistem
- **categories** - Kategori buku
- **books** - Data buku perpustakaan
- **members** - Data anggota perpustakaan
- **loans** - Data peminjaman buku

### Relationships
- Book belongs to Category
- Loan belongs to Book and Member
- User dapat memiliki berbagai role

## 🎨 Komponen Frontend

### Pages/Views
- **Homepage** - Halaman utama
- **Dashboard** - Dashboard admin
- **Login** - Halaman login

### Components
- **books/** - Komponen manajemen buku
- **categories/** - Komponen manajemen kategori
- **members/** - Komponen manajemen anggota
- **loans/** - Komponen manajemen peminjaman
- **reports/** - Komponen laporan

## 🧪 Testing

### Backend Testing
```bash
cd backend
php artisan test
```

### Frontend Testing
```bash
cd frontend
npm run test
```

## 🔧 Development

### Backend Development
- Gunakan `php artisan serve` untuk development server
- Gunakan `php artisan tinker` untuk testing di console
- Check logs di `storage/logs/laravel.log`

### Frontend Development
- Gunakan `npm run serve` untuk hot-reload development
- Gunakan `npm run lint` untuk code linting

## 🤝 Kontribusi

1. Fork repository ini
2. Buat branch fitur baru (`git checkout -b feature/AmazingFeature`)
3. Commit perubahan (`git commit -m 'Add some AmazingFeature'`)
4. Push ke branch (`git push origin feature/AmazingFeature`)
5. Buat Pull Request

## 📄 Lisensi

Proyek ini dilisensikan di bawah [MIT License](LICENSE).

## 👨‍💻 Developer

- **GitHub**: [kodokbakar](https://github.com/kodokbakar)

## 📞 Support

Jika ada pertanyaan atau bug, silakan buat [issue](https://github.com/kodokbakar/Manajemen-Perpustakaan/issues) di repository ini.


**Made with ❤️ by [kodokbakar](https://github.com/kodokbakar)**