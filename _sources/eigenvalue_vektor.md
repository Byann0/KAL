# Eigenvalue dan Eigenvector Matriks 2x2

Diketahui matriks:

\[
A =
\begin{bmatrix}
2 & 1 \\
1 & 2
\end{bmatrix}
\]

---

# 1. Mencari Eigenvalue

Gunakan persamaan karakteristik:

\[
\det(A-\lambda I)=0
\]

\[
\begin{vmatrix}
2-\lambda & 1 \\
1 & 2-\lambda
\end{vmatrix}=0
\]

Hitung determinan:

\[
(2-\lambda)(2-\lambda)-1=0
\]

\[
(2-\lambda)^2-1=0
\]

\[
4-4\lambda+\lambda^2-1=0
\]

\[
\lambda^2-4\lambda+3=0
\]

Faktorkan:

\[
(\lambda-3)(\lambda-1)=0
\]

Maka diperoleh eigenvalue:

\[
\lambda_1=3
\]

\[
\lambda_2=1
\]

---

# 2. Mencari Eigenvector

## Eigenvector untuk \(\lambda = 3\)

Gunakan:

\[
(A-3I)v=0
\]

\[
\begin{bmatrix}
2-3 & 1 \\
1 & 2-3
\end{bmatrix}
=
\begin{bmatrix}
-1 & 1 \\
1 & -1
\end{bmatrix}
\]

Misalkan:

\[
v=
\begin{bmatrix}
x\\
y
\end{bmatrix}
\]

Maka:

\[
-x+y=0
\]

\[
y=x
\]

Ambil:

\[
x=1
\]

Sehingga:

\[
v_1=
\begin{bmatrix}
1\\
1
\end{bmatrix}
\]

Normalisasi:

\[
||v_1||=\sqrt{1^2+1^2}=\sqrt{2}
\]

\[
q_1=
\frac{1}{\sqrt{2}}
\begin{bmatrix}
1\\
1
\end{bmatrix}
\]

---

## Eigenvector untuk \(\lambda = 1\)

Gunakan:

\[
(A-I)v=0
\]

\[
\begin{bmatrix}
1 & 1 \\
1 & 1
\end{bmatrix}
\]

Persamaan:

\[
x+y=0
\]

\[
y=-x
\]

Ambil:

\[
x=1
\]

Sehingga:

\[
v_2=
\begin{bmatrix}
1\\
-1
\end{bmatrix}
\]

Normalisasi:

\[
||v_2||=\sqrt{1^2+(-1)^2}=\sqrt{2}
\]

\[
q_2=
\frac{1}{\sqrt{2}}
\begin{bmatrix}
1\\
-1
\end{bmatrix}
\]

---

# 3. Gram-Schmidt

Matriks:

\[
A=
\begin{bmatrix}
2 & 1\\
1 & 2
\end{bmatrix}
\]

Kolom pertama:

\[
a_1=
\begin{bmatrix}
2\\
1
\end{bmatrix}
\]

Kolom kedua:

\[
a_2=
\begin{bmatrix}
1\\
2
\end{bmatrix}
\]

---

## Langkah 1: Vector Pertama

Normalisasi \(a_1\):

\[
||a_1||=\sqrt{2^2+1^2}
=\sqrt{5}
\]

\[
q_1=
\frac{a_1}{||a_1||}
=
\frac{1}{\sqrt{5}}
\begin{bmatrix}
2\\
1
\end{bmatrix}
\]

---

## Langkah 2: Vector Kedua

Hitung proyeksi \(a_2\) terhadap \(q_1\):

\[
a_2 \cdot q_1
=
\begin{bmatrix}
1\\
2
\end{bmatrix}
\cdot
\frac{1}{\sqrt5}
\begin{bmatrix}
2\\
1
\end{bmatrix}
\]

\[
=
\frac{2+2}{\sqrt5}
=
\frac{4}{\sqrt5}
\]

Proyeksi:

\[
(a_2 \cdot q_1)q_1
=
\frac45
\begin{bmatrix}
2\\
1
\end{bmatrix}
=
\begin{bmatrix}
8/5\\
4/5
\end{bmatrix}
\]

Cari vector tegak lurus:

\[
v_2
=
a_2-(a_2 \cdot q_1)q_1
\]

\[
=
\begin{bmatrix}
1\\
2
\end{bmatrix}
-
\begin{bmatrix}
8/5\\
4/5
\end{bmatrix}
\]

\[
=
\begin{bmatrix}
-3/5\\
6/5
\end{bmatrix}
\]

Norm:

\[
||v_2||
=
\sqrt{
\left(-\frac35\right)^2+
\left(\frac65\right)^2
}
\]

\[
=
\sqrt{
\frac9{25}+\frac{36}{25}
}
=
\sqrt{\frac{45}{25}}
=
\frac{3}{\sqrt5}
\]

Normalisasi:

\[
q_2=
\frac{v_2}{||v_2||}
=
\begin{bmatrix}
-\frac1{\sqrt5}\\
\frac2{\sqrt5}
\end{bmatrix}
\]

---

# 4. Python Code

```python
import numpy as np

# Matriks
A = np.array([
    [2, 1],
    [1, 2]
])

# =========================
# Eigenvalue & Eigenvector
# =========================
eigenvalues, eigenvectors = np.linalg.eig(A)

print("Matriks A:")
print(A)

print("\nEigenvalue:")
print(eigenvalues)

print("\nEigenvector:")
print(eigenvectors)

# =========================
# Gram-Schmidt
# =========================

# Ambil kolom matriks
a1 = A[:, 0]
a2 = A[:, 1]

# Langkah 1
q1 = a1 / np.linalg.norm(a1)

# Langkah 2
proj = np.dot(a2, q1) * q1
v2 = a2 - proj
q2 = v2 / np.linalg.norm(v2)

print("\nq1:")
print(q1)

print("\nProyeksi a2 ke q1:")
print(proj)

print("\nv2:")
print(v2)

print("\nq2:")
print(q2)

# Matriks Q
Q = np.column_stack((q1, q2))

print("\nMatriks Q:")
print(Q)
```

---

# Hasil Akhir

## Eigenvalue

\[
\lambda_1 = 3
\]

\[
\lambda_2 = 1
\]

---

## Eigenvector

\[
v_1=
\begin{bmatrix}
1\\
1
\end{bmatrix}
\]

\[
v_2=
\begin{bmatrix}
1\\
-1
\end{bmatrix}
\]

---

## Matriks Q Gram-Schmidt

\[
Q=
\begin{bmatrix}
0.8944 & -0.4472 \\
0.4472 & 0.8944
\end{bmatrix}
\]