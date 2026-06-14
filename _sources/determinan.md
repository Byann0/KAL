---
title: Determinan
date: 2026-04-12
---

# Pengantar Determinan Matriks

Dalam aljabar linear, **determinan** adalah nilai skalar unik yang dapat dihitung dari elemen-elemen suatu matriks persegi (matriks dengan jumlah baris dan kolom yang sama, yaitu ordo $n \times n$). Determinan berfungsi sebagai representasi numerik yang merangkum karakteristik geometris dan aljabar penting dari suatu matriks.

---

## Fungsi Utama dan Signifikansi Determinan

Determinan memiliki beberapa peran krusial dalam matematika dan komputasi aljabar linear:

1. **Menentukan Keberadaan Invers Matriks:**
   Determinan merupakan syarat mutlak untuk menentukan apakah suatu matriks memiliki invers ($A^{-1}$):
   * Jika $\det(A) \neq 0$, matriks disebut **non-singular** (memiliki invers).
   * Jika $\det(A) = 0$, matriks disebut **singular** (tidak memiliki invers).
2. **Penyelesaian Sistem Persamaan Linear (SPL):**
   Digunakan secara langsung dalam **Aturan Cramer** untuk menentukan solusi SPL persegi secara analitis.
3. **Interpretasi Geometris (Skala Transformasi):**
   Dalam geometri dan grafik komputer, determinan mengukur faktor skala perubahan ukuran suatu objek setelah dikenai transformasi linear:
   * Pada dimensi 2 (matriks $2 \times 2$), determinan mutlak menyatakan luas daerah.
   * Pada dimensi 3 (matriks $3 \times 3$), determinan mutlak menyatakan volume bangun ruang.

---

## Metode Perhitungan Determinan

Cara menghitung nilai determinan sangat bergantung pada ordo (ukuran) matriks persegi tersebut:

### 1. Matriks Ordo $2 \times 2$

Untuk matriks berukuran $2 \times 2$:

$$
A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}
$$

Determinan dihitung dengan mengalikan elemen-elemen diagonal utama lalu dikurangi dengan hasil kali elemen-elemen diagonal samping:

$$
\det(A) = |A| = ad - bc
$$

---

### 2. Matriks Ordo $3 \times 3$ (Metode Sarrus)

Metode Sarrus merupakan cara praktis yang khusus digunakan untuk matriks ordo $3 \times 3$:

$$
A = \begin{bmatrix} 
a & b & c \\ 
d & e & f \\ 
g & h & i 
\end{bmatrix}
$$

**Skema Perhitungan Sarrus:**
Perhitungan dilakukan dengan menuliskan kembali dua kolom pertama di sebelah kanan matriks, kemudian menjumlahkan hasil kali elemen diagonal dari kiri-atas ke kanan-bawah, lalu dikurangi dengan jumlah hasil kali elemen diagonal dari kiri-bawah ke kanan-atas:

$$
\det(A) = (aei + bfg + cdh) - (ceg + afh + bdi)
$$

---

### 3. Matriks Ordo $n \times n$ (Metode Ekspansi Kofaktor / Laplace)

Untuk matriks berordo lebih besar (seperti $4 \times 4$ ke atas), digunakan metode ekspansi kofaktor sepanjang baris ke-$i$ atau kolom ke-$j$:

$$
\det(A) = \sum_{k=1}^n a_{ik} C_{ik}
$$

Di mana:
* $a_{ik}$ adalah elemen matriks pada baris ke-$i$ dan kolom ke-$k$.
* $C_{ik}$ adalah **kofaktor** yang diperoleh dari rumus:
  $$C_{ik} = (-1)^{i+k} M_{ik}$$
* $M_{ik}$ adalah **minor**, yaitu determinan submatriks yang diperoleh dengan menghapus baris ke-$i$ dan kolom ke-$k$ dari matriks asal.

---

## Sifat-Sifat Utama Determinan

Untuk menyederhanakan perhitungan matriks yang kompleks, beberapa sifat determinan berikut dapat digunakan:

* **Transpose:** Determinan matriks transpose sama dengan determinan matriks asalnya: $\det(A^T) = \det(A)$.
* **Perkalian Matriks:** Determinan dari hasil kali dua matriks sama dengan hasil kali determinan masing-masing matriks: $\det(A \cdot B) = \det(A) \cdot \det(B)$.
* **Invers:** Determinan dari invers suatu matriks adalah kebalikan dari determinan matriks asalnya: $\det(A^{-1}) = \frac{1}{\det(A)}$.
* **Baris/Kolom Nol:** Jika suatu matriks memiliki satu baris atau satu kolom yang semua elemennya bernilai $0$, maka nilai determinannya adalah $0$.
* **Baris/Kolom Identik:** Jika terdapat dua baris atau dua kolom yang memiliki elemen yang sama (atau kelipatannya), maka nilai determinannya adalah $0$.
