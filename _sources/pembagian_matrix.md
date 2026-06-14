---
title: Pembagian Matrix
date: 2026-06-12
---

## Pembagian Matriks

Di dalam aljabar linear, secara harfiah **tidak ada operasi pembagian matriks secara langsung** (kita tidak bisa melakukan operasi seperti $A \div B$ atau $\frac{A}{B}$). 

### **Analogi Sederhana: Kenapa Matriks Tidak Bisa Dibagi Biasa?**
Bayangkan sebuah bilangan biasa: $10 \div 2 = 5$. Ini sangat mudah karena kita hanya membagi satu nilai tunggal dengan nilai tunggal lainnya. 

Namun, matriks adalah **kumpulan angka berbentuk tabel**. Tidak ada aturan matematika untuk membagi sebuah tabel angka secara langsung dengan tabel angka lainnya. 

Sebagai solusinya, kita menggunakan konsep **perkalian dengan invers (kebalikan) matriks**.
* Pada bilangan biasa: $10 \div 2$ sama dengan $10 \times 2^{-1}$ (atau $10 \times \frac{1}{2}$).
* Pada matriks: $A \div B$ diselesaikan dengan mengalikan matriks $A$ dengan invers matriks $B$ (yaitu $B^{-1}$).

---

### **1. Apa itu Invers Matriks?**
Invers matriks (dilambangkan dengan $A^{-1}$) adalah kebalikan dari matriks $A$. Jika matriks $A$ dikalikan dengan inversnya, hasilnya adalah **Matriks Identitas ($I$)** (matriks yang diagonal utamanya bernilai $1$ dan elemen lainnya $0$, setara dengan angka $1$ pada bilangan biasa).

$$A \times A^{-1} = I$$

#### **Syarat Matriks Memiliki Invers:**
1. Harus berupa **matriks persegi** (jumlah baris dan kolom sama, misal $2 \times 2$ atau $3 \times 3$).
2. Determinannya tidak boleh bernilai nol ($\det(A) \neq 0$). Jika $\det(A) = 0$, matriks tersebut tidak memiliki kebalikan (disebut *matriks singular*).

#### **Rumus Invers Matriks $2 \times 2$:**
Jika $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$, maka:
$$A^{-1} = \frac{1}{\det(A)} \begin{pmatrix} d & -b \\ -c & a \end{pmatrix} = \frac{1}{ad - bc} \begin{pmatrix} d & -b \\ -c & a \end{pmatrix}$$

---

### **2. Posisi Perkalian Sangat Penting! (Pembagian Kiri vs Kanan)**
Karena perkalian matriks tidak bersifat komutatif ($A \times B \neq B \times A$), kita harus sangat berhati-hati dalam menaruh posisi matriks invers. Kita membaginya menjadi dua kasus:

| Kasus | Persamaan Asal | Cara Menyelesaikan | Posisi Invers |
| :--- | :--- | :--- | :--- |
| **Pembagian Kiri** | $A \cdot X = B$ | $X = A^{-1} \cdot B$ | Invers di depan ($A^{-1}$ di kiri) |
| **Pembagian Kanan** | $X \cdot A = B$ | $X = B \cdot A^{-1}$ | Invers di belakang ($A^{-1}$ di kanan) |

---

### **3. Contoh Kasus Perhitungan Manual (Step-by-Step)**
Selesaikan persamaan matriks berikut untuk mencari matriks $X$:
$$\begin{pmatrix} 2 & 1 \\ 5 & 3 \end{pmatrix} \cdot X = \begin{pmatrix} 4 \\ 11 \end{pmatrix}$$

Persamaan ini berbentuk $A \cdot X = B$, maka penyelesaiannya menggunakan **Pembagian Kiri**: $X = A^{-1} \cdot B$.

---

#### **Langkah 1: Hitung Determinan Matriks $A$**
Sebelum mencari kebalikan matriks, kita harus menghitung determinannya terlebih dahulu. Nilai determinan ini berfungsi sebagai penyebut/pembagi utama rumus invers. 

