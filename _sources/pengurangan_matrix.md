---
title: Pengurangan Matrix
date: 2026-06-12
---

## Pengurangan Matriks

Pengurangan matriks adalah operasi aljabar linear dasar untuk mengurangkan elemen-elemen suatu matriks dengan elemen-elemen matriks lainnya yang berada di posisi yang seletak.

### **Syarat Pengurangan Matriks**
Sama halnya dengan penjumlahan, dua matriks atau lebih dapat dikurangkan jika dan hanya jika keduanya memiliki **ordo (dimensi/ukuran) yang sama**. Jika ordonya berbeda, maka hasil operasi pengurangan tersebut **tidak terdefinisi**.

---

### **Sifat-Sifat Pengurangan Matriks**
Berbeda dengan operasi penjumlahan, pengurangan matriks **tidak bersifat komutatif maupun asosiatif**:
1. **Tidak Komutatif:**
   $$A - B \neq B - A$$
2. **Tidak Asosiatif:**
   $$(A - B) - C \neq A - (B - C)$$

---

### **Perhitungan Manual**
Secara umum, jika kita memiliki dua matriks berukuran $2 \times 2$:
$$A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}, \quad B = \begin{pmatrix} e & f \\ g & h \end{pmatrix}$$

Maka hasil pengurangannya adalah:
$$A - B = \begin{pmatrix} a-e & b-f \\ c-g & d-h \end{pmatrix}$$

#### **Contoh Kasus:**
Diberikan matriks:
$$A = \begin{pmatrix} 8 & 6 \\ 5 & 4 \end{pmatrix}, \quad B = \begin{pmatrix} 3 & 2 \\ 1 & 4 \end{pmatrix}$$

Maka hasil pengurangannya:
$$A - B = \begin{pmatrix} 8-3 & 6-2 \\ 5-1 & 4-4 \end{pmatrix} = \begin{pmatrix} 5 & 4 \\ 4 & 0 \end{pmatrix}$$

---

### **Implementasi Komputasi dengan Python (NumPy)**

Dalam pemrograman Python, kita menggunakan library **NumPy** untuk melakukan pengurangan matriks secara instan menggunakan operator `-`.

```python
import numpy as np

# 1. Definisikan matriks A dan B
A = np.array([
    [8, 6],
    [5, 4]
], dtype=float)

B = np.array([
    [3, 2],
    [1, 4]
], dtype=float)

# 2. Lakukan pengurangan matriks
hasil = A - B

# 3. Tampilkan hasil
print("Matriks A:")
print(A)
print("\nMatriks B:")
print(B)
print("\nHasil A - B:")
print(hasil)
```
