### Struktur Tabel: tr_hr_pelamar_account

| Kolom            | Tipe Data   | Aturan/Relasi                      | Deskripsi |
|------------------|-------------|------------------------------------|-----------|
| tr_hr_pelamar_id | varchar(50) | PRIMARY KEY, NOT NULL (relasi ke pelamar)| ID pelamar, relasi ke pelamar utama |
| bank_acc         | varchar(50) |                                    | Nomor rekening bank pelamar |
| ktp              | varchar(50) |                                    | Nomor KTP pelamar |
| ms_bank_id       | varchar(50) | (relasi ke master bank)            | Relasi ke master bank |

**Catatan:**
- Setiap record account terhubung ke pelamar melalui kolom `tr_hr_pelamar_id`.

### Struktur Tabel: ms_hr_status_pelamar

| Kolom                   | Tipe Data   | Aturan/Relasi         | Deskripsi |
|-------------------------|-------------|-----------------------|-----------|
| ms_hr_status_pelamar_id | varchar(50) | PRIMARY KEY, NOT NULL | ID status pelamar |

**Catatan:**
- Tabel master status pelamar, digunakan untuk referensi status proses rekrutmen.
### Struktur Tabel: tr_hr_pelamar_sosmed

| Kolom                | Tipe Data        | Aturan/Relasi               | Deskripsi |
|----------------------|------------------|-----------------------------|-----------|
| tr_hr_pelamar_sosmed | int              | PRIMARY KEY, NOT NULL       | ID unik sosial media pelamar |
| sosmed_link          | nvarchar(max)    |                             | Link ke profil sosial media |
| tr_hr_pelamar_id     | varchar(50)      | (relasi ke pelamar)         | Relasi ke pelamar utama |
| sosmed_user          | varchar(50)      |                             | Username akun sosial media |
| sosmed_type          | varchar(50)      |                             | Jenis platform (Facebook, Instagram, dll) |
| date_created         | date             |                             | Tanggal data dibuat |
| user_created         | varchar(50)      |                             | User yang membuat data |

**Catatan:**
- Setiap record sosial media pelamar terhubung ke pelamar melalui kolom `tr_hr_pelamar_id`.
- Kolom `sosmed_type` untuk jenis platform (misal: Facebook, Instagram, dll).
### Struktur Tabel: tr_hr_pelamar_skedul

| Kolom                | Tipe Data   | Aturan/Relasi                            | Deskripsi |
|----------------------|-------------|-------------------------------------------|-----------|
| tr_hr_pelamar_id     | varchar(50) | PRIMARY KEY, NOT NULL (relasi ke pelamar) | ID pelamar, relasi ke pelamar utama |
| skedul_pelamar_time  | datetime    |                                           | Waktu jadwal interview yang diinputkan sistem atau pelamar |
| skedul_confirmed     | datetime    |                                           | Waktu persetujuan jadwal oleh admin HRD, menandakan jadwal sudah disetujui |

**Catatan:**
- Setiap record skedul terhubung ke pelamar melalui kolom `tr_hr_pelamar_id`.
- Menyimpan waktu jadwal interview dan waktu konfirmasi kehadiran.
### Struktur Tabel: tr_hr_pelamar_personal

| Kolom             | Tipe Data    | Aturan/Relasi               | Deskripsi |
|-------------------|--------------|-----------------------------|-----------|
| tr_hr_pelamar_id  | varchar(50)  | PRIMARY KEY, NOT NULL (relasi ke pelamar) | ID pelamar, relasi ke pelamar utama |
| date_lahir        | date         |                             | Tanggal lahir pelamar |
| kota_lahir        | varchar(50)  |                             | Kota kelahiran pelamar |
| alamat            | varchar(50)  |                             | Alamat domisili pelamar |
| jenis             | varchar(50)  |                             | Jenis kelamin pelamar |
| agama             | varchar(50)  |                             | Agama pelamar |
| nama              | varchar(50)  |                             | Nama lengkap pelamar |
| pendidikan        | varchar(50)  |                             | Pendidikan terakhir |
| cek_pengalaman    | bit          |                             | Apakah pelamar memiliki pengalaman kerja (boolean) |

