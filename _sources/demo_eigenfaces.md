# demo EigenFaces tunggal

1. Penambahan Library Visualisasi (matplotlib)Potongan Kode:Pythonimport matplotlib.pyplot as plt  # Library untuk memunculkan gambar
Penjelasan:Pada kode awal Anda, library ini hanya di-import secara lokal di dalam fungsi visualisasi eigenfaces yang tidak tereksekusi dengan benar akibat error dimensi dataset. Dengan meletakkannya di bagian paling atas (global scope), kita bisa menggunakan perintah plt.imshow() dan plt.show() kapan saja untuk mengubah susunan angka di dalam matriks menjadi gambar hitam-putih (grayscale) yang bisa dilihat langsung di layar.2. Pembersihan Struktur Class dan Fokus pada Alur TunggalPenjelasan:Struktur class EigenfaceRecognizer, fungsi kenali_wajah_baru, dan pengkondisian file uji luar (img/test_wajah.jpg) dihapus total.Alasan: Fungsi-fungsi tersebut dirancang untuk cetak biru dataset banyak foto (metode Eigenface). Ketika Anda mengubah matriks A menjadi hanya berisi satu foto, fungsi pencarian jarak dan pengenalan wajah otomatis rusak (crash) karena kekurangan dimensi kolom data untuk dibandingkan. Kode kini disederhanakan murni di dalam blok if __name__ == "__main__":.3. Mempertahankan Matriks 2D Asli $(64 \times 64)$ tanpa FlattenPotongan Kode:Pythonimg = cv2.imread(path, cv2.IMREAD_GRAYSCALE)
img_resized = cv2.resize(img, target_size)
A = img_resized
Penjelasan:Pada teori Eigenface banyak foto, gambar harus di-flatten (diubah menjadi vektor 1D panjang berukuran $4096 \times 1$). Namun, karena tujuan kita sekarang adalah SVD Tunggal pada satu gambar, matriks gambar A harus tetap berbentuk grid 2D berukuran $(64 \times 64)$. SVD akan membedah baris dan kolom dari gambar tunggal ini secara langsung.4. Memperbaiki Urutan Eksekusi SVD (Mengatasi NameError)Potongan Kode:Python# Melakukan dekomposisi SVD murni pada matriks 2D gambar asli (A)
U, S, Vt = np.linalg.svd(A.astype(float), full_matrices=True)
Sigma = np.diag(S)
Penjelasan:Solusi Bug: Di kode lama Anda, terdapat baris self.S = S yang ditulis sebelum fungsi np.linalg.svd(...) dipanggil. Hal ini menyebabkan Python error karena variabel S belum tercipta. Di kode baru, urutannya dibalik: SVD dieksekusi terlebih dahulu, baru nilai S disimpan.Pembentukan Matriks Diagonal ($\Sigma$): Fungsi np.linalg.svd dari numpy secara default hanya mengeluarkan nilai singular berupa array 1D. Baris np.diag(S) bertugas mengubah array 1D tersebut menjadi matriks diagonal 2D berukuran $(64 \times 64)$ agar bisa dikalikan kembali secara matematis.5. Proses Rekonstruksi Gambar Menggunakan Perkalian Matriks MurniPotongan Kode:PythonA_reconstructed = U @ Sigma @ Vt

# Mengembalikan nilai ke format piksel gambar (0-255)
gambar_rekonstruksi = np.clip(A_reconstructed, 0, 255).astype(np.uint8)
Penjelasan:Operator @: Digunakan untuk melakukan perkalian matriks sesuai rumus matematis SVD: $A = U \times \Sigma \times V^T$.np.clip dan astype(np.uint8): Hasil perkalian matriks SVD menghasilkan angka bertipe float (desimal) yang kadang bisa sedikit di bawah 0 atau di atas 255 karena pembulatan komputer. Fungsi np.clip(..., 0, 255) mengunci angka agar tetap berada di rentang piksel valid (0 hingga 255), kemudian .astype(np.uint8) mengubah tipenya kembali menjadi interger/bilangan bulat positif agar OpenCV dan Matplotlib tahu bahwa ini adalah data piksel gambar yang siap dirender.6. Menampilkan Gambar Asli vs Rekonstruksi Secara BerdampinganPotongan Kode:Pythonplt.figure(figsize=(8, 4))
plt.subplot(1, 2, 1)
plt.imshow(A, cmap='gray')
plt.title("Gambar Wajah Asli", fontsize=10)
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(gambar_rekonstruksi, cmap='gray')
plt.title("Gambar Hasil Rekonstruksi SVD", fontsize=10)
plt.axis('off')

plt.show()  # Memunculkan jendela plot ke layar
Penjelasan:Perintah plt.subplot(1, 2, x) membagi jendela visualisasi menjadi 1 baris dan 2 kolom.Indeks 1 digunakan untuk menggambar wajah asli, dan indeks 2 digunakan untuk menggambar wajah hasil perkalian ulang SVD.cmap='gray' wajib dipasang agar warna yang keluar tidak menjadi warna hijau/kuning semu (karena Matplotlib membaca matriks 2D sebagai heatmap secara default jika tidak dipaksa ke mode abu-abu).plt.show() adalah tombol mutlak untuk memerintahkan komputer memunculkan grafik tersebut secara fisik di layar Anda.7. Verifikasi Akhir Dimensi (Poin 7 Tugas Anda)Potongan Kode:Pythonprint(f"Dimensi Matriks Hasil Rekonstruksi: {gambar_rekonstruksi.shape}")
apakah_identik = np.allclose(A.astype(float), A_reconstructed)
print(f"Apakah hasil perkalian kembali identik dengan matriks asli? {apakah_identik}")
Penjelasan:Bagian ini ditambahkan untuk membuktikan secara numerik di terminal bahwa dimensi gambar tidak berubah sedikit pun sesudah didekomposisi, yaitu tetap berukuran $(64 \times 64)$, serta membuktikan lewat fungsi np.allclose bahwa nilai-nilai matematis di dalam matriks hasil rekonstruksi tersebut bernilai sama persis dengan matriks asli sebelum dipecah.