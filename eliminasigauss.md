---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Eliminasi Gauss

Kita akan mengidentifikasi sistem $L$ dengan matriks augmentasinya $A$.

Lebih lanjut, mereduksi sistem linear menggunakan operasi elementer pada persamaan diterjemahkan sebagai melakukan operasi baris elementer pada matriks.

Tindakan mengubah matriks menggunakan operasi baris elementer disebut **reduksi baris**.

Dua matriks disebut **ekuivalen baris** jika yang satu dapat diperoleh dari yang lain melalui urutan hingga operasi baris elementer.

---

## Operasi Baris Elementer

1. **Perkalian Skalar**

   Kalikan sebuah baris dengan bilangan tak-nol $c \ne 0$.

   $$
   r_i \rightarrow c\, r_i
   $$

2. **Pertukaran Baris**

   Tukar dua baris dari matriks:

   $$
   r_i \leftrightarrow r_j
   $$

3. **Penjumlahan Baris**

   Tambahkan kelipatan suatu baris ke baris lain:

   $$
   r_i \rightarrow r_i + c\, r_j
   $$

---

## Definisi Eliminasi Gaussian

Eliminasi Gaussian adalah algoritma yang menerima masukan matriks $A$ dan menghasilkan matriks $B$ yang ekuivalen baris dalam **bentuk eselon baris**.

### Langkah-langkah:

**Langkah 1**  
Temukan kolom tak-nol paling kiri.  
Lakukan pertukaran baris jika perlu untuk memindahkan entri tak-nol ke posisi paling atas.

**Langkah 2**  
Skalakan baris teratas tersebut sehingga entri utamanya menjadi 1 (disebut *satu utama* atau pivot).

**Langkah 3**  
Untuk setiap baris $r_i$ di bawah baris pivot $r$, lakukan operasi:

$$
r_i \rightarrow r_i + c\, r
$$

untuk mengubah semua entri di bawah pivot menjadi nol.

**Langkah 4**  
Ulangi proses pada submatriks yang tersisa (baris-baris di bawah pivot sebelumnya) hingga seluruh matriks berada dalam bentuk eselon baris.