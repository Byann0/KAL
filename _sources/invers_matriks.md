---
title: Invers Matriks
date: 2026-06-15
---

# Invers Matriks

Invers matriks (kebalikan matriks) adalah salah satu konsep paling penting dalam aljabar linear. Secara sederhana, invers matriks berfungsi sebagai pengganti operasi **pembagian** dalam dunia matriks, karena operasi pembagian antar-matriks secara langsung tidak didefinisikan.

Untuk matriks persegi $A$, invers dari matriks tersebut dilambangkan dengan $A^{-1}$. Hubungan utama antara matriks dan inversnya adalah:

$$A \cdot A^{-1} = A^{-1} \cdot A = I$$

Di mana $I$ adalah **Matriks Identitas** (matriks persegi dengan nilai diagonal utama $1$ dan elemen lainnya $0$).

---

## Hubungan Erat Determinan dengan Invers Matriks

Determinan sebuah matriks bertindak sebagai indikator utama untuk menentukan apakah matriks tersebut dapat dibalik (memiliki invers) atau tidak:

> [!IMPORTANT]
> 1. **Matriks Non-Singular (Invertible):** Matriks memiliki invers jika dan hanya jika nilai determinannya tidak sama dengan nol ($\det(A) \neq 0$).
> 2. **Matriks Singular:** Jika nilai determinan sama dengan nol ($\det(A) = 0$), maka matriks tersebut **tidak memiliki invers**.

---

## 1. Panduan Lengkap Perhitungan Invers Matriks Ordo 2 × 2

Untuk matriks berukuran $2 \times 2$:

$$
A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}
$$

Invers matriks $A$ dihitung menggunakan rumus:

$$
A^{-1} = \frac{1}{\det(A)} \begin{bmatrix} d & -b \\ -c & a \end{bmatrix} = \frac{1}{ad - bc} \begin{bmatrix} d & -b \\ -c & a \end{bmatrix}
$$

### **Contoh Kasus Perhitungan Ordo 2 × 2 (Langkah demi Langkah)**

Misalkan diberikan matriks $A$:

$$
A = \begin{bmatrix} 3 & 5 \\ 1 & 2 \end{bmatrix}
$$

#### **Langkah 1: Menghitung Determinan ($\det A$)**
Kalikan elemen diagonal utama kemudian kurangi dengan hasil kali diagonal samping:
$$
\det(A) = ad - bc = (3 \times 2) - (5 \times 1) = 6 - 5 = 1
$$
Karena $\det(A) = 1 \neq 0$, maka matriks $A$ memiliki invers.

#### **Langkah 2: Membentuk Adjoin Matriks Ordo 2 × 2**
Tukar posisi elemen diagonal utama ($a$ ditukar dengan $d$) dan ubah tanda elemen diagonal samping ($b$ menjadi $-b$ dan $c$ menjadi $-c$):
$$
\operatorname{adj}(A) = \begin{bmatrix} d & -b \\ -c & a \end{bmatrix} = \begin{bmatrix} 2 & -5 \\ -1 & 3 \end{bmatrix}
$$

#### **Langkah 3: Mengalikan Skalar Determinan dengan Adjoin**
$$
A^{-1} = \frac{1}{\det(A)} \cdot \operatorname{adj}(A) = \frac{1}{1} \begin{bmatrix} 2 & -5 \\ -1 & 3 \end{bmatrix} = \begin{bmatrix} 2 & -5 \\ -1 & 3 \end{bmatrix}
$$

---

## 2. Panduan Lengkap Perhitungan Invers Matriks Ordo 3 × 3 (Metode Adjoin)

Untuk matriks berordo $3 \times 3$ ke atas, digunakan metode adjoin:

$$
A^{-1} = \frac{1}{\det(A)} \cdot \operatorname{adj}(A)
$$

### **Contoh Kasus Perhitungan Ordo 3 × 3 (Langkah demi Langkah)**