**Catatan:**
- Setiap record personal terhubung ke pelamar melalui kolom `tr_hr_pelamar_id`.
- Kolom `cek_pengalaman` bertipe bit (boolean) untuk menandai apakah pelamar memiliki pengalaman kerja.
### Struktur Tabel: tr_hr_pelamar_pengalaman_perusahaan


| Kolom                      | Tipe Data      | Aturan/Relasi               | Deskripsi |
|----------------------------|----------------|-----------------------------|-----------|
| tr_hr_pelamar_pengalaman_id| int (IDENTITY) | PRIMARY KEY, NOT NULL       | ID unik pengalaman kerja (auto increment) |
| tr_hr_pelamar_id           | varchar(50)    | NOT NULL (relasi ke pelamar)| Relasi ke pelamar utama |
| perusahaan                 | varchar(50)    | NOT NULL                    | Nama perusahaan tempat bekerja |
| tgl_start                  | date           | NOT NULL                    | Tanggal mulai bekerja |
| tgl_end                    | date           | NOT NULL                    | Tanggal selesai bekerja |
| hp_hrd                     | varchar(50)    | NOT NULL                    | Nomor HP HRD perusahaan lama |
| nama_hrd                   | varchar(50)    | NOT NULL                    | Nama HRD perusahaan lama |
| hp_atasan                  | varchar(50)    | NOT NULL                    | Nomor HP atasan langsung |
| alasan_resign              | text           | NOT NULL                    | Alasan resign dari perusahaan tersebut |
| jabatan_akhir              | varchar(50)    |                             | Jabatan terakhir di perusahaan |
| jabatan_awal               | varchar(50)    |                             | Jabatan awal di perusahaan |
| gaji_awal                  | money          | NOT NULL                    | Gaji awal saat masuk |
| gaji_akhir                 | money          | NOT NULL                    | Gaji terakhir saat keluar |
| sukses_rating              | int            |                             | Radio -3 s/d +3, caption: "Menurut anda, seberapa sukses anda di perusahaan ini?" |
| sukses_keterangan          | text           |                             | Penjelasan tambahan untuk sukses_rating |
| sulit_rating               | int            |                             | Radio -3 s/d +3, caption: "Seberapa besar kesulitan yang anda hadapi di perusahaan ini?" |
| sulit_keterangan           | text           |                             | Penjelasan tambahan untuk sulit_rating |
| puas_rating                | int            |                             | Radio -3 s/d +3, caption: "Seberapa puas anda bekerja di sana?" |
| puas_keterangan            | text           |                             | Penjelasan tambahan untuk puas_rating |
| masalah_rating             | int            |                             | Radio -3 s/d +3, penilaian masalah utama |
| masalah_keterangan         | text           |                             | Penjelasan tambahan untuk masalah_rating |
| kesalahan_paling_besar     | text           |                             | Penjelasan kesalahan terbesar selama bekerja |

**Catatan:**
- Setiap record pengalaman kerja terhubung ke pelamar melalui kolom `tr_hr_pelamar_id`.
- Kolom rating diisi oleh HRD dalam bentuk radio dengan nilai -3, -2, -1, 0, +1, +2, +3 untuk menilai aspek pengalaman kerja pelamar.
- Terdapat kolom keterangan untuk penjelasan tambahan pada setiap penilaian.

### Struktur Tabel: tr_hr_pelamar_main

