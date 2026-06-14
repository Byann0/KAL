---
title: Penjumlahan Matrix
date: 2026-06-12
---

## Penjumlahan Matriks

Penjumlahan matriks adalah operasi dasar aljabar linear untuk menjumlahkan dua matriks dengan menjumlahkan elemen-elemen yang berada di posisi yang sama (seletak).

### **Syarat Penjumlahan Matriks**
Dua matriks atau lebih hanya dapat dijumlahkan jika dan hanya jika memiliki **ordo (dimensi/ukuran) yang sama**. Misalnya, matriks berukuran $2 \times 2$ hanya bisa dijumlahkan dengan matriks berukuran $2 \times 2$. Jika ukuran ordo berbeda, maka penjumlahan tersebut **tidak terdefinisi**.

---

### **Sifat-Sifat Penjumlahan Matriks**
Penjumlahan matriks memenuhi sifat-sifat aljabar berikut:
1. **Komutatif:** 
   $$A + B = B + A$$
2. **Asosiatif:** 
   $$(A + B) + C = A + (B + C)$$
3. **Elemen Identitas (Matriks Nol):** 
   $$A + O = O + A = A$$
   *(Dimana $O$ adalah matriks yang seluruh elemennya bernilai $0$ dengan ordo yang sama dengan $A$)*
4. **Lawan Matriks (Invers Tambah):** 
   $$A + (-A) = O$$

---

### **Perhitungan Manual**
Secara umum, jika kita memiliki dua matriks berukuran $2 \times 2$:
$$A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}, \quad B = \begin{pmatrix} e & f \\ g & h \end{pmatrix}$$

Maka hasil penjumlahannya adalah:
$$A + B = \begin{pmatrix} a+e & b+f \\ c+g & d+h \end{pmatrix}$$

#### **Contoh Kasus:**
Diberikan matriks:
$$A = \begin{pmatrix} 2 & 4 \\ 1 & 3 \end{pmatrix}, \quad B = \begin{pmatrix} 5 & 1 \\ 0 & 2 \end{pmatrix}$$

Maka hasil penjumlahannya:
$$A + B = \begin{pmatrix} 2+5 & 4+1 \\ 1+0 & 3+2 \end{pmatrix} = \begin{pmatrix} 7 & 5 \\ 1 & 5 \end{pmatrix}$$

---

### **Implementasi Komputasi dengan Python (NumPy)**

Dalam pemrograman Python, kita menggunakan library **NumPy** untuk melakukan operasi matriks secara cepat dan efisien menggunakan operator `+`.

```python
import numpy as np

# 1. Definisikan matriks A dan B
A = np.array([
    [2, 4],
    [1, 3]
], dtype=float)

B = np.array([
    [5, 1],
    [0, 2]
], dtype=float)

# 2. Lakukan penjumlahan matriks
hasil = A + B

# 3. Tampilkan hasil
print("Matriks A:")
print(A)
print("\nMatriks B:")
print(B)
print("\nHasil A + B:")
print(hasil)
```
