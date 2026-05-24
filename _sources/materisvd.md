





# Singular Value Decomposition (SVD)


>

## Pendahuluan

Singular Value Decomposition (SVD) adalah teknik faktorisasi matriks untuk menguraikan sebuah matriks menjadi tiga matriks lainnya, mengungkapkan aspek  penting dari struktural matriks aslinya. SVD digunakan dalam berbagai aplikasi, termasuk pemrosesan sinyal, kompresi gambar, dan reduksi dimensi dalam machine learning.



Materi ini  mengasumsikan kita memiliki pengetahuan dasar aljabar linear. Secara lebih spesifik, dan juga harus familiar dengan konsep-konsep seperti norma vektor dan matriks, rank matriks, dekomposisi eigen (vektor eigen dan nilai eigen), vektor ortonormal, dan proyeksi linear.



## Definisi Matematis

Dekomposisi nilai singular dari matriks riil $A$ berukuran $m\times n$ adalah faktorisasi berbentuk:

$$A=U\Sigma V^T$$

dengan:

- $U$ adalah matriks **ortogonal** berukuran $m\times m$ (yaitu, kolom dan barisnya adalah vektor ortonormal). Kolom-kolom $U$ disebut **vektor singular kiri** dari $A$.
- $\Sigma$ adalah matriks diagonal persegi panjang berukuran $m\times n$ dengan bilangan riil non-negatif pada diagonalnya. Entri diagonal $\sigma_i=\Sigma_{ii}$ dikenal sebagai **nilai singular** dari $A$ dan biasanya disusun dalam urutan menurun, yaitu $\sigma_1\ge\sigma_2\ge\dots\ge\sigma_n\ge 0$. Jumlah nilai singular yang tidak nol sama dengan rank dari $A$.
- $V$ adalah matriks ortogonal berukuran $n\times n$. Kolom-kolom $V$ disebut **vektor singular kanan** dari $A$.


## Algoritma SVD
Langkah algoritma SVD:

### **Langkah 1: Menghitung Vektor Singular Kiri**
- Hitung matriks $AA^T$ (berukuran $m \times m$)
- Cari **nilai-nilai eigen** dari $AA^T$
- **Rank(A) = k** = banyaknya nilai eigen yang **tidak nol**
- Nilai eigen ini akan digunakan untuk mendapatkan vektor-vektor kiri

### **Langkah 2: Membentuk Matriks U**
- Tentukan **vektor eigen** $\mathbf{u}_1, \mathbf{u}_2, ..., \mathbf{u}_m$ yang berkorespondensi dengan nilai eigen dari $AA^T$
- **Normalisasi** setiap vektor eigen:
  $$\mathbf{u}_i = \frac{\mathbf{u}_i}{\|\mathbf{u}_i\|}$$
  (dibagi dengan panjang/norm vektor)
- Susun vektor-vektor ini sebagai kolom matriks **U** (berukuran $m \times m$)

### **Langkah 3: Menghitung Vektor Singular Kanan dan Nilai Singular**
- Hitung matriks $A^TA$ (berukuran $n \times n$)
- Cari **nilai-nilai eigen** dari $A^TA$
- **Nilai singular** $\sigma_i$ adalah akar dari nilai eigen:
  $$\sigma_i = \sqrt{\lambda_i}$$
  di mana $\lambda_i$ adalah nilai eigen dari $A^TA$

### **Langkah 4: Membentuk Matriks V**
- Tentukan **vektor eigen** $\mathbf{v}_1, \mathbf{v}_2, ..., \mathbf{v}_n$ dari $A^TA$
- **Normalisasi** setiap vektor eigen
- Susun sebagai kolom matriks **V** (berukuran $n \times n$)
- Transpose menjadi $V^T$