Misalkan diberikan matriks $B$:

$$
B = \begin{bmatrix} 1 & 0 & 2 \\ 2 & -1 & 3 \\ 4 & 1 & 8 \end{bmatrix}
$$

---

#### **Langkah 1: Menghitung Determinan ($\det B$)**
Determinan dihitung menggunakan ekspansi kofaktor sepanjang baris pertama:
$$
\begin{aligned}
\det(B) &= b_{11} C_{11} + b_{12} C_{12} + b_{13} C_{13} \\
        &= 1 \cdot \det\begin{bmatrix} -1 & 3 \\ 1 & 8 \end{bmatrix} - 0 \cdot \det\begin{bmatrix} 2 & 3 \\ 4 & 8 \end{bmatrix} + 2 \cdot \det\begin{bmatrix} 2 & -1 \\ 4 & 1 \end{bmatrix}
\end{aligned}
$$

Selesaikan masing-masing determinan submatriks $2 \times 2$:
* Submatriks 1: $(-1 \times 8) - (3 \times 1) = -8 - 3 = -11$
* Submatriks 2: $(2 \times 8) - (3 \times 4) = 16 - 12 = 4$
* Submatriks 3: $(2 \times 1) - (-1 \times 4) = 2 - (-4) = 6$

Substitusikan kembali ke persamaan awal:
$$
\det(B) = 1(-11) - 0(4) + 2(6) = -11 + 12 = 1
$$
Karena $\det(B) = 1 \neq 0$, matriks memiliki invers.

---

#### **Langkah 2: Menghitung Matriks Kofaktor $C$ (Sembilan Elemen)**
Nilai kofaktor dihitung menggunakan rumus $C_{ij} = (-1)^{i+j} \cdot M_{ij}$ dengan menghapus baris ke-$i$ dan kolom ke-$j$ secara bertahap:

##### **Baris Pertama ($i = 1$):**
* **Kofaktor $C_{11}$** (Hapus baris 1, kolom 1):
  $$C_{11} = (-1)^{1+1} \cdot \begin{vmatrix} -1 & 3 \\ 1 & 8 \end{vmatrix} = +1 \cdot ((-1 \cdot 8) - (3 \cdot 1)) = -8 - 3 = -11$$
* **Kofaktor $C_{12}$** (Hapus baris 1, kolom 2):
  $$C_{12} = (-1)^{1+2} \cdot \begin{vmatrix} 2 & 3 \\ 4 & 8 \end{vmatrix} = -1 \cdot ((2 \cdot 8) - (3 \cdot 4)) = -(16 - 12) = -4$$
* **Kofaktor $C_{13}$** (Hapus baris 1, kolom 3):
  $$C_{13} = (-1)^{1+3} \cdot \begin{vmatrix} 2 & -1 \\ 4 & 1 \end{vmatrix} = +1 \cdot ((2 \cdot 1) - (-1 \cdot 4)) = 2 + 4 = 6$$

##### **Baris Kedua ($i = 2$):**
* **Kofaktor $C_{21}$** (Hapus baris 2, kolom 1):
  $$C_{21} = (-1)^{2+1} \cdot \begin{vmatrix} 0 & 2 \\ 1 & 8 \end{vmatrix} = -1 \cdot ((0 \cdot 8) - (2 \cdot 1)) = -(0 - 2) = 2$$
* **Kofaktor $C_{22}$** (Hapus baris 2, kolom 2):
  $$C_{22} = (-1)^{2+2} \cdot \begin{vmatrix} 1 & 2 \\ 4 & 8 \end{vmatrix} = +1 \cdot ((1 \cdot 8) - (2 \cdot 4)) = 8 - 8 = 0$$
* **Kofaktor $C_{23}$** (Hapus baris 2, kolom 3):
  $$C_{23} = (-1)^{2+3} \cdot \begin{vmatrix} 1 & 0 \\ 4 & 1 \end{vmatrix} = -1 \cdot ((1 \cdot 1) - (0 \cdot 4)) = -(1 - 0) = -1$$