*Jika determinan bernilai 0, maka matriks tidak memiliki invers dan pembagian tidak bisa diselesaikan.*

* Matriks $A = \begin{pmatrix} 2 & 1 \\ 5 & 3 \end{pmatrix} \implies a=2, b=1, c=5, d=3$
* Rumus Determinan: 
  $$\det(A) = ad - bc$$
* Substitusi Nilai: 
  $$\det(A) = (2 \times 3) - (1 \times 5) = 6 - 5 = 1$$

---

#### **Langkah 2: Temukan Invers Matriks $A$ ($A^{-1}$)**
Untuk mencari invers matriks $2 \times 2$, kita menukar posisi elemen diagonal utama ($a$ dengan $d$), memberikan tanda negatif pada diagonal samping ($b$ dan $c$), lalu mengalikannya dengan hasil $\frac{1}{\det(A)}$.

* **Tukar posisi $a$ dan $d$:** Angka $2$ dan $3$ bertukar posisi menjadi $3$ dan $2$.
* **Ubah tanda $b$ dan $c$:** Angka $1$ dan $5$ berubah tanda menjadi $-1$ dan $-5$.
* **Rumus Invers:**
  $$A^{-1} = \frac{1}{\det(A)} \begin{pmatrix} d & -b \\ -c & a \end{pmatrix}$$
* **Substitusi Nilai:**
  $$A^{-1} = \frac{1}{1} \begin{pmatrix} 3 & -1 \\ -5 & 2 \end{pmatrix} = \begin{pmatrix} 3 & -1 \\ -5 & 2 \end{pmatrix}$$

---

#### **Langkah 3: Kalikan Invers Matriks dengan Matriks Hasil ($X = A^{-1} \cdot B$)**
Langkah terakhir adalah melakukan perkalian matriks (*dot product*) antara matriks invers $A^{-1}$ (dari arah kiri) dengan matriks hasil $B$.

* **Persamaan:**
  $$X = \begin{pmatrix} 3 & -1 \\ -5 & 2 \end{pmatrix} \begin{pmatrix} 4 \\ 11 \end{pmatrix}$$

* **Pekalian Baris 1 dengan Kolom 1 (untuk mendapatkan elemen baris atas):**
  $$(3 \times 4) + (-1 \times 11) = 12 - 11 = 1$$

* **Perkalian Baris 2 dengan Kolom 1 (untuk mendapatkan elemen baris bawah):**
  $$(-5 \times 4) + (2 \times 11) = -20 + 22 = 2$$

* **Hasil Akhir Matriks $X$:**
  $$X = \begin{pmatrix} 1 \\ 2 \end{pmatrix}$$

---

### **4. Implementasi Komputasi dengan Python (NumPy)**

Dalam pemrograman Python, library **NumPy** menyediakan cara mudah untuk mencari invers dengan `np.linalg.inv()` dan menyelesaikannya secara cepat dengan fungsi solver `np.linalg.solve()`.

```python
import numpy as np

# 1. Definisikan matriks A dan B
A = np.array([
    [2, 1],
    [5, 3]
], dtype=float)

B = np.array([
    [4],
    [11]
], dtype=float)

# Metode 1: Menggunakan Perkalian Invers Manual (A^-1 @ B)
A_inv = np.linalg.inv(A)
X_invers = A_inv @ B

# Metode 2: Menggunakan np.linalg.solve (Direkomendasikan & Lebih Stabil)
X_solve = np.linalg.solve(A, B)

# Cetak hasil verifikasi
print("Matriks A:")
print(A)
print("\nMatriks B:")
print(B)
print("\nInvers Matriks A (A^-1):")
print(A_inv)
print("\nHasil X (Metode Invers Manual):")
print(X_invers)
print("\nHasil X (Metode np.linalg.solve):")
print(X_solve)
```