### **Langkah 5: Membentuk Matriks Σ (Sigma)**
- Buat matriks **Σ** berukuran $m \times n$
- Elemen diagonal berisi **nilai singular** $\sigma_1, \sigma_2, ..., \sigma_k$
- **Urutkan dari besar ke kecil**: $\sigma_1 \geq \sigma_2 \geq ... \geq \sigma_k > 0$
- Elemen di luar diagonal = 0

### **Langkah 6: Hasil Dekomposisi**
- Matriks A dapat direkonstruksi sebagai:
  $$A = U \Sigma V^T$$

---

## **Ilustrasi Dimensi:**

$$A_{m \times n} = U_{m \times m} \cdot \Sigma_{m \times n} \cdot V^T_{n \times n}$$

---

## **Catatan**

1. **Nilai eigen $AA^T$ dan $A^TA$ adalah sama**
2. **Nilai singular** selalu **non-negatif** dan **real**
3. **U dan V adalah matriks ortogonal**: $U^TU = I$ dan $V^TV = I$

## Contoh



### **Matriks :**
$$A = \begin{bmatrix} 3 & 1 & 1 \\ -1 & 3 & 1 \end{bmatrix}$$
(matriks berukuran 2×3)

Carilah SVD dari matrik diatas

---

### **1: Menghitung $AA^T$ (untuk vektor singular kiri)**

$$AA^T = \begin{bmatrix} 3 & 1 & 1 \\ -1 & 3 & 1 \end{bmatrix} \begin{bmatrix} 3 & -1 \\ 1 & 3 \\ 1 & 1 \end{bmatrix}$$



---

### **2: Mencari Nilai Eigen dari $AA^T$**

Persamaan karakteristik:
$$\det(AA^T - \lambda I) = 0$$

$$\det\begin{bmatrix} 11-\lambda & 1 \\ 1 & 11-\lambda \end{bmatrix} = 0$$

$$(11-\lambda)^2 - 1 = 0$$
$$\lambda^2 - 22\lambda + 120 = 0$$
$$(\lambda - 12)(\lambda - 10) = 0$$

**Nilai eigen:** $\lambda_1 = 12$ dan $\lambda_2 = 10$

**Rank(A) = 2** karena ada 2 nilai eigen tidak nol.

---

### **3: Menentukan Matriks U (vektor eigen dari $AA^T$)**

Untuk mencari vektor eigen, selesaikan:
$$(\lambda I - AA^T)\mathbf{x} = 0$$

$$\begin{bmatrix} \lambda - 11 & -1 \\ -1 & \lambda - 11 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$$

**Untuk $\lambda_1 = 12$:**
$$\begin{bmatrix} 1 & -1 \\ -1 & 1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$$

Persamaan: $x_1 - x_2 = 0 \Rightarrow x_1 = x_2$

Vektor eigen: $\mathbf{u}_1 = \begin{bmatrix} 1 \\ 1 \end{bmatrix}$

**Normalisasi:** $\|\mathbf{u}_1\| = \sqrt{1^2 + 1^2} = \sqrt{2}$

$$\mathbf{u}_1 = \begin{bmatrix} 1/\sqrt{2} \\ 1/\sqrt{2} \end{bmatrix}$$

**Untuk $\lambda_2 = 10$:**
$$\begin{bmatrix} -1 & -1 \\ -1 & -1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$$

Persamaan: $-x_1 - x_2 = 0 \Rightarrow x_1 = -x_2$

Vektor eigen: $\mathbf{u}_2 = \begin{bmatrix} 1 \\ -1 \end{bmatrix}$

**Normalisasi:** $\|\mathbf{u}_2\| = \sqrt{1^2 + (-1)^2} = \sqrt{2}$

$$\mathbf{u}_2 = \begin{bmatrix} 1/\sqrt{2} \\ -1/\sqrt{2} \end{bmatrix}$$

---

### **HASIL :**

**Matriks U:**
$$U = \begin{bmatrix} 1/\sqrt{2} & 1/\sqrt{2} \\ 1/\sqrt{2} & -1/\sqrt{2} \end{bmatrix}$$

