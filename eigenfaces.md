# Pengenalan Wajah: Eigenfaces Berbasis SVD

Alur kerja matematis dan implementasi terprogram dari algoritma Eigenfaces menggunakan metode dekomposisi matriks Singular Value Decomposition (SVD) untuk mengenali wajah dari dataset berisi 410 foto.

## 1. Teori SVD (Standar Aljabar Linear)

Berdasarkan teori aljabar linear, setiap matriks data $A$ berukuran $M \times N$ dapat difaktorkan menjadi perkalian tiga matriks terpisah:

$$A = U \Sigma V^T$$

Dalam proyek pengenalan wajah ini, variabel matriks tersebut memiliki representasi fisik sebagai berikut:

- Matriks $A$ (Matriks Data Terpusat):
Berukuran $4096 \times 410$. Setiap kolom merepresentasikan 1 foto wajah yang telah dikonversi menjadi vektor kolom dimensi tinggi dan dikurangi wajah rata-rata.
- Matriks $U$ (Left Singular Vectors / Eigenfaces): Berukuran $4096 \times 410$ (pada Economy SVD). Kolom-kolom di dalam matriks ini adalah vektor eigen dari matriks kovarians data yang menyimpan arah variasi geometri wajah terbesar (mata, hidung, bibir).
- Matriks $\Sigma$ (Singular Values): Matriks diagonal berukuran $410 \times 410$ yang menyimpan tingkat kepentingan/magnitudo informasi dari setiap Eigenface, terurut dari nilai terbesar hingga terkecil.
- Matriks $V^T$ (Right Singular Vectors): Matriks berukuran $410 \times 410$ yang menyimpan koefisien relasi atau koordinat gambar asli di dalam database.

## 2. Alur Kerja Matematis & Bedah Potongan Kode

### 1 Konstruksi Matriks Data Wajah ($A$)

Setiap gambar 2D berukuran $64 \times 64$ piksel diubah menjadi vektor baris/kolom 1D (flattening) sepanjang 4096 piksel ($M = 4096$). Seluruh 410 foto ($N = 410$) digabungkan secara berdampingan menjadi satu matriks raksasa.

```python
# .flatten() mengubah matriks 2D (64x64) menjadi array 1D sepanjang 4096
matriks_wajah.append(img_resized.flatten())

# Melakukan Transpose (.T) agar ukuran matriks menjadi (Piksel x Jumlah_Foto) -> (4096 x 410)
A = np.array(matriks_wajah).T
```

### 2 Sentralisasi Data (Mean Subtraction)

Untuk membuang kemiripan latar belakang ruangan atau pencahayaan konstan, sistem menghitung Wajah Rata-rata ($\Psi$) dari seluruh foto, lalu mengurangi setiap foto asli dengan nilai tersebut untuk menyisakan fitur unik wajah.

$$\Phi_i = \Gamma_i - \Psi$$

```python
# axis=1 menghitung rata-rata nilai piksel secara horizontal melewati 410 foto
wajah_rata_rata = np.mean(A, axis=1, keepdims=True)
A_terpusat = A - wajah_rata_rata
```

### 3 Ekstraksi Fitur Utama lewat SVD dan Trunkasi ($k=50$)

Kita menggunakan Economy SVD (full_matrices=False) agar komputasi efisien. Mengingat nilai singular pada matriks $\Sigma$ sudah terurut, kita memotong data dengan hanya mengambil $k = 50$ kolom pertama dari matriks $U$ untuk mereduksi dimensi data dari 4096 piksel menjadi hanya 50 fitur utama.

```python
# Menghitung faktorisasi matriks
U, S, Vt = np.linalg.svd(A_terpusat, full_matrices=False)

# Mengambil k komponen utama (Trunkasi Subspace)
eigenfaces = U[:, :self.k_komponen]  # Menghasilkan matriks ukuran (4096 x 50)
```

### 4 Proyeksi dan Penyimpanan Vektor Bobot ($\Omega$)

Seluruh wajah terpusat di database diproyeksikan ke dalam ruang eigen dimensi rendah ($U_k$) untuk mendapatkan koordinat ringkasnya masing-masing.

$$\Omega = U_k^T \cdot A_{\text{terpusat}}$$

```python
# Mengalikan transpose Eigenfaces dengan Matriks Terpusat
bobot_training = eigenfaces.T @ A_terpusat  # Menghasilkan matriks ukuran (50 x 410)
```

### 5 Identifikasi Wajah Baru Menggunakan Euclidean Distance

Ketika ada file test_wajah.jpg masuk, gambar tersebut diproses ke dalam format yang sama, diproyeksikan ke ruang eigen menjadi koordinat bobot_baru ($50 \times 1$), lalu dihitung jarak geometris L2-Normnya terhadap 410 data di database.

$$\epsilon = \sqrt{\sum_{j=1}^{50} (\omega_{\text{baru}, j} - \omega_{\text{database}, j})^2}$$

```python
# Menghitung Euclidean Distance antara bobot baru dengan seluruh kolom database
jarak = np.linalg.norm(bobot_baru - self.bobot_training[:, i:i+1])
indeks_terdekat = np.argmin(jarak_list) # Mencari jarak paling minimum/mirip
```

## 3. Hasil Interpretasi Grafik Grafis

A. Jendela Visualisasi Eigenfaces (Ghost Wajah)

Ketika fungsi visualisasikan_eigenfaces() dijalankan, vektor eigen kolom pada matriks $U$ dipetakan kembali ke bentuk spasialnya.

- Eigenface 1, 2, dan 3: Menghasilkan visualisasi wajah abstrak kabur yang dominan menangkap variasi arah jatuhnya pencahayaan (kontras bayangan kiri, kanan, atau atas).

- Eigenface 4 hingga 10: Mulai mendeteksi fitur pembentuk wajah secara spesifik seperti struktur tulang rahang, bentuk bayangan garis bibir, posisi lengkungan alis, dan lebar cuping hidung.

B. Jendela Scree Plot (Retensi Energi Singular)

Melalui fungsi plot_retensi_energi(), nilai kuadrat dari komponen diagonal $\Sigma$ dijumlahkan secara akumulatif.

- Kurva melonjak tajam pada nilai $k$ awal dan melandai di akhir, membuktikan bahwa variasi terbesar data langsung terkonsentrasi di komponen-komponen awal.

- Titik koordinat penanda merah menunjukkan bahwa dengan nilai $k = 50$, sistem berhasil mempertahankan sekitar 85% hingga 95% total informasi varians penting dari seluruh gambar asli, sementara sisa dimensi yang dibuang hanyalah noise frekuensi tinggi yang tidak berdampak signifikan pada proses pengenalan wajah.

## 4. Kode Program

