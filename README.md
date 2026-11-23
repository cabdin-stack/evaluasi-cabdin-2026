# Evaluasi Kinerja Pendidikan 2026 – Cabdin Wilayah Jember

Aplikasi web pengumpulan & dashboard rekapitulasi evaluasi kinerja pendidikan SMA, SMK, dan SLB Negeri/Swasta di bawah Cabang Dinas Pendidikan Wilayah Jember (Kab. Jember & Kab. Lumajang).

## Pemasangan (±5 menit)
1. Buat/buka Google Spreadsheet Anda → **Extensions → Apps Script**.
2. Hapus isi default, tempel seluruh isi `Code.gs`.
3. **Wajib:** Ganti `ADMIN_PASSWORD = 'ganti-password-admin'` di `Code.gs` dengan password admin yang kuat, lalu simpan.
4. **Deploy → New deployment → Web app**: Execute as **Me**, Who has access **Anyone** → Deploy → izinkan akses → salin **Web app URL**.
   *(Jika memperbarui `Code.gs` pada deployment lama: **Deploy → Manage deployments → Edit → New version → Deploy**.)*
5. Tempel Web app URL pada konstanta `SCRIPT_URL` di `index.html` dan `admin.html`.
6. Hosting `index.html` dan `admin.html` bersama-sama (Netlify Drop, GitHub Pages, atau Firebase Hosting) lalu bagikan link `index.html` ke sekolah.

## Sheet `Master_Sekolah` (Validasi Akses NPSN)
Buat sheet bernama **`Master_Sekolah`** di Spreadsheet dengan header baris pertama:
`NPSN` | `Nama` | `Jenjang` | `Status` | `Kabupaten` | `Kecamatan` *(opsional)*

- Selama sheet `Master_Sekolah` berisi data sekolah, **hanya NPSN yang terdaftar** yang dapat membuka formulir lanjutan, memuat data, dan mengirim isian (divalidasi di frontend maupun backend `Code.gs`).
- Identitas sekolah (`Nama`, `Jenjang`, `Status`, `Kabupaten`) otomatis terisi dan terkunci sesuai `Master_Sekolah` saat sekolah menekan **Verifikasi NPSN & Muat Data**.
- Di `admin.html`, `Master_Sekolah` juga digunakan untuk menampilkan daftar sekolah yang **Belum mengisi**.

## Sheet yang terbentuk otomatis
`01_Profil`, `02_Anggaran`, `02_Anggaran_Rinci`, `03_Sarpras_SDM`, `04_Mutu`, `05_Program`, `06_Indikator_Prestasi`, `06_Prestasi` (1 baris = 1 prestasi), `07_Kemitraan`, `08_Evaluasi`, `09_Proyeksi2027`, `10_Data2025`.
Setiap baris memuat waktu kirim, NPSN, nama sekolah, jenjang, status, kabupaten, kecamatan, pengisi, kontak, kepala sekolah, dan NIP.