**Nilai singular:**
$$\sigma_1 = \sqrt{12} = 2\sqrt{3}, \quad \sigma_2 = \sqrt{10}$$



### **3: Singular Kanan ($A^TA$)**

#### **Mengapa menghitung $A^TA$?**
- $A$ berukuran $2 \times 3$, sehingga $A^T$ berukuran $3 \times 2$
- Hasil $A^TA$ adalah matriks $3 \times 3$ (lebih besar dari $AA^T$ yang $2 \times 2$)
- Vektor eigen dari $A^TA$ akan menjadi kolom matriks **V** (vektor singular **kanan**)

#### **Perhitungan $A^TA$:**

$$A^TA = \begin{bmatrix} 3 & -1 \\ 1 & 3 \\ 1 & 1 \end{bmatrix} \begin{bmatrix} 3 & 1 & 1 \\ -1 & 3 & 1 \end{bmatrix}$$




$$A^TA = \begin{bmatrix} 10 & 0 & 2 \\ 0 & 10 & 4 \\ 2 & 4 & 2 \end{bmatrix}$$

---

### **Nilai Eigen dari $A^TA$**

Diperoleh **3 nilai eigen**:
- $\lambda_1 = 12$ (terbesar)
- $\lambda_2 = 10$
- $\lambda_3 = 0$ (terkecil)


1. **Dua nilai eigen pertama** (12 dan 10) **SAMA** dengan nilai eigen $AA^T$ dari langkah sebelumnya
2. **Nilai eigen ketiga = 0** muncul karena $A^TA$ berukuran $3 \times 3$ sedangkan rank(A) = 2
3. Ini menunjukkan matriks A **tidak full column rank**

---

### **Nilai Singular**

Nilai singular ($\sigma_i$) adalah **akar dari nilai eigen yang tidak nol**:

$$\sigma_1 = \sqrt{\lambda_1} = \sqrt{12} = 2\sqrt{3} \approx 3.464$$
$$\sigma_2 = \sqrt{\lambda_2} = \sqrt{10} \approx 3.162$$

**Mengapa hanya yang tidak nol?**
- Nilai singular merepresentasikan "kekuatan" transformasi
- $\lambda_3 = 0$ berarti $\sigma_3 = 0$ (arah ini "dihilangkan" oleh matriks A)

---

### **4: Vektor-Vektor Eigen v₁, v₂, dan v₃**



Untuk mencari vektor eigen, kita selesaikan persamaan:
$$(A^TA - \lambda I)\mathbf{v} = \mathbf{0}$$

dengan $A^TA = \begin{bmatrix} 10 & 0 & 2 \\ 0 & 10 & 4 \\ 2 & 4 & 2 \end{bmatrix}$

---

#### **a. Mencari v₁ untuk $\lambda_1 = 12$**

$$(A^TA - 12I)\mathbf{v}_1 = \mathbf{0}$$

$$\begin{bmatrix} 10-12 & 0 & 2 \\ 0 & 10-12 & 4 \\ 2 & 4 & 2-12 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$$

$$\begin{bmatrix} -2 & 0 & 2 \\ 0 & -2 & 4 \\ 2 & 4 & -10 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$$

**Sistem persamaan:**
1. $-2x_1 + 0x_2 + 2x_3 = 0$ → $-2x_1 + 2x_3 = 0$ → $x_1 = x_3$
2. $0x_1 - 2x_2 + 4x_3 = 0$ → $-2x_2 + 4x_3 = 0$ → $x_2 = 2x_3$
3. $2x_1 + 4x_2 - 10x_3 = 0$

**Substitusi $x_1 = x_3$ dan $x_2 = 2x_3$ ke persamaan 3:**
$$2(x_3) + 4(2x_3) - 10x_3 = 0$$
$$2x_3 + 8x_3 - 10x_3 = 0$$
$$0 = 0 \quad \text{(terpenuhi)}$$

