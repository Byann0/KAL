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

kita akan mengidentifikasi sistem L dengan matriks augmentasinya A\text{.}.
Lebih lanjut, mereduksi sistem linear menggunakan operasi elementer pada persamaan sekarang diterjemahkan sebagai melakukan operasi baris elementer pada matriks. Dengan risiko redundansi, kita sekarang secara resmi menerjemahkan sejumlah konsep terdahulu kita mengenai reduksi sistem linear ke dalam konteks matriks.

Perkalian skalar : Kalikan sebuah baris dengan bilangan tak-nol c\ne 0\text{:}: yaitu, ganti r_i dengan c\,r_i\text{,}, hasil perkalian semua entri baris dengan c\text{.}.

Pertukaran baris : Tukar dua baris dari A\text{.}.

Penjumlahan baris : Tambahkan kelipatan satu baris ke baris lain: yaitu, ganti r_i dengan r_i+cr_j untuk suatu c\text{,}, i\text{,}, dan j\text{.}.

Tindakan mengubah matriks menggunakan operasi baris elementer disebut reduksi baris
Dua matriks ekuivalen baris jika yang satu dapat diperoleh dari yang lain dengan melakukan urutan hingga operasi baris elementer.

## Definisi Eliminasi Gaussian

Eliminasi Gaussian adalah algoritma yang dijelaskan di bawah. Algoritma ini menerima masukan matriks A dan mengembalikan matriks B yang ekuivalen baris dalam bentuk eselon baris.

- Langkah 1
Temukan kolom tak-nol paling kiri dan lakukan pertukaran baris untuk memindahkan baris dengan entri tak-nol ini ke bagian atas matriks.🔗
- Langkah 2
Skala baris teratas yang baru untuk menghasilkan satu utama pada baris tersebut. Sebut baris baru ini r\text{.}.
- Langkah 3
Untuk setiap baris r_i di bawah r\text{,}, lakukan operasi baris berbentuk r_i+c\,r untuk mengganti semua entri di bawah satu utama dari r dengan nol.
- Langkah 4
Mulai lagi dengan Langkah 1 yang diterapkan pada matriks yang terdiri dari semua baris di bawah r\text{.}. Lanjutkan hingga matriks berada dalam bentuk eselon baris.