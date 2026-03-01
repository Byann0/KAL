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

Sebuah ekspresi linear dalam n peubah tak diketahui (atau variabel) 
$x_1, x_2, \dots, x_n$ adalah ekspresi berbentuk

$$
a_1x_1 + a_2x_2 + \cdots + a_nx_n
$$

Sebuah persamaan linear dalam peubah 
$x_1, x_2, \dots, x_n$ adalah persamaan yang dapat disederhanakan—hanya menggunakan penjumlahan dan pengurangan—menjadi bentuk

$$
a_1x_1 + a_2x_2 + \cdots + a_nx_n = b
$$

yang kita sebut sebagai bentuk baku.

Suatu persamaan disebut nonlinear jika tidak dapat disederhanakan ke bentuk di atas hanya dengan penjumlahan dan pengurangan.

Persamaan disebut homogen jika $b = 0$, dan nonhomogen jika $b \ne 0$.

---

## Contoh Persamaan Linear dan Nonlinear

1. Tinjau

$$
\sqrt{3}x + \sin(5) = 2z - e^4 y
$$

Ini adalah persamaan linear dalam peubah $x, y, z$.  
Bentuk bakunya:

$$
\sqrt{3}x + e^4 y - 2z = -\sin(5)
$$

Karena ruas kanannya tidak nol, persamaan ini bersifat nonhomogen.

2. Persamaan

$$
x^2 + y^2 = 1
$$

adalah persamaan nonlinear dalam peubah $x$ dan $y$.

---

## Definisi Sistem Persamaan Linear

Sebuah sistem persamaan linear adalah himpunan persamaan linear.

Sistem disebut homogen jika seluruh persamaannya homogen.

Contoh sistem dengan $m$ persamaan dan $n$ variabel:

$$
\begin{aligned}
a_{11}x_1 + a_{12}x_2 + \dots + a_{1n}x_n &= b_1 \\
a_{21}x_1 + a_{22}x_2 + \dots + a_{2n}x_n &= b_2 \\
\vdots \\
a_{m1}x_1 + a_{m2}x_2 + \dots + a_{mn}x_n &= b_m
\end{aligned}
$$

---

## Definisi Solusi Sistem Linear

Sebuah solusi persamaan linear

$$
a_1x_1 + a_2x_2 + \cdots + a_nx_n = b
$$

adalah sebuah $n$-tuple $(s_1, s_2, \dots, s_n)$ sehingga substitusi  
$x_1 = s_1, x_2 = s_2, \dots, x_n = s_n$ membuat persamaan benar.

Sebuah solusi sistem persamaan linear adalah $n$-tuple  
$(s_1, s_2, \dots, s_n)$ yang merupakan solusi dari setiap persamaan dalam sistem.

Himpunan solusi dapat berupa:

1. Tidak ada solusi (sistem tidak konsisten)
2. Tepat satu solusi
3. Tak hingga banyak solusi

---

# Representasi Matriks dari Sistem Linear

Jika $A$ adalah matriks koefisien dan $\mathbf{b}$ adalah vektor konstanta,  
maka sistem dapat ditulis sebagai

$$
A\mathbf{x} = \mathbf{b}
$$

---

## Contoh

$$
\begin{aligned}
2x_1 + 4x_2 - 3x_3 + 5x_4 + x_5 &= 9 \\
3x_1 + x_2 + x_4 - 3x_5 &= 0 \\
-2x_1 + 7x_2 - 5x_3 + 2x_4 + 2x_5 &= -3
\end{aligned}
$$

Matriks koefisiennya:

$$
A =
\begin{bmatrix}
2 & 4 & -3 & 5 & 1 \\
3 & 1 & 0 & 1 & -3 \\
-2 & 7 & -5 & 2 & 2
\end{bmatrix}
$$

Vektor konstanta:

$$
\mathbf{b} =
\begin{bmatrix}
9 \\
0 \\
-3
\end{bmatrix}
$$

---

## Definisi Matriks Augmentasi

Matriks augmentasi dari sistem adalah:

$$
\left[
\begin{array}{ccc|c}
1 & -1 & 2 & 1 \\
2 & 1 & 1 & 8 \\
1 & 1 & 0 & 5
\end{array}
\right]
$$

Matriks ini merepresentasikan seluruh informasi penting dari sistem persamaan.
