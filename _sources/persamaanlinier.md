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

# Sistem Persamaan Linear

Menghitung dan mempelajari solusi persamaan, serta sistem persamaan, tanpa diragukan lagi memainkan peran penting dalam matematika; meskipun kami segera menambahkan bahwa ini bukan satu-satunya hal yang dilakukan para matematikawan.

## Definisi Persamaan Linear

Sebuah ekspresi linear dalam n peubah tak diketahui (atau variabel) x_1,x_2,\dots,x_n adalah ekspresi berbentuk

\begin{equation*}
a_1x_1 + a_2x_2 + \cdots + a_nx_n,
\end{equation*}

Sebuah persamaan linear dalam peubah x_1,x_2,\dots,x_n adalah persamaan yang dapat disederhanakan—hanya menggunakan penjumlahan dan pengurangan—menjadi bentuk

\begin{equation}
a_1x_1 + a_2x_2 + \cdots + a_nx_n = b,\tag{1.2.1}
\end{equation}

yang kita sebut sebagai bentuk baku. Suatu persamaan dalam peubah x_1,x_2,\dots,x_n disebut nonlinear jika tidak dapat disederhanakan ke bentuk gambar diatas hanya dengan penjumlahan dan pengurangan.

Diberikan suatu persamaan linear dalam bentuk baku (1.2.1), persamaan tersebut disebut homogen jika b = 0\text{,}, dan nonhomogen jika b \ne 0\text{.}.

## Contoh Persamaan Linear dan Nonlinear

1. Tinjau \sqrt{3}x + \sin(5) = 2z - e^4y\text{.}. Ini adalah persamaan linear dalam peubah x, y, z\text{.}. Bentuk bakunya adalah \sqrt{3}x + e^4y - 2z = -\sin(5)\text{.}. Karena ruas kanannya tak nol, persamaan ini bersifat nonhomogen.
2. Persamaan x^2 + y^2 = 1 adalah persamaan nonlinear dalam peubah x
 dan y\text{.}.

## Definisi Sistem Persamaan Linear

Sebuah sistem persamaan linear (atau sistem linear) adalah himpunan persamaan linear. Sebuah sistem linear disebut homogen jika seluruh persamaannya homogen.
Saat menampilkan sistem yang terdiri atas m persamaan dalam n peubah x_1,x_2,\dots,x_n\text{,}, biasanya kita menuliskan setiap persamaan dalam bentuk baku dan menyelaraskan suku-suku yang bersesuaian ke dalam kolom:

\begin{equation*}
\eqsys
\end{equation*}

Sistem homogen biasanya ditulis sebagai:

\begin{equation*}
\homsys.
\end{equation*}

## Definisi Solusi Sistem Linear

Sebuah solusi persamaan linear 
\begin{equation*}
a_1x_1 + a_2x_2 + \cdots + a_nx_n = b
\end{equation*}
adalah sebuah n-tuple (s_1,s_2,\dots,s_n) bilangan real sedemikian sehingga substitusi x_1 = s_1, x_2 = s_2, \dots, x_n = s_n menjadikan persamaan tersebut benar. Dalam hal ini, kita katakan bahwa (s_1,\dots,s_n) memecahkan persamaan tersebut.
Sebuah solusi sistem persamaan linear

\begin{equation*}
\eqsys
\end{equation*}

adalah sebuah n-tuple (s_1,s_2,\dots,s_n) yang merupakan solusi dari masing-masing m persamaan dalam sistem tersebut. Kita katakan bahwa (s_1,s_2,\dots,s_n) memecahkan sistem tersebut.

Diberikan suatu sistem linear, kita berupaya mencari himpunan seluruh solusinya. Seperti yang akan segera kita lihat, himpunan solusi ini memiliki salah satu dari tiga bentuk kualitatif berikut:

1. Himpunan solusi kosong; artinya, tidak ada solusi. Dalam hal ini, sistem disebut tidak konsisten. Jika tidak demikian, sistem disebut konsisten.
2. Himpunan solusi berisi tepat satu elemen; artinya, hanya ada satu solusi.
3. Himpunan solusi berisi tak hingga banyak elemen; artinya, terdapat tak hingga solusi.

# Representasi Matriks dari Sistem Linear

## Definisi Representasi Matriks dari Sistem Linear.  
Jika A adalah matriks koefisien dari suatu sistem persamaan linear dan \vect{b} adalah vektor konstanta, maka kita akan menuliskan \linearsystem{A}{\vect{b}} sebagai ungkapan singkat untuk sistem persamaan linear tersebut, yang akan kita sebut sebagai representasi matriks dari sistem linear.

Contoh Notasi untuk sistem persamaan linear:

\begin{align*}
2x_1+4x_2-3x_3+5x_4+x_5&=9\\
3x_1+x_2+\quad\quad x_4-3x_5&=0\\
-2x_1+7x_2-5x_3+2x_4+2x_5&=-3
\end{align*}

memiliki matriks koefisien

\begin{equation*}
A=
\begin{bmatrix}
2 & 4 & -3 & 5 & 1\\
3 & 1 & 0 & 1 & -3\\
-2 & 7 & -5 & 2 & 2
\end{bmatrix}
\end{equation*}

dan vektor konstanta

\begin{equation*}
\vect{b}=\colvector{9\\0\\-3}
\end{equation*}

dan sehingga akan direferensikan sebagai \linearsystem{A}{\vect{b}}\text{.}.

## Definisi Matriks Augmentasi

Misalkan kita memiliki sistem dengan m persamaan dalam n variabel, dengan matriks koefisien A dan vektor konstanta \vect{b}\text{.}.
Maka matriks augmentasi dari sistem persamaan tersebut adalah matriks berukuran m\times(n+1) yang n kolom pertamanya adalah kolom-kolom dari A
dan kolom terakhirnya (kolom ke-n+1) adalah vektor kolom \vect{b}\text{.}.
Ketika dideskripsikan secara simbolik, matriks ini akan dituliskan sebagai \augmented{A}{\mathbf{b}}\text{.}.

Matriks augmentasi merepresentasikan semua informasi penting dalam sistem persamaan, karena nama-nama variabel telah diabaikan, dan satu-satunya koneksi dengan variabel adalah lokasi koefisien mereka dalam matriks. Perlu diperhatikan bahwa matriks augmentasi hanyalah sebuah matriks, dan bukan sistem persamaan. Namun, matriks augmentasi selalu terkait dengan suatu sistem persamaan, dan sebaliknya. Perhatikan bahwa kita menggunakan ungkapan simbolik, \augmented{A}{\mathbf{b}}\text{,}, dengan garis vertikal dan kita akan melakukan hal yang sama dalam contoh konkret kita tetapi belum melakukannya karena pertimbangan teknis. Berikut adalah contoh singkat.

## Contoh Matriks augmentasi

Berikut adalah sistem berikut dengan 3 persamaan dalam 3 variabel.

\begin{align*}
x_1 -x_2 +2x_3 & =1\\
2x_1+ x_2 + x_3 & =8\\
x_1 + x_2 & =5
\end{align*}

Berikut adalah matriks augmentasinya.

\begin{align*}
\begin{bmatrix}
1 & -1 & 2 & 1\\
2 & 1 & 1 & 8\\
1 & 1 & 0 & 5
\end{bmatrix}
\end{align*}
