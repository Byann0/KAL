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

# Aritmetika Matriks

Tidak setiap matriks harus dianggap sebagai matriks augmented yang terkait dengan sistem linear.

## Definisi Matriks

Sebuah matriks (real) adalah array persegi panjang dari bilangan real
$$
A = \begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{bmatrix}
$$

Bilangan $a_{ij}$ yang terletak pada baris ke-$i$ dan kolom ke-$j$ dari $A$ disebut $(i, j)$-entri (atau $ij$-entri) dari $A$.Sebuah matriks dengan $m$ baris dan $n$ kolom dikatakan memiliki ukuran (atau dimensi) $m \times n$.Matriks biasanya menggunakan huruf kapital awal alfabet (e.g. $A, B, C, D$, etc.) untuk menunjukkan matriks.

## Notasi Matriks
Notasi pembangun matriks

Notasi $[a_{ij}]_{m \times n}$ menunjukkan matriks $m \times n$ yang entri $ij$-nya (baris ke-$i$, kolom ke-$j$) adalah $a_{ij}$. Ketika tidak ada bahaya kebingungan, notasi ini sering disingkat menjadi $[a_{ij}]$.

Notasi entri matriks

Diberikan sebuah matriks $A$, notasi $[A]_{ij}$ menunjukkan entri ke-$ij$ dari $A$. Jadi jika $A = [a_{ij}]_{m \times n}$, maka $[A]_{ij} = a_{ij}$ untuk semua $1 \le i \le m$ dan $1 \le j \le n$.

---

## Contoh Notasi

Notasi dapat digunakan untuk mendeskripsikan matriks yang entri $ij$-nya diberikan oleh aturan atau formula tertentu.Sebagai contoh, misalkan $A = [a_{ij}]_{2 \times 3}$, dimana $a_{ij} = (i - j)j$. Ini adalah matriks $2 \times 3$ yang entri $ij$-nya adalah $(i - j)j$. Jadi

$$
A = \begin{bmatrix} (1 - 1)1 & (1 - 2)2 & (1 - 3)3 \\ (2 - 1)1 & (2 - 2)2 & (2 - 3)3 \end{bmatrix} = \begin{bmatrix} 0 & -2 & -6 \\ 1 & 0 & -3 \end{bmatrix}
$$

Dalam contoh ini kita memiliki $[A]_{23} = -3$ dan $[A]_{ii} = 0$ untuk $i = 1, 2$.

---

## Definisi Kesamaan Matriks

Misalkan $A$ dan $B$ adalah matriks dengan dimensi $m \times n$ dan $m' \times n'$, masing-masing. Dua matriks tersebut sama jika:

1. $m = m'$ dan $n = n'$;
2. $[A]_{ij} = [B]_{ij}$ untuk semua $1 \le i \le m$ dan $1 \le j \le n$.

Dengan kata lain, kita memiliki $A = B$ jika dan hanya jika $A$ dan $B$ memiliki bentuk yang sama, dan setiap entri dari $A$ sama dengan entri yang bersesuaian dari $B$.

## Contoh Kesamaan Matriks

$$
A = \begin{bmatrix} 1 & 2 & 3 & 4 \end{bmatrix} \quad
B = \begin{bmatrix} 1 \\ 2 \\ 3 \\ 4 \end{bmatrix}
$$

tidak sama satu sama lain, meskipun mereka memiliki entri yang sama yang muncul kira-kira dalam urutan yang sama. Dalam kasus ini kesamaan tidak berlaku karena $A$ dan $B$ memiliki bentuk yang berbeda: $A$ adalah $1 \times 4$, dan $B$ adalah $4 \times 1$.

Matriks $A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$ dan $B = \begin{bmatrix} 1 & 2 \\ 5 & 4 \end{bmatrix}$ memiliki dimensi yang sama, tetapi tidak sama karena $[A]_{21} = 3 \neq 5 = [B]_{21}$.

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
