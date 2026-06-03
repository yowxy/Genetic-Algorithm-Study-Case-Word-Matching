# Algoritma Genetika: Studi Kasus Pencocokan Kata

## Deskripsi

Proyek ini mengimplementasikan Algoritma Genetika untuk menyelesaikan masalah pencocokan kata (word matching). Program akan mencoba menemukan sebuah kata target secara otomatis melalui proses evolusi yang terinspirasi dari seleksi alam.

Kata target yang digunakan sebagai studi kasus adalah **"GENETIKA"**.

---

## Apa itu Algoritma Genetika?

Algoritma Genetika adalah metode pencarian solusi yang meniru cara kerja evolusi makhluk hidup. Cara kerjanya sederhana:

1. Buat sekumpulan solusi acak (populasi awal)
2. Ukur seberapa baik setiap solusi (fitness)
3. Pilih solusi terbaik sebagai induk (seleksi)
4. Gabungkan dua induk untuk menghasilkan solusi baru (crossover)
5. Ubah sedikit nilai secara acak untuk variasi (mutasi)
6. Ulangi proses hingga solusi terbaik ditemukan

---

## Cara Kerja Program

### 1. Inisialisasi

Program mengubah setiap huruf target menjadi angka (A=1, B=2, ..., Z=26), kemudian membuat populasi awal berisi 100 individu secara acak.

### 2. Fungsi Fitness

Fitness mengukur seberapa dekat sebuah individu dengan kata target. Semakin tinggi nilai fitness, semakin mirip individu tersebut dengan kata target.

```
Fitness = Fitness Maksimal - Total Selisih Nilai Huruf
```

Fitness maksimal = 208 (26 x 8 huruf).

### 3. Seleksi (Roulette Wheel)

Individu dengan fitness lebih tinggi memiliki peluang lebih besar untuk dipilih sebagai induk. Prinsipnya seperti roda roulette, di mana individu terbaik mendapat bagian yang lebih besar.

### 4. Crossover (Dua Titik)

Dua induk saling bertukar segmen gen di antara dua titik potong yang dipilih secara acak. Hasilnya adalah dua individu baru (anak) yang mewarisi sifat dari kedua induk.

```
Induk 1: N F B D | W O | Q H
Induk 2: L V G M | K F | D P
Anak 1 : N F B M | K F | Q H
Anak 2 : L V G D | W O | D P
```

### 5. Mutasi

Setiap individu memiliki peluang kecil (1%) untuk mengalami perubahan acak pada salah satu gen-nya. Mutasi berfungsi menjaga keberagaman populasi agar tidak terjebak pada solusi yang kurang optimal.

### 6. Elitisme

Setelah satu generasi selesai, program menggabungkan populasi lama dan populasi baru, lalu hanya menyimpan 100 individu terbaik untuk generasi berikutnya. Hal ini memastikan kualitas solusi tidak menurun antar generasi.

---

## Parameter Algoritma

| Parameter | Nilai |
|---|---|
| Jumlah Populasi | 100 individu |
| Jumlah Generasi | 10 |
| Probabilitas Crossover | 0.7 (70%) |
| Probabilitas Mutasi | 0.01 (1%) |
| Panjang Gen | 8 (sesuai panjang kata target) |
| Rentang Nilai Alel | 1 sampai 26 |
| Fitness Maksimal | 208 |

---

## Struktur Proyek

```
Word-Matching/
├── index.ipynb   # Notebook utama berisi seluruh implementasi
└── README.md     # Dokumentasi proyek ini
```

---

## Persyaratan Sistem

Sebelum menjalankan proyek ini, pastikan perangkat sudah terinstal:

- Python versi 3.10 ke atas
- Jupyter Notebook atau JupyterLab
- Library Python: `numpy`, `matplotlib`

---

## Cara Instalasi dan Menjalankan

### Langkah 1: Pastikan Python sudah terinstal

Buka terminal atau command prompt, lalu ketik:

```bash
python --version
```

Jika muncul versi Python, berarti sudah terinstal. Jika belum, unduh Python di [https://www.python.org/downloads](https://www.python.org/downloads).

### Langkah 2: Install library yang dibutuhkan

Jalankan perintah berikut di terminal:

```bash
pip install numpy matplotlib jupyter
```

### Langkah 3: Buka notebook

Masuk ke folder proyek, lalu jalankan:

```bash
jupyter notebook index.ipynb
```

Atau buka file `index.ipynb` langsung melalui VS Code jika sudah terinstal ekstensi Jupyter.

### Langkah 4: Jalankan seluruh cell

Di dalam Jupyter Notebook, klik menu **Kernel > Restart & Run All** untuk menjalankan semua kode dari awal secara berurutan.

---

## Contoh Output

```
Menjalankan Algoritma Genetika untuk Word Matching:
target: GENETIKA -> [6, 4, 13, 4, 19, 8, 10, 0]
Generasi 1: Best Individu: [6, 5, 19, 4, 14, 12, 25, 3] -> "FESDNLYC" dengan Fitness: 174
Generasi 2: Best Individu: [5, 4, 9, 7, 22, 7, 7, 4]   -> "EDIGVGGD" dengan Fitness: 189
Generasi 3: Best Individu: [5, 4, 9, 7, 22, 7, 9, 4]   -> "EDIGVGID" dengan Fitness: 191
...
Generasi 10: Best Individu: [7, 4, 18, 4, 19, 7, 8, 2] -> "GDRDSGHB" dengan Fitness: 197
```

Nilai fitness terus meningkat setiap generasi, yang menandakan populasi semakin mendekati kata target.

---

## Catatan

- Karena algoritma ini menggunakan nilai acak, hasil setiap kali dijalankan bisa berbeda.
- Untuk mendapatkan hasil yang lebih optimal, jumlah generasi dapat ditingkatkan di bagian parameter.
- Kata target dapat diubah dengan mengganti nilai variabel `Target_word` pada cell pertama.

---

## Teknologi yang Digunakan

- **Python 3** - Bahasa pemrograman utama
- **NumPy** - Operasi array dan pengurutan data
- **Matplotlib** - Visualisasi grafik (siap digunakan)
- **Jupyter Notebook** - Lingkungan eksekusi interaktif