**Solusi:**
Misalkan $x_3 = 1$, maka:
- $x_1 = 1$
- $x_2 = 2$

$$\mathbf{v}_1 = \begin{bmatrix} 1 \\ 2 \\ 1 \end{bmatrix}$$

---

#### **b. Mencari v₂ untuk $\lambda_2 = 10$**

$$(A^TA - 10I)\mathbf{v}_2 = \mathbf{0}$$

$$\begin{bmatrix} 10-10 & 0 & 2 \\ 0 & 10-10 & 4 \\ 2 & 4 & 2-10 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$$

$$\begin{bmatrix} 0 & 0 & 2 \\ 0 & 0 & 4 \\ 2 & 4 & -8 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$$

**Sistem persamaan:**
1. $0x_1 + 0x_2 + 2x_3 = 0$ → $2x_3 = 0$ → $x_3 = 0$
2. $0x_1 + 0x_2 + 4x_3 = 0$ → $4x_3 = 0$ → $x_3 = 0$ (sama)
3. $2x_1 + 4x_2 - 8x_3 = 0$

**Karena $x_3 = 0$, persamaan 3 menjadi:**
$$2x_1 + 4x_2 = 0$$
$$x_1 + 2x_2 = 0$$
$$x_1 = -2x_2$$

**Solusi:**
Misalkan $x_2 = -1$, maka:
- $x_1 = -2(-1) = 2$
- $x_3 = 0$

$$\mathbf{v}_2 = \begin{bmatrix} 2 \\ -1 \\ 0 \end{bmatrix}$$

---

#### **c. Mencari v₃ untuk $\lambda_3 = 0$**

$$(A^TA - 0I)\mathbf{v}_3 = \mathbf{0}$$

$$\begin{bmatrix} 10 & 0 & 2 \\ 0 & 10 & 4 \\ 2 & 4 & 2 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$$

**Sistem persamaan:**
1. $10x_1 + 0x_2 + 2x_3 = 0$ → $10x_1 + 2x_3 = 0$ → $x_3 = -5x_1$
2. $0x_1 + 10x_2 + 4x_3 = 0$ → $10x_2 + 4x_3 = 0$ → $x_2 = -\frac{2}{5}x_3$
3. $2x_1 + 4x_2 + 2x_3 = 0$

**Substitusi $x_3 = -5x_1$ ke persamaan 2:**
$$x_2 = -\frac{2}{5}(-5x_1) = 2x_1$$

**Cek dengan persamaan 3:**
$$2x_1 + 4(2x_1) + 2(-5x_1) = 0$$
$$2x_1 + 8x_1 - 10x_1 = 0$$
$$0 = 0 \quad \text{(terpenuhi)}$$

**Solusi:**
Misalkan $x_1 = 1$, maka:
- $x_2 = 2$
- $x_3 = -5$

$$\mathbf{v}_3 = \begin{bmatrix} 1 \\ 2 \\ -5 \end{bmatrix}$$

---



### **Proses berikutnya Normalisasi dan Pembentukan Matriks V:**



#### **A. PROSES NORMALISASI**

Normalisasi adalah membagi setiap vektor dengan panjangnya (normnya) agar menjadi **vektor satuan** (panjang = 1).

---

#### **1. Normalisasi v₁ = [1, 2, 1]^T**

**Hitung panjang vektor:**
$$\|\mathbf{v}_1\| = \sqrt{1^2 + 2^2 + 1^2} = \sqrt{1 + 4 + 1} = \sqrt{6}$$

**Normalisasi:**
$$\hat{\mathbf{v}}_1 = \frac{\mathbf{v}_1}{\|\mathbf{v}_1\|} = \frac{1}{\sqrt{6}}\begin{bmatrix} 1 \\ 2 \\ 1 \end{bmatrix} = \begin{bmatrix} \frac{1}{\sqrt{6}} \\ \frac{2}{\sqrt{6}} \\ \frac{1}{\sqrt{6}} \end{bmatrix}$$

