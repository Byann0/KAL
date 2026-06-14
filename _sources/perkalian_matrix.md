---
title: Perkalian Matrix
date: 2026-06-12
---

## Perkalian Matriks

Dalam aljabar linear, operasi perkalian pada matriks dibagi menjadi dua jenis utama, yaitu perkalian matriks dengan skalar (angka tunggal) dan perkalian matriks dengan matriks lainnya.

---

### **1. Perkalian Matriks dengan Skalar**
Perkalian skalar dilakukan dengan mengalikan suatu bilangan real (skalar $k$) dengan setiap elemen yang ada di dalam matriks.

#### **Rumus dan Contoh:**
Jika $k$ adalah skalar dan $A$ adalah matriks $2 \times 2$:
$$k \cdot \begin{pmatrix} a & b \\ c & d \end{pmatrix} = \begin{pmatrix} ka & kb \\ kc & kd \end{pmatrix}$$

Misalnya, $k = 3$ dan $A = \begin{pmatrix} 1 & 4 \\ 2 & 5 \end{pmatrix}$:
$$3 \cdot \begin{pmatrix} 1 & 4 \\ 2 & 5 \end{pmatrix} = \begin{pmatrix} 3(1) & 3(4) \\ 3(2) & 3(5) \end{pmatrix} = \begin{pmatrix} 3 & 12 \\ 6 & 15 \end{pmatrix}$$

---

### **2. Perkalian Matriks dengan Matriks**
Perkalian dua matriks tidak dilakukan dengan mengalikan elemen-elemen yang seletak, melainkan dengan prinsip **mengalikan elemen-elemen baris pada matriks pertama dengan elemen-elemen kolom pada matriks kedua**.

#### **Syarat Perkalian Matriks**
Dua matriks $A$ (berukuran $m \times n$) dan $B$ (berukuran $p \times q$) dapat dikalikan ($A \times B$) jika dan hanya jika **jumlah kolom matriks pertama sama dengan jumlah baris matriks kedua** ($n = p$). Matriks hasil perkalian akan memiliki ukuran $m \times q$.

$$\text{Ukuran: } (m \times \mathbf{n}) \times (\mathbf{n} \times q) \implies (m \times q)$$

#### **Sifat-Sifat Perkalian Matriks**
1. **Tidak Komutatif (Secara Umum):** 
   $$A \times B \neq B \times A$$
2. **Asosiatif:** 
   $$(A \times B) \times C = A \times (B \times C)$$
3. **Distributif:** 
   $$A \times (B + C) = A \times B + A \times C$$
4. **Matriks Identitas ($I$):** 
   $$A \times I = I \times A = A$$

---

### **Perhitungan Manual (Dot Product)**
Misalkan kita memiliki dua matriks berukuran $2 \times 2$:
$$A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}, \quad B = \begin{pmatrix} 5 & 6 \\ 7 & 8 \end{pmatrix}$$

Operasi perkaliannya adalah:
$$A \times B = \begin{pmatrix} \text{Baris 1 A} \cdot \text{Kolom 1 B} & \text{Baris 1 A} \cdot \text{Kolom 2 B} \\ \text{Baris 2 A} \cdot \text{Kolom 1 B} & \text{Baris 2 A} \cdot \text{Kolom 2 B} \end{pmatrix}$$

$$A \times B = \begin{pmatrix} 1(5) + 2(7) & 1(6) + 2(8) \\ 3(5) + 4(7) & 3(6) + 4(8) \end{pmatrix} = \begin{pmatrix} 5 + 14 & 6 + 16 \\ 15 + 28 & 18 + 32 \end{pmatrix} = \begin{pmatrix} 19 & 22 \\ 43 & 50 \end{pmatrix}$$

---

### **Kasus Khusus: Langkah Detail Perkalian Matriks $2 \times 2$ dengan Matriks $2 \times 2$**

Untuk mempermudah pemahaman langkah demi langkah, mari kita bedah perkalian dua matriks persegi $2 \times 2$ secara umum:

$$A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}, \quad B = \begin{pmatrix} e & f \\ g & h \end{pmatrix}$$

Matriks hasil perkalian $C = A \times B$ juga akan berukuran $2 \times 2$:
$$C = \begin{pmatrix} C_{11} & C_{12} \\ C_{21} & C_{22} \end{pmatrix}$$

Di mana setiap elemen dihitung dengan mengalikan baris matriks pertama dengan kolom matriks kedua:
1. **Mencari $C_{11}$ (Baris 1 Matriks A $\times$ Kolom 1 Matriks B):**
   $$C_{11} = a \cdot e + b \cdot g$$
2. **Mencari $C_{12}$ (Baris 1 Matriks A $\times$ Kolom 2 Matriks B):**
   $$C_{12} = a \cdot f + b \cdot h$$
3. **Mencari $C_{21}$ (Baris 2 Matriks A $\times$ Kolom 1 Matriks B):**
   $$C_{21} = c \cdot e + d \cdot g$$
4. **Mencari $C_{22}$ (Baris 2 Matriks A $\times$ Kolom 2 Matriks B):**
   $$C_{22} = c \cdot f + d \cdot h$$

#### **Contoh Soal dengan Angka:**
Misalkan kita ingin mengalikan matriks berikut:
$$A = \begin{pmatrix} 2 & 3 \\ 1 & 4 \end{pmatrix}, \quad B = \begin{pmatrix} 5 & 6 \\ 7 & 8 \end{pmatrix}$$

* **Langkah 1: Hitung $C_{11}$ (Baris 1 $\times$ Kolom 1)**
  $$C_{11} = 2(5) + 3(7) = 10 + 21 = 31$$
* **Langkah 2: Hitung $C_{12}$ (Baris 1 $\times$ Kolom 2)**
  $$C_{12} = 2(6) + 3(8) = 12 + 24 = 36$$
* **Langkah 3: Hitung $C_{21}$ (Baris 2 $\times$ Kolom 1)**
  $$C_{21} = 1(5) + 4(7) = 5 + 28 = 33$$
* **Langkah 4: Hitung $C_{22}$ (Baris 2 $\times$ Kolom 2)**
  $$C_{22} = 1(6) + 4(8) = 6 + 32 = 38$$

Sehingga diperoleh hasil akhir matriks perkalian $A \times B$:
$$C = \begin{pmatrix} 31 & 36 \\ 33 & 38 \end{pmatrix}$$

---

### **Implementasi Komputasi dengan Python (NumPy)**

Dalam Python, kita dapat menggunakan operator `@` atau fungsi `np.dot()` dari library **NumPy** untuk melakukan perkalian matriks.

```python
import numpy as np

# 1. Definisikan matriks A dan B
A = np.array([
    [1, 2],
    [3, 4]
], dtype=float)

B = np.array([
    [5, 6],
    [7, 8]
], dtype=float)

# 2. Lakukan perkalian matriks menggunakan operator '@'
hasil = A @ B

# 3. Tampilkan hasil
print("Matriks A:")
print(A)
print("\nMatriks B:")
print(B)
print("\nHasil A @ B (Perkalian Matriks):")
print(hasil)
```
