# Lab7Web - Praktikum Pemrograman Web 2 (CodeIgniter 4)

Repositori ini berisi kumpulan tugas dan implementasi dari Praktikum Pemrograman Web 2 menggunakan framework PHP **CodeIgniter 4**. Proyek ini mencakup empat modul praktikum yang saling terhubung, dimulai dari konfigurasi dasar framework dan arsitektur MVC, hingga pembuatan sistem CRUD, manajemen View Layout, dan implementasi Modul Login dengan *Authentication Filter*.

---

## 📑 Daftar Isi
1. [Praktikum 1: Dasar CodeIgniter 4 & Arsitektur MVC](#praktikum-1-dasar-codeigniter-4--arsitektur-mvc)
2. [Praktikum 2: Framework Lanjutan (CRUD)](#praktikum-2-framework-lanjutan-crud)
3. [Praktikum 3: View Layout dan View Cell](#praktikum-3-view-layout-dan-view-cell)
4. [Praktikum 4: Modul Login & Filter Autentikasi](#praktikum-4-modul-login--filter-autentikasi)

---

## 🚀 Praktikum 1: Dasar CodeIgniter 4 & Arsitektur MVC
Praktikum pertama difokuskan pada pengenalan dasar *framework* CodeIgniter 4 dan pemahaman konsep Model-View-Controller (MVC). Konsep ini memisahkan kode program berdasarkan alur logika, pengolahan data, dan tampilan antarmuka.

**Langkah-langkah Utama:**
* **Persiapan Lingkungan:** Mengaktifkan ekstensi PHP yang dibutuhkan pada XAMPP (seperti `php-json`, `php-mysqlnd`, dan `php-intl`).
* **Instalasi & CLI:** Melakukan instalasi manual CodeIgniter 4 dan menggunakan antarmuka baris perintah (CLI) bawaan yaitu `php spark` untuk mempermudah pengembangan.
* **Mode Debugging:** Mengubah status variabel `CI_ENVIRONMENT` menjadi `development` pada file `.env` untuk memudahkan pelacakan *error*.
* **Routing & Controller:** Membuat pengaturan *routing* pada `app/Config/Routes.php` untuk mengarahkan URL ke Controller tertentu (seperti halaman Home, About, Contact, dan FAQ).
* **View & Layout Dasar:** Membuat file View untuk menampilkan halaman web dan menggabungkannya dengan aset CSS statis (`style.css`) yang diletakkan pada folder `public`.

> **Hasil Praktikum 1:**
> ![foto](https://github.com/Manueljds2311105/Lab2_7_Web/blob/6a2b4dd4b8d7933b42e353a7b23edb0700773b64/Web2%20Praktikum%201-4%20SS/Screenshot%202026-04-03%20152137.png)

---

## 📝 Praktikum 2: Framework Lanjutan (CRUD)
Praktikum kedua melanjutkan pengembangan dengan membangun fitur CRUD (*Create, Read, Update, Delete*) untuk entitas data Artikel.

**Langkah-langkah Utama:**
* **Persiapan Database:** Membuat database MySQL bernama `lab_ci4` beserta tabel `artikel`.
* **Konfigurasi Koneksi:** Menghubungkan aplikasi dengan database melalui file konfigurasi `.env`.
* **Pembuatan Model:** Menggunakan `ArtikelModel` untuk merepresentasikan tabel database dan menentukan variabel seperti `$primaryKey` dan `$allowedFields`.
* **Controller & View (Frontend):** Membuat *method* `index()` pada `Artikel` Controller untuk mengambil data dari database dan menampilkannya pada halaman utama *portal berita*, serta *method* `view()` untuk menampilkan detail artikel.
* **Menu Admin (Backend):** Membuat rute khusus admin untuk melakukan proses CRUD, yang meliputi penambahan data (Add), pengubahan data (Edit), dan penghapusan data (Delete).

> **Hasil Praktikum 2:**
> ![foto](https://github.com/Manueljds2311105/Lab2_7_Web/blob/4892197e5a4502419fc0157cd43ab2f66e0d37d8/Web2%20Praktikum%201-4%20SS/Screenshot%202026-04-03%20160058.png)
> ![foto](https://github.com/Manueljds2311105/Lab2_7_Web/blob/4892197e5a4502419fc0157cd43ab2f66e0d37d8/Web2%20Praktikum%201-4%20SS/Screenshot%202026-04-03%20155434.png)

---

## 🎨 Praktikum 3: View Layout dan View Cell
Praktikum ini merapikan struktur tampilan aplikasi menggunakan konsep **View Layout** dan **View Cell**. Pendekatan ini membuat manajemen tampilan menjadi lebih modular, rapi, dan efisien. Selain itu, bagian ini juga mencakup penyelesaian tugas akhir modul.

**Langkah-langkah Utama & Penyelesaian Tugas:**
* **View Layout Utama:** Membuat file `main.php` di dalam folder `layout` sebagai templat dasar halaman. File *view* lainnya dimodifikasi agar mewarisi tata letak ini menggunakan sintaks `extend` dan mengisi bagian konten dengan `section`.
* **Penyesuaian Database (Tugas):** Menambahkan kolom `created_at` (DATETIME) untuk mengurutkan artikel dari yang terbaru, serta menambahkan kolom `kategori` (VARCHAR) pada tabel `artikel` di database MySQL.
* **Implementasi View Cell Custom:** Membuat komponen widget dinamis `ArtikelTerkini`. *Catatan pengembangan:* Kode disesuaikan dengan standar CodeIgniter 4 terbaru dengan melepaskan *class* dari `extends Cell` untuk menghindari konflik (*Fatal Error*).
* **Filter Kategori Tertentu (Tugas):** Memodifikasi logika pada fungsi `render()` di View Cell `ArtikelTerkini` untuk mengambil datanya sendiri ke Model. Data difilter menggunakan query builder `where('kategori', 'Berita')` dan diurutkan menggunakan `orderBy('created_at', 'DESC')`.

**Jawaban Pertanyaan Modul:**
* **Manfaat View Layout:** Meningkatkan *reusability* (penggunaan ulang kode) dan efisiensi. Kita tidak perlu menulis struktur dasar HTML berulang kali. Jika ada perubahan desain dasar (seperti menu navigasi), cukup edit satu file layout utama saja dan perubahannya otomatis teraplikasikan ke seluruh halaman.
* **Perbedaan View Biasa & View Cell:** View biasa dikendalikan penuh oleh *Controller* utama yang harus mengambil dan menyuplai semua data. Sebaliknya, View Cell adalah komponen UI mandiri yang bisa mengambil datanya sendiri (memanggil *Model* secara langsung) tanpa membebani *Controller* utama. Sangat cocok untuk *widget* dinamis yang berulang di banyak halaman.

> **Hasil Praktikum 3:**
> ![foto](https://github.com/Manueljds2311105/Lab2_7_Web/blob/01884f9c657f42e0d15f88bd8b73f3566c7e301d/Web2%20Praktikum%201-4%20SS/Screenshot%202026-04-03%20170431.png)

---

## 🔒 Praktikum 4: Modul Login & Filter Autentikasi
Praktikum terakhir berfokus pada keamanan aplikasi dengan menambahkan sistem Login (Autentikasi). Sistem ini membatasi akses ke menu Admin, sehingga hanya pengguna yang terdaftar yang dapat mengelola artikel.

**Langkah-langkah Utama:**
* **Tabel & Model User:** Membuat tabel `user` (dengan struktur kolom username, useremail, dan userpassword) beserta `UserModel` untuk menangani data kredensial.
* **Database Seeder:** Men-generate data pengguna *dummy* (termasuk *hashing* password menggunakan `password_hash`) langsung ke database melalui CLI menggunakan fitur `Database Seeder`.
* **Modul Login & Session:** Mengembangkan antarmuka Login (`login.php`) dan mengelola logika validasi login pada Controller `User`. Jika data cocok, informasi pengguna akan disimpan di dalam `session`. Fungsi logout juga ditambahkan untuk menghancurkan *session* saat ini.
* **Auth Filter:** Membatasi rute URL menggunakan *Filters*. Sebuah filter bernama `Auth` dibuat untuk mengecek keberadaan sesi login. Filter ini kemudian disisipkan ke dalam *route group* `admin`, yang secara otomatis akan menendang pengguna ke halaman login jika mencoba mengakses halaman admin tanpa sesi yang sah.

> **Hasil Praktikum 4:**
> ![foto](https://github.com/Manueljds2311105/Lab2_7_Web/blob/01884f9c657f42e0d15f88bd8b73f3566c7e301d/Web2%20Praktikum%201-4%20SS/Screenshot%202026-04-03%20170315.png)

---

## 📌 Praktikum 5: Pagination dan Pencarian

Pada praktikum ke-5 ini, fokus utama adalah mengoptimalkan tampilan dan pencarian data artikel pada halaman Admin.

### 1. Membuat Pagination
Pagination berfungsi untuk memecah tampilan data yang panjang menjadi beberapa halaman agar lebih rapi dan mempercepat waktu *loading* halaman. 
- **Controller:** Memanfaatkan fungsi `paginate()` bawaan CI4 pada `ArtikelModel` dengan batas 10 *record* per halaman.
- **View:** Menambahkan kode `<?= $pager->links(); ?>` di bawah tabel `admin_index.php` untuk memunculkan tombol navigasi halaman.

**Screenshot Hasil Pagination:**
![foto](https://github.com/Manueljds2311105/Lab2_7_Web/blob/123d9b42ae5b89f530c21410db30e4cd9070dadd/Web2%20Praktikum%201-4%20SS/Screenshot%202026-04-09%20104630.png)

### 2. Membuat Pencarian (Search)
Fitur pencarian digunakan untuk memfilter data artikel berdasarkan judul[cite: 71].
- **Controller:** Menangkap keyword dari form pencarian menggunakan `$this->request->getVar('q')` dan memfilternya menggunakan Query Builder `like('judul', $q)`.
- [cite_start]**View:** Menambahkan form HTML pencarian dengan method `GET` dan memastikan link pagination tetap membawa parameter pencarian dengan `$pager->only(['q'])->links()`.

**Screenshot Hasil Pencarian:**
![foto](https://github.com/Manueljds2311105/Lab2_7_Web/blob/123d9b42ae5b89f530c21410db30e4cd9070dadd/Web2%20Praktikum%201-4%20SS/Screenshot%202026-04-09%20104713.png)

---

## 📌 Praktikum 6: Relasi Tabel dan Query Builder

Pada praktikum ke-6 ini, dilakukan perombakan struktur database untuk menerapkan relasi *One-to-Many* dan menggunakan Query Builder untuk melakukan operasi `JOIN`.

### 1. Persiapan Database & Relasi Tabel
- Membuat tabel baru bernama `kategori` untuk menyimpan daftar kategori.
- Menambahkan kolom `id_kategori` sebagai *Foreign Key* pada tabel `artikel` agar saling terhubung.

### 2. Memodifikasi Model & Menggunakan Query Builder (JOIN)
- Membuat `KategoriModel` untuk berinteraksi dengan tabel kategori.
- Memodifikasi `ArtikelModel` dengan menambahkan fungsi baru yang menggunakan `->join('kategori', 'kategori.id_kategori = artikel.id_kategori')` agar nama kategori bisa ditarik bersamaan dengan data artikel.

### 3. Memodifikasi Controller & View (Form & Dropdown)
- **Controller:** Mengambil data kategori menggunakan `KategoriModel->findAll()` lalu mengirimkannya ke view untuk keperluan form Tambah, Edit, dan Filter.
- **View:** Mengubah input kategori yang awalnya statis/tidak ada menjadi *Dropdown* dinamis (`<select>`) menggunakan perulangan *foreach* pada form Add dan form Edit.

### 4. Penyelesaian Tugas Praktikum
- **Detail Artikel:** Memodifikasi `Artikel.php` fungsi `view()` menggunakan metode *JOIN*, sehingga pada halaman `artikel/detail.php` kini dapat menampilkan Nama Kategori artikel yang sedang dibaca.
- **Improvisasi:** Melakukan perbaikan validasi form tambah/edit dan menangani isu *foreign key* saat update artikel lama yang nilai kategorinya masih kosong/NULL.

**Screenshot Dashboard Admin (Data dengan Kategori):**
![foto](https://github.com/Manueljds2311105/Lab2_7_Web/blob/123d9b42ae5b89f530c21410db30e4cd9070dadd/Web2%20Praktikum%201-4%20SS/Screenshot%202026-04-22%20201004.png)

**Screenshot Form Tambah/Edit (Dropdown Kategori):**
![foto](https://github.com/Manueljds2311105/Lab2_7_Web/blob/123d9b42ae5b89f530c21410db30e4cd9070dadd/Web2%20Praktikum%201-4%20SS/Screenshot%202026-04-22%20200658.png)

---

**Dikerjakan Oleh:**
Manuel (Manueljds2311105)

*Proyek ini dikembangkan sebagai bagian dari Modul Praktikum Pemrograman Web 2 Universitas Pelita Bangsa.*