##### **Baris Ketiga ($i = 3$):**
* **Kofaktor $C_{31}$** (Hapus baris 3, kolom 1):
  $$C_{31} = (-1)^{3+1} \cdot \begin{vmatrix} 0 & 2 \\ -1 & 3 \end{vmatrix} = +1 \cdot ((0 \cdot 3) - (2 \cdot -1)) = 0 + 2 = 2$$
* **Kofaktor $C_{32}$** (Hapus baris 3, kolom 2):
  $$C_{32} = (-1)^{3+2} \cdot \begin{vmatrix} 1 & 2 \\ 2 & 3 \end{vmatrix} = -1 \cdot ((1 \cdot 3) - (2 \cdot 2)) = -(3 - 4) = 1$$
* **Kofaktor $C_{33}$** (Hapus baris 3, kolom 3):
  $$C_{33} = (-1)^{3+3} \cdot \begin{vmatrix} 1 & 0 \\ 2 & -1 \end{vmatrix} = +1 \cdot ((1 \cdot -1) - (0 \cdot 2)) = -1 - 0 = -1$$

Maka Matriks Kofaktor $C$ yang terbentuk adalah:
$$
C = \begin{bmatrix} -11 & -4 & 6 \\ 2 & 0 & -1 \\ 2 & 1 & -1 \end{bmatrix}
$$

---

#### **Langkah 3: Mentranspose Matriks Kofaktor untuk Memperoleh Adjoin ($\operatorname{adj} B$)**

Operasi transpose matriks dilakukan dengan cara menukar posisi baris menjadi kolom. Secara spesifik:
* Elemen-elemen **Baris 1** pada matriks kofaktor $C$ yaitu $[-11, -4, 6]$ diubah menjadi **Kolom 1** pada matriks adjoin.
* Elemen-elemen **Baris 2** pada matriks kofaktor $C$ yaitu $[2, 0, -1]$ diubah menjadi **Kolom 2** pada matriks adjoin.
* Elemen-elemen **Baris 3** pada matriks kofaktor $C$ yaitu $[2, 1, -1]$ diubah menjadi **Kolom 3** pada matriks adjoin.

Proses pemindahan ini dirumuskan sebagai:

$$
\operatorname{adj}(B) = C^T = \begin{bmatrix} -11 & 2 & 2 \\ -4 & 0 & 1 \\ 6 & -1 & -1 \end{bmatrix}
$$

---

#### **Langkah 4: Menghitung Invers Matriks ($B^{-1}$)**

Pada langkah ini, matriks adjoin yang diperoleh pada Langkah 3 dikalikan dengan invers nilai determinan ($\frac{1}{\det(B)}$). 

Karena nilai determinan $\det(B)$ adalah $1$, maka nilai pengali skalarnya adalah $\frac{1}{1} = 1$. Setiap elemen di dalam matriks adjoin dikalikan satu per satu dengan angka $1$:

$$
\begin{aligned}
B^{-1} &= \frac{1}{\det(B)} \cdot \operatorname{adj}(B) \\
       &= \frac{1}{1} \cdot \begin{bmatrix} -11 & 2 & 2 \\ -4 & 0 & 1 \\ 6 & -1 & -1 \end{bmatrix} \\
       &= \begin{bmatrix} 1 \cdot (-11) & 1 \cdot 2 & 1 \cdot 2 \\ 1 \cdot (-4) & 1 \cdot 0 & 1 \cdot 1 \\ 1 \cdot 6 & 1 \cdot (-1) & 1 \cdot (-1) \end{bmatrix} \\
       &= \begin{bmatrix} -11 & 2 & 2 \\ -4 & 0 & 1 \\ 6 & -1 & -1 \end{bmatrix}
\end{aligned}
$$

---