```python
import os
import cv2
import numpy as np

class EigenfaceRecognizer:
    def __init__(self, target_size=(64, 64), k_komponen=50):
        self.target_size = target_size
        self.k_komponen = k_komponen
        self.wajah_rata_rata = None
        self.eigenfaces = None
        self.bobot_training = None
        self.label_wajah = []

    def latih_model(self, folder_path):
        print("=== Memulai Tahap Training ===")
        matriks_wajah = []
        
        # 1. Membaca seluruh 410 foto dari folder
        daftar_file = [f for f in os.listdir(folder_path) if f.endswith(('.jpg', '.jpeg', '.png'))]
        if len(daftar_file) == 0:
            raise ValueError(f"Tidak ada foto berformat gambar ditemukan di folder '{folder_path}'")
            
        for filename in daftar_file:
            path = os.path.join(folder_path, filename)
            img = cv2.imread(path, cv2.IMREAD_GRAYSCALE)
            img_resized = cv2.resize(img, self.target_size)
            
            # Ubah jadi vektor 1D dan masukkan ke list
            matriks_wajah.append(img_resized.flatten())
            self.label_wajah.append(filename) # Menyimpan nama file sebagai identitas
            
        # Bentuk Matriks Data A (Ukuran: Piksel x Jumlah_Foto)
        A = np.array(matriks_wajah).T
        print(f"Matriks Data Wajah (A) berhasil dibentuk dengan ukuran: {A.shape}")
        
        # 2. Sentralisasi Data (Mean Subtraction)
        self.wajah_rata_rata = np.mean(A, axis=1, keepdims=True)
        A_terpusat = A - self.wajah_rata_rata
        
        # 3. Hitung SVD sesuai teori matematika
        print("Menghitung Singular Value Decomposition (SVD)...")
        U, S, Vt = np.linalg.svd(A_terpusat, full_matrices=False)
        self.S = S
        
        # 4. Ambil k-Eigenfaces terbesar untuk reduksi dimensi
        self.eigenfaces = U[:, :self.k_komponen]
        print(f"Eigenspace (Eigenfaces) berhasil dibentuk dengan ukuran: {self.eigenfaces.shape}")
        
        # 5. Proyeksikan data training ke Eigenspace untuk mendapat vektor bobot
        self.bobot_training = self.eigenfaces.T @ A_terpusat
        print("Model berhasil dilatih dan vektor bobot disimpan.\n")

    def kenali_wajah_baru(self, path_wajah_baru):
        if self.eigenfaces is None:
            raise ValueError("Model belum dilatih! Jalankan 'latih_model()' terlebih dahulu.")
            
        # 1. Baca dan preprocess wajah baru
        img = cv2.imread(path_wajah_baru, cv2.IMREAD_GRAYSCALE)
        img_resized = cv2.resize(img, self.target_size)
        vektor_baru = img_resized.flatten().reshape(-1, 1) # Jadikan vektor kolom
        
        # 2. Sentralisasi wajah baru terhadap wajah rata-rata training
        vektor_terpusat = vektor_baru - self.wajah_rata_rata
        
        # 3. Proyeksikan ke Eigenspace untuk mendapatkan vektor bobot baru
        bobot_baru = self.eigenfaces.T @ vektor_terpusat
        
        # 4. Hitung Euclidean Distance dengan seluruh 410 data training
        jarak_list = []
        for i in range(self.bobot_training.shape[1]):
            jarak = np.linalg.norm(bobot_baru - self.bobot_training[:, i:i+1])
            jarak_list.append(jarak)
            
        # 5. Cari indeks dengan jarak terpendek (paling mirip)
        indeks_terdekat = np.argmin(jarak_list)
        jarak_terdekat = jarak_list[indeks_terdekat]
        nama_orang_mirip = self.label_wajah[indeks_terdekat]
        
        return nama_orang_mirip, jarak_terdekat
    
    def visualisasikan_eigenfaces(self, jumlah_tampil=10):
        import matplotlib.pyplot as plt
        if self.eigenfaces is None:
            print("[-] Model belum dilatih!")
            return
        
        print(f"[*] Menampilkan {jumlah_tampil} Eigenfaces pertama...")
        plt.figure(figsize=(15, 6))
        for i in range(jumlah_tampil):
            plt.subplot(2, 5, i + 1)
            # Reshape kembali dari vektor 1D (4096) ke matriks 2D (64x64)
            komponen_wajah = self.eigenfaces[:, i].reshape(self.target_size)
            
            plt.imshow(komponen_wajah, cmap='gray')
            plt.title(f"Eigenface {i+1}")
            plt.axis('off')
            
        plt.suptitle("Visualisasi Basis Subspace (Eigenfaces)", fontsize=16, fontweight='bold')
        plt.tight_layout()
        plt.show()
        
    def plot_retensi_energi(self):
        import matplotlib.pyplot as plt
        if self.S is None:
            print("[-] Data Nilai Singular tidak ditemukan!")
            return
        
        # Hitung varians / energi kumulatif berdasarkan nilai kuadrat singular values
        energi_total = np.sum(self.S**2)
        energi_kumulatif = np.cumsum(self.S**2) / energi_total * 100
        
        plt.figure(figsize=(9, 5))
        # Plot garis energi kumulatif
        plt.plot(range(1, len(energi_kumulatif) + 1), energi_kumulatif, color='blue', linewidth=2)
        
        # Beri tanda titik merah pada batas k komponen yang kita pilih (k=50)
        persen_terpilih = energi_kumulatif[self.k_komponen - 1]
        plt.scatter(self.k_komponen, persen_terpilih, color='red', s=100, zorder=5)
        plt.axhline(y=persen_terpilih, color='red', linestyle='--')
        plt.axvline(x=self.k_komponen, color='red', linestyle='--')
        
        plt.title("Scree Plot: Retensi Energi Kumulatif Nilai Singular", fontsize=12, fontweight='bold')
        plt.xlabel("Jumlah Komponen Utama (k)")
        plt.ylabel("Persentase Informasi / Energi Kumulatif (%)")
        plt.text(self.k_komponen + 10, persen_terpilih - 5, f"k={self.k_komponen}\nInfo = {persen_terpilih:.2f}%", color='red', fontweight='bold')
        plt.grid(True, linestyle=':', alpha=0.6)
        plt.show()

# =====================================================================
# CARA PENGGUNAAN SKRIP
# =====================================================================
if __name__ == "__main__":
    pengenal = EigenfaceRecognizer(target_size=(64, 64), k_komponen=50)
    folder_dataset = "eigenfaces" 
    
    try:
        # 1. Jalankan training data
        pengenal.latih_model(folder_dataset)
        
        # === PLAY VISUALISASI GRAFIS ===
        pengenal.visualisasikan_eigenfaces(jumlah_tampil=10)
        pengenal.plot_retensi_energi()
        # ===============================
        
        # 2. Jalankan pengujian wajah baru
        foto_test = "img/test_wajah.jpg" 
        if os.path.exists(foto_test):
            nama_hasil, nilai_jarak = pengenal.kenali_wajah_baru(foto_test)
            print("=== HASIL IDENTIFIKASI WAJAH ===")
            print(f"Input Foto       : {foto_test}")
            print(f"Paling Mirip Dengan: {nama_hasil}")
            print(f"Jarak Euclidean  : {nilai_jarak:.4f}")
        else:
            print(f"Sistem siap! Masukkan file foto baru dengan nama '{foto_test}' untuk mencoba deteksi.")
            
    except Exception as e:
        print(f"Terjadi Kesalahan: {e}")
```

## Hasil Output Program

Hasil Kode :
![Hasil Hitung](img/hsil.png)

Hasil Visualisasi Wajah :
![Hasil Hitung](img/hasil10eigenfaces.png)

Hasil ScatterPlot :
![Hasil Hitung](img/hasil_scatterplot.png)
