# Generator Screenshot Formulir

Aplikasi web ini memungkinkan pengguna untuk secara cepat menghasilkan gambar screenshot formulir web yang terlihat realistis dan profesional hanya dengan mendeskripsikan elemen-elemennya.

## Proses Bisnis & Tujuan

Dalam pengembangan produk digital, seringkali dibutuhkan visualisasi cepat dari sebuah antarmuka pengguna (UI), seperti formulir pendaftaran, login, atau kontak. Proses pembuatan mockup ini secara manual menggunakan perangkat lunak desain bisa memakan waktu dan memerlukan keahlian desain.

**Generator Screenshot Formulir** hadir untuk mengatasi masalah ini dengan menyediakan solusi instan bagi:

*   **UI/UX Designer & Product Manager:** Untuk membuat mockup awal (lo-fi/hi-fi) dengan cepat guna presentasi ide, pengujian konsep, atau diskusi internal tanpa harus membuka aplikasi desain.
*   **Developer:** Untuk menghasilkan gambar placeholder yang representatif saat membangun frontend, sebelum desain final tersedia.
*   **Content Creator & Technical Writer:** Untuk membuat ilustrasi visual untuk dokumentasi, artikel blog, atau materi tutorial dengan mudah.
*   **Marketer:** Untuk membuat visual pendukung materi promosi atau kampanye.

Aplikasi ini menghemat waktu, mempercepat alur kerja, dan memungkinkan siapa saja untuk menghasilkan aset visual berkualitas tinggi tanpa keahlian desain grafis.

## Alur Proses & Teknologi

Aplikasi ini dibangun menggunakan arsitektur frontend modern yang berinteraksi langsung dengan AI generatif untuk pembuatan gambar.

**Teknologi Utama:**

*   **Frontend:** React, TypeScript, Tailwind CSS
*   **AI Image Generation:** Google Gemini API (Model `imagen-4.0-generate-001`)

**Alur Kerja Aplikasi:**

1.  **Input Pengguna:** Pengguna membuka aplikasi dan disambut dengan antarmuka sederhana di panel sebelah kiri. Di sini, pengguna dapat memasukkan:
    *   **Judul Formulir:** Teks utama yang akan menjadi judul dari formulir.
    *   **Label Kolom:** Nama-nama untuk setiap kolom input (misalnya, "Nama Pengguna", "Email"). Pengguna dapat menambah atau mengurangi jumlah kolom sesuai kebutuhan.
    *   **Teks Tombol:** Teks untuk tombol aksi utama (misalnya, "Kirim", "Daftar").

2.  **Pembuatan Prompt:** Ketika pengguna menekan tombol **"Buat Screenshot"**, aplikasi secara dinamis menyusun sebuah *prompt* (perintah teks) yang sangat deskriptif. Prompt ini tidak hanya berisi teks yang dimasukkan pengguna, tetapi juga instruksi gaya, seperti:
    *   Meminta gambar screenshot UI resolusi tinggi.
    *   Menjelaskan estetika desain (modern, minimalis, bersih).
    *   Menentukan palet warna profesional (nuansa biru, abu-abu, putih).
    *   Memastikan output terlihat seperti screenshot dari situs web nyata.

3.  **Komunikasi dengan Gemini API:**
    *   Prompt yang telah dibuat dikirimkan ke model `imagen-4.0-generate-001` melalui Google Gemini API.
    *   Aplikasi menampilkan status *loading* untuk memberitahu pengguna bahwa proses pembuatan gambar sedang berlangsung.

4.  **Penerimaan & Tampilan Gambar:**
    *   Gemini API memproses prompt dan menghasilkan gambar berformat PNG berdasarkan deskripsi tersebut.
    *   Gambar dikirim kembali ke aplikasi dalam format Base64.
    *   Aplikasi kemudian menampilkan gambar yang dihasilkan di panel utama di sebelah kanan. Pengguna dapat melihat hasilnya dan menyimpannya dengan klik kanan.

5.  **Penanganan Error:** Jika terjadi kegagalan saat komunikasi dengan API, aplikasi akan menampilkan pesan kesalahan yang informatif kepada pengguna.

## Struktur Proyek

```
/
├── components/
│   └── icons.tsx         # Komponen ikon SVG (Loading, Plus, Trash)
├── services/
│   └── geminiService.ts  # Logika untuk berinteraksi dengan Gemini API
├── App.tsx               # Komponen utama aplikasi, berisi UI dan state management
├── index.html            # File HTML utama
├── index.tsx             # Titik masuk aplikasi React
├── metadata.json         # Metadata aplikasi
└── README.md             # Dokumentasi ini
```

## Prasyarat

Untuk menjalankan dan mengembangkan aplikasi ini, dibutuhkan sebuah kunci API (API Key) dari Google AI Studio yang memiliki akses ke model `imagen-4.0-generate-001`. Kunci API ini harus dikonfigurasi sebagai variabel lingkungan (`process.env.API_KEY`).