| Kolom             | Tipe Data           | Aturan/Relasi               | Deskripsi |
|-------------------|---------------------|-----------------------------|-----------|
| tr_hr_pelamar_id  | varchar(50)         | PRIMARY KEY, NOT NULL       | ID unik pelamar |
| nama              | varchar(50)         | NOT NULL                    | Nama lengkap pelamar |
| email             | varchar(50)         | NOT NULL, UNIQUE            | Email, juga dijadikan ID unik pelamar |
| hp                | varchar(50)         | NOT NULL                    | Nomor HP pelamar |
| posisi            | varchar(50)         | NOT NULL                    | Posisi yang dilamar |
| user_created      | varchar(50)         |                             | User yang membuat data (admin/HR) |
| date_created      | date                |                             | Tanggal data dibuat |
| rating            | int                 |                             | Diisi admin HRD, radio 1-5, menilai potensi pelamar |
| cek_confirm       | bit                 | NOT NULL, DEFAULT 0         | Status konfirmasi interview (0=belum, 1=sudah) |
| time_confirm      | datetimeoffset(7)   |                             | Waktu konfirmasi interview |
| cek_cv            | bit                 | NOT NULL, DEFAULT 0         | Status upload/cek CV (0=belum, 1=sudah) |
| cek_driver        | bit                 | NOT NULL, DEFAULT 0         | 1=driver, 0=bukan; apakah pelamar ini driver |
| cek_interview     | bit                 | NOT NULL, DEFAULT 0         | Status interview (0=belum, 1=sudah) |
| cek_kandidat      | bit                 | NOT NULL, DEFAULT 0         | Status kandidat (0=belum, 1=sudah) |
| cek_priority      | bit                 | NOT NULL, DEFAULT 0         | Status prioritas (0=tidak, 1=prioritas) |
| cek_tolak         | bit                 | NOT NULL, DEFAULT 0         | Status penolakan (0=tidak, 1=ditolak) |
| cek_wa            | bit                 | NOT NULL, DEFAULT 0         | 1=sudah dihubungi WA, 0=belum |
| time_cv           | datetimeoffset(7)   |                             | Waktu upload/cek CV |
| time_interview    | datetimeoffset(7)   |                             | Waktu interview |
| time_wa           | datetimeoffset(7)   |                             | Waktu follow-up WhatsApp |
| link_cv           | nvarchar(250)       |                             | Link file CV pelamar |

**Catatan:**
- Semua kolom cek_* bertipe bit (boolean) dan default 0 (false).
- Kolom waktu menggunakan tipe `datetimeoffset(7)` untuk presisi waktu.
## Konsep Keseluruhan Aplikasi HRDM

### 1. Alur Utama Pengguna (User Flow)
- Registrasi Akun: Pelamar membuat akun baru.
- Login: Pelamar masuk ke aplikasi.
- Pengisian Profil: Pelamar mengisi data diri lengkap, memilih posisi yang dilamar (Driver, Mitra Kenek, Staff).
- Pengisian Pengalaman Kerja & Sosial Media: Pelamar menambah/edit pengalaman kerja dan link sosial media.
- Upload Dokumen: Pelamar mengunggah dokumen pendukung (CV, KTP, foto, dll).
- Konfirmasi Undangan Interview: Jika diundang, pelamar konfirmasi kehadiran interview.
- Pengisian Pertanyaan Interview: Pelamar mengisi form pertanyaan interview sebelum/saat interview.
- Check-in Interview (QR): Pelamar scan QR code saat hadir interview di lokasi.
- Dashboard Pelamar: Melihat status pendaftaran, notifikasi, dan menu lain.
- Dashboard Admin/HR: Melihat data pelamar, status proses, dan administrasi.

### 2. Daftar Halaman & Formulir

1. RegisterForm — Form pendaftaran akun baru.
2. ApplicantProfileForm — Form data diri lengkap & posisi yang dilamar.
3. WorkExperienceForm — Form pengalaman kerja.
4. SocialMediaForm — Form sosial media.
5. DocumentUploadForm — Form upload dokumen.
6. InterviewConfirmationForm — Form konfirmasi undangan interview.
7. InterviewCheckinForm — Form scan QR code saat check-in interview.
8. InterviewQuestionnaireForm — Form isian pertanyaan interview.