---

#### **2. Normalisasi v₂ = [2, -1, 0]^T**

**Hitung panjang vektor:**
$$\|\mathbf{v}_2\| = \sqrt{2^2 + (-1)^2 + 0^2} = \sqrt{4 + 1 + 0} = \sqrt{5}$$

**Normalisasi:**
$$\hat{\mathbf{v}}_2 = \frac{\mathbf{v}_2}{\|\mathbf{v}_2\|} = \frac{1}{\sqrt{5}}\begin{bmatrix} 2 \\ -1 \\ 0 \end{bmatrix} = \begin{bmatrix} \frac{2}{\sqrt{5}} \\ \frac{-1}{\sqrt{5}} \\ 0 \end{bmatrix}$$

---

#### **3. Normalisasi v₃ = [1, 2, -5]^T**

**Hitung panjang vektor:**
$$\|\mathbf{v}_3\| = \sqrt{1^2 + 2^2 + (-5)^2} = \sqrt{1 + 4 + 25} = \sqrt{30}$$

**Normalisasi:**
$$\hat{\mathbf{v}}_3 = \frac{\mathbf{v}_3}{\|\mathbf{v}_3\|} = \frac{1}{\sqrt{30}}\begin{bmatrix} 1 \\ 2 \\ -5 \end{bmatrix} = \begin{bmatrix} \frac{1}{\sqrt{30}} \\ \frac{2}{\sqrt{30}} \\ \frac{-5}{\sqrt{30}} \end{bmatrix}$$

---

#### **B. MEMBENTUK MATRIKS V**

Matriks **V** dibentuk dengan menyusun vektor-vektor yang sudah dinormalisasi sebagai **kolom-kolom**:

$$V = \begin{bmatrix} | & | & | \\ \hat{\mathbf{v}}_1 & \hat{\mathbf{v}}_2 & \hat{\mathbf{v}}_3 \\ | & | & | \end{bmatrix}$$

$$V = \begin{bmatrix} 
\frac{1}{\sqrt{6}} & \frac{2}{\sqrt{5}} & \frac{1}{\sqrt{30}} \\
\frac{2}{\sqrt{6}} & \frac{-1}{\sqrt{5}} & \frac{2}{\sqrt{30}} \\
\frac{1}{\sqrt{6}} & 0 & \frac{-5}{\sqrt{30}}
\end{bmatrix}$$

---

#### **C. MATRIKS V^T (Transpose)**

**Transpose** adalah menukar baris menjadi kolom (dan sebaliknya):

$$V^T = \begin{bmatrix} 
\frac{1}{\sqrt{6}} & \frac{2}{\sqrt{6}} & \frac{1}{\sqrt{6}} \\
\frac{2}{\sqrt{5}} & \frac{-1}{\sqrt{5}} & 0 \\
\frac{1}{\sqrt{30}} & \frac{2}{\sqrt{30}} & \frac{-5}{\sqrt{30}}
\end{bmatrix}$$

---

#### **D. VERIFIKASI SIFAT ORTOGONAL**

Karena vektor-vektor eigen sudah dinormalisasi dan saling ortogonal, matriks V memiliki sifat:

$$V^T V = I \quad \text{(matriks identitas)}$$

Ini berarti **V adalah matriks ortogonal**.

---

#### **Membentuk matriks **Σ****

Setelah mendapatkan V, langkah selanjutnya adalah:



 **Mengapa Ukuran 2 × 3?**

Matriks $\Sigma$ selalu berukuran **sama dengan matriks asli $A$**:
- $A$ berukuran $2 \times 3$ (2 baris, 3 kolom)
- Maka $\Sigma$ juga berukuran $2 \times 3$

Ini agar perkalian $U \Sigma V^T$ valid:
- $U$: $2 \times 2$
- $\Sigma$: $2 \times 3$
- $V^T$: $3 \times 3$
- Hasil: $(2 \times 2) \cdot (2 \times 3) \cdot (3 \times 3) = 2 \times 3$ ✓