## 3. Verifikasi Keabsahan Hasil Invers

Untuk memastikan kebenaran hasil perhitungan invers matriks, dilakukan pembuktian dengan mengalikan matriks asal $B$ dengan matriks invers $B^{-1}$. Hasil perkalian dua matriks ini harus menghasilkan **Matriks Identitas ($I$)**:

$$
B \cdot B^{-1} = \begin{bmatrix} 1 & 0 & 2 \\ 2 & -1 & 3 \\ 4 & 1 & 8 \end{bmatrix} \begin{bmatrix} -11 & 2 & 2 \\ -4 & 0 & 1 \\ 6 & -1 & -1 \end{bmatrix}
$$

### **Proses Perkalian Matriks (Baris × Kolom)**

Perkalian matriks dilakukan dengan mengalikan elemen baris dari matriks pertama dengan elemen kolom dari matriks kedua secara berpasangan, lalu menjumlahkan hasilnya:

#### **1. Baris ke-1 dari Matriks B:** $[1, 0, 2]$
* **Kolom 1 ($B^{-1}_{*1}$):** $[-11, -4, 6]^T$
  $$\text{Elemen } c_{11} = (1 \cdot -11) + (0 \cdot -4) + (2 \cdot 6) = -11 + 0 + 12 = \mathbf{1}$$
* **Kolom 2 ($B^{-1}_{*2}$):** $[2, 0, -1]^T$
  $$\text{Elemen } c_{12} = (1 \cdot 2) + (0 \cdot 0) + (2 \cdot -1) = 2 + 0 - 2 = \mathbf{0}$$
* **Kolom 3 ($B^{-1}_{*3}$):** $[2, 1, -1]^T$
  $$\text{Elemen } c_{13} = (1 \cdot 2) + (0 \cdot 1) + (2 \cdot -1) = 2 + 0 - 2 = \mathbf{0}$$

#### **2. Baris ke-2 dari Matriks B:** $[2, -1, 3]$
* **Kolom 1 ($B^{-1}_{*1}$):** $[-11, -4, 6]^T$
  $$\text{Elemen } c_{21} = (2 \cdot -11) + (-1 \cdot -4) + (3 \cdot 6) = -22 + 4 + 18 = \mathbf{0}$$
* **Kolom 2 ($B^{-1}_{*2}$):** $[2, 0, -1]^T$
  $$\text{Elemen } c_{22} = (2 \cdot 2) + (-1 \cdot 0) + (3 \cdot -1) = 4 + 0 - 3 = \mathbf{1}$$
* **Kolom 3 ($B^{-1}_{*3}$):** $[2, 1, -1]^T$
  $$\text{Elemen } c_{23} = (2 \cdot 2) + (-1 \cdot 1) + (3 \cdot -1) = 4 - 1 - 3 = \mathbf{0}$$

#### **3. Baris ke-3 dari Matriks B:** $[4, 1, 8]$
* **Kolom 1 ($B^{-1}_{*1}$):** $[-11, -4, 6]^T$
  $$\text{Elemen } c_{31} = (4 \cdot -11) + (1 \cdot -4) + (8 \cdot 6) = -44 - 4 + 48 = \mathbf{0}$$
* **Kolom 2 ($B^{-1}_{*2}$):** $[2, 0, -1]^T$
  $$\text{Elemen } c_{32} = (4 \cdot 2) + (1 \cdot 0) + (8 \cdot -1) = 8 + 0 - 8 = \mathbf{0}$$
* **Kolom 3 ($B^{-1}_{*3}$):** $[2, 1, -1]^T$
  $$\text{Elemen } c_{33} = (4 \cdot 2) + (1 \cdot 1) + (8 \cdot -1) = 8 + 1 - 8 = \mathbf{1}$$

---

### **Hasil Akhir Perkalian:**

$$
B \cdot B^{-1} = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix} = I \quad (\mathbf{\text{Terbukti Valid}})
$$