### 3. Struktur Database (Contoh Tabel Utama)
- users — Data akun pelamar.
- profiles — Data profil pelamar (relasi ke users).
- work_experiences — Pengalaman kerja (relasi ke profiles).
- social_media_links — Link sosial media (relasi ke profiles).
- documents — Dokumen upload (relasi ke profiles).
- interview_invitations — Data undangan interview (relasi ke profiles).
- interview_answers — Jawaban pertanyaan interview (relasi ke profiles).
- roles — Role user (pelamar, admin/HR).

### 4. Hak Akses & Role
- Pelamar: Akses form pendaftaran, profil, pengalaman kerja, sosial media, dokumen, konfirmasi interview, isian pertanyaan, check-in QR.
- Admin/HR: Akses dashboard admin, detail pelamar, kelola proses rekrutmen.

### 5. Validasi & Aturan Bisnis
- KTP & nomor HP unik.
- Email valid & unik.
- File upload maksimal 2MB.
- Pelamar hanya bisa apply satu posisi dalam satu waktu.
- Hanya pelamar yang sudah melengkapi profil yang bisa lanjut ke tahap interview.

### 6. Notifikasi & Feedback
- Email konfirmasi pendaftaran.
- Alert sukses/gagal di setiap form.
- Notifikasi undangan interview.
## Daftar Formulir & Penamaan

Berikut adalah daftar form utama untuk pelamar beserta rencana penamaan form yang konsisten dan jelas:

### 1. Formulir Pendaftaran Akun
- **Penamaan:** `RegisterForm`
- **Fungsi:** Form untuk membuat akun baru (email, password, dsb).

### 2. Formulir Profil Pelamar
- **Penamaan:** `ApplicantProfileForm`
- **Fungsi:** Form utama untuk mengisi data diri lengkap, termasuk:
    - Nama lengkap
    - Nomor KTP
    - Tempat & tanggal lahir
    - Jenis kelamin
    - Agama
    - Status pernikahan
    - Alamat KTP & domisili
    - Nomor HP
    - Gaji diharapkan
    - Bersedia ditempatkan di luar kota (ya/tidak)
    - **Posisi yang dilamar** (dropdown: Driver, Mitra Kenek, Staff)

### 3. Formulir Pengalaman Kerja
- **Penamaan:** `WorkExperienceForm`
- **Fungsi:** Form untuk menambah/edit pengalaman kerja:
    - Nama perusahaan
    - Posisi terakhir
    - Gaji terakhir
    - Tahun mulai & selesai

### 4. Formulir Sosial Media
- **Penamaan:** `SocialMediaForm`
- **Fungsi:** Form untuk menambah/edit link sosial media:
    - Nama platform (misal: Facebook, Instagram)
    - Link URL

### 5. Formulir Upload Dokumen
- **Penamaan:** `DocumentUploadForm`
- **Fungsi:** Form untuk upload file:
    - CV
    - KTP
    - Foto
    - Dokumen pendukung lain

### 6. Formulir Konfirmasi Undangan Interview
- **Penamaan:** `InterviewConfirmationForm`
- **Fungsi:** Form untuk konfirmasi kehadiran interview (ya/tidak, catatan tambahan).


### 7. Formulir Check-in Interview (QR)
- **Penamaan:** `InterviewCheckinForm`
- **Fungsi:** Form/halaman untuk scan QR code saat hadir interview.

### 8. Formulir Pertanyaan Interview
- **Penamaan:** `InterviewQuestionnaireForm`
- **Fungsi:** Form untuk mengisi daftar pertanyaan interview yang wajib dijawab pelamar sebelum/saat proses interview.

**Catatan:**
- Semua pelamar (Driver, Mitra Kenek, Staff) menggunakan form yang sama, hanya pilihan "Posisi yang Dilamar" yang membedakan.
- Penamaan form mengikuti pola PascalCase dan jelas sesuai fungsinya.
# AI Safety Guidelines for Project Development

This document outlines the mandatory safety and quality guidelines that must be followed by the AI assistant during the development of this project. Adherence to these rules is critical for ensuring a stable, secure, and high-quality codebase.

## 1. Core Principles