---

#### **Struktur Matriks $\Sigma$**

$$\Sigma = \begin{bmatrix} \sigma_1 & 0 & 0 \\ 0 & \sigma_2 & 0 \end{bmatrix} = \begin{bmatrix} \sqrt{12} & 0 & 0 \\ 0 & \sqrt{10} & 0 \end{bmatrix}$$

**Karakteristik:**
1. **Diagonal utama** berisi nilai singular yang sudah diurutkan dari besar ke kecil:
   - $\sigma_1 = \sqrt{12} \approx 3.464$
   - $\sigma_2 = \sqrt{10} \approx 3.162$

2. **Elemen di luar diagonal** = 0

3. **Kolom ketiga** semua nol karena rank(A) = 2 (hanya ada 2 nilai singular tidak nol)

---

#### **Bentuk Umum $\Sigma$ untuk Matriks $m \times n$**

Untuk matriks $A_{m \times n}$ dengan $r = \text{rank}(A)$:

$$\Sigma = \begin{bmatrix} 
\sigma_1 & 0 & \cdots & 0 & \cdots & 0 \\
0 & \sigma_2 & \cdots & 0 & \cdots & 0 \\
\vdots & \vdots & \ddots & \vdots & & \vdots \\
0 & 0 & \cdots & \sigma_r & \cdots & 0 \\
\vdots & \vdots & & \vdots & 0 & \vdots \\
0 & 0 & \cdots & 0 & \cdots & 0
\end{bmatrix}_{m \times n}$$

---

#### **Mengapa Kolom Ketiga Nol?**

Karena:
- Rank(A) = 2 (hanya ada 2 nilai eigen tidak nol)
- Artinya hanya ada 2 nilai singular: $\sigma_1$ dan $\sigma_2$
- Kolom ketiga berkorespondensi dengan $\lambda_3 = 0$, jadi $\sigma_3 = 0$

Ini mencerminkan fakta bahwa matriks $A$ **tidak full rank** (ada ketergantungan linear di kolom-kolomnya).

---

###

Sekarang kita punya semua komponen:

$$A = U \Sigma V^T$$

$$A = \underbrace{\begin{bmatrix} \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{2}} \end{bmatrix}}_{U_{2\times2}} \underbrace{\begin{bmatrix} \sqrt{12} & 0 & 0 \\ 0 & \sqrt{10} & 0 \end{bmatrix}}_{\Sigma_{2\times3}} \underbrace{\begin{bmatrix} \frac{1}{\sqrt{6}} & \frac{2}{\sqrt{6}} & \frac{1}{\sqrt{6}} \\ \frac{2}{\sqrt{5}} & -\frac{1}{\sqrt{5}} & 0 \\ \frac{1}{\sqrt{30}} & \frac{2}{\sqrt{30}} & -\frac{5}{\sqrt{30}} \end{bmatrix}}_{V^T_{3\times3}}$$

## Implementasi Sagemath SVD

```{sagemath}
A = matrix(RDF, [[3, 1, 1], [-1, 3, 1]])
U, Sigma, Vt = A.SVD()
print(U, Sigma, Vt)
print(A.singular_values())   # [3.4641, 3.1623]
```

### Menggunakan python
```{python}
import numpy as np

A = np.array([[3, 1, 1],
              [-1, 3, 1]], dtype=float)

# Dekomposisi
U, s, Vt = np.linalg.svd(A)

# Bentuk Sigma (harus 2×3, sama ukuran dengan A)
Sigma = np.zeros_like(A)
np.fill_diagonal(Sigma, s)

# Rekonstruksi A = U · Σ · Vᵀ
A_kembali = U @ Sigma @ Vt

print(A_kembali)
# [[ 3.  1.  1.]
#  [-1.  3.  1.]]
```
