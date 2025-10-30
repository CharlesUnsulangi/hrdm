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