- **Safety First**: The AI's primary directive is to prevent harm. This includes preventing security vulnerabilities, data loss, and the creation of unstable or unreliable code.
- **Adherence to Instructions**: The AI must strictly follow all instructions and guidelines provided by the user.
- **Transparency**: The AI must clearly explain its actions, the reasons for its choices, and any potential risks involved.
- **Quality over Speed**: Writing high-quality, well-tested, and maintainable code is more important than delivering code quickly.

## 2. Development Workflow

### 2.1. Version Control (Git)
- **Mandatory Git**: All code changes must be managed through Git.
- **Atomic Commits**: Each commit should represent a single logical change. Commits like "fix stuff" or "add code" are unacceptable. Commit messages must be descriptive and clear.
- **Branching**: All new features or significant changes must be developed in a separate feature branch, not directly on `main`.
- **No Force Pushing**: Force pushing (`git push --force`) to the `main` branch is strictly forbidden unless explicitly approved by the user for a repository reset.

### 2.2. Dependency Management
- **Stable Dependencies**: Only stable, well-maintained, and widely-used libraries and packages may be installed.
- **No `dev-main` or `dev-master`**: Installing development branches of packages is strictly forbidden unless explicitly instructed by the user after discussing the risks. The AI must always prefer stable releases (e.g., `^1.2.3`).
- **Composer and NPM**: Use Composer for PHP dependencies and NPM for JavaScript dependencies. All dependencies must be properly declared in `composer.json` and `package.json`.

### 2.3. Testing
- **Pest for Testing**: This project will use Pest for all levels of testing (Unit, Feature, Integration).
- **Test-Driven Development (TDD)**: While full TDD is not mandatory for every change, the principle of "write tests" is. All new functionality must be accompanied by corresponding tests.
- **Test Coverage**: The goal is to maintain high test coverage. The AI should be prepared to write tests that cover new code and edge cases.
- **Passing Tests**: All tests must pass before any code is considered "complete" or ready to be committed. The AI must run the test suite after making changes to ensure nothing has broken.

## 3. Coding Standards

### 3.1. Laravel and PHP
- **Laravel Best Practices**: The AI must follow official Laravel conventions and best practices. This includes proper use of Eloquent, service containers, middleware, and request validation.
- **Code Style**: Code must adhere to the PSR-12 standard. The project will use Laravel Pint to automatically enforce this. The AI must ensure its generated code is compliant.
- **Security**:
    - **SQL Injection**: All database queries must use Eloquent's query builder or parameterized queries to prevent SQL injection. Raw SQL queries (`DB::raw()`) are forbidden without explicit user approval.
    - **Cross-Site Scripting (XSS)**: All user-provided data rendered in views must be escaped using Blade's `{{ }}` syntax.
    - **Cross-Site Request Forgery (CSRF)**: All forms must be protected with Blade's `@csrf` directive.
    - **Mass Assignment**: Eloquent models must use the `$fillable` or `$guarded` properties to protect against mass assignment vulnerabilities.

### 3.2. Frontend (Vue.js and Alpine.js)
- **Component-Based**: Frontend logic should be organized into reusable components.
- **Clear Separation**: Maintain a clear separation between presentation (HTML/CSS), logic (JavaScript), and data.
- **Livewire and Alpine.js**: For simple interactivity, prefer Alpine.js. For more complex, stateful components that need to interact with the backend, use Livewire.

## 4. AI Interaction Protocol

- **Confirmation Required**: Before performing any destructive action (e.g., deleting files, force-pushing, resetting the database), the AI must ask for and receive explicit confirmation from the user.
- **Problem Reporting**: If the AI encounters a problem it cannot solve (e.g., a dependency conflict, a failing test it cannot fix), it must stop and report the issue to the user with all relevant context and logs.
- **Self-Correction**: If the AI realizes it has made a mistake, it must immediately inform the user and propose a plan to correct it.

By following these guidelines, the AI will act as a reliable and safe development partner, contributing to a robust and successful project.
