# Laporan Praktikum 4: Implementasi Modul Login dan Filter

Repository ini telah diperbarui dengan modul autentikasi. Fokus praktikum kali ini adalah mengamankan halaman administrasi menggunakan Sistem Login dan Auth Filter di CodeIgniter 4.

# Fitur Baru pada Praktikum 4
1. Sistem Autentikasi: Memastikan hanya pengguna terdaftar yang bisa masuk ke menu admin.

2. Auth Filter: "Satpam" otomatis yang menjaga URL /admin/* dari akses ilegal.

3. Database Seeding: Pengisian data user admin secara otomatis melalui CLI.

4. Session Management: Menyimpan data login pengguna selama sesi browsing berlangsung.

# Langkah-Langkah Pengerjaan

1. Persiapan Tabel Database

   Membuat tabel user untuk menampung data kredensial (username, email, password) dengan field password yang mendukung enkripsi password_hash.

2. Pembuatan Model dan Controller

   - UserModel: Mengatur interaksi data dengan tabel user.
   - Controller User: Berisi logika untuk proses login (verifikasi email & password) dan proses logout (destroy session).

3. Implementasi Filter (Keamanan)
   
   Membuat file Auth.php di folder app/Filters yang berfungsi mengecek session logged_in. Jika user belum login, mereka akan diarahkan secara otomatis ke halaman login. Filter ini kemudian didaftarkan di Config/Filters.php.

4. Konfigurasi Routes

   Mengelompokkan semua route admin (/admin/artikel, /admin/add, dll) ke dalam satu grup yang diproteksi oleh filter auth.

# Struktur Folder Setelah Pembaruan

app/

├── Config/

│   ├── Filters.php      (Pendaftaran alias 'auth')

│   └── Routes.php       (Proteksi grup admin dengan filter)

├── Controllers/

│   └── User.php         (Logika Login & Logout)

├── Filters/

│   └── Auth.php         (Logika pengecekan session)

├── Models/

│   └── UserModel.php    (Model untuk tabel user)

└── Views

    └── user/
    
        └── login.php    Tampilan form login/Sign In)

# Cara Penggunaan

1. Pastikan server Apache dan MySQL di XAMPP sudah berjalan .
   
2. Masukkan data user admin melalui terminal (jalankan di dalam folder ci4):
   
   - php spark db:seed UserSeeder
     
3. Akses halaman login di: http://localhost:8080/user/login.
   
4. Login menggunakan akun default:
   
   - Email: admin@email.com
     
   - Password: admin123
  
# Hasil Praktikum (Screenshot)

1. Halaman Sign In

   <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0323e9fd-dca9-4468-a4fc-43cbfeb34ddb" />

3. Notifikasi Login Gagal

   <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5ca56ddd-a6a9-4412-9534-602757364a23" />

5. Berhasil Masuk Dashboard Admin

   <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bc9ed409-39ff-4216-9f7c-028dd13d6421" />

