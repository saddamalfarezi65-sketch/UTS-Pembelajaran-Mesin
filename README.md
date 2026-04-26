# UTS-Pembelajaran-Mesin
Berikut adalah penjabaran tahapan-tahapan pembuatan model klasifikasi beserta analisis perbandingan algoritma Decision Tree, Naive Bayes, dan Support Vector Machine (SVM):
1. Tahap Pra-pemrosesan Data (Data Preprocessing)

Ingesti Data: Memuat dataset observasi metrik fisik buah sitrus (citrus.csv) ke dalam lingkungan komputasi memori.

Transformasi Variabel (Label Encoding): Mengonversi variabel target kategorikal (kelas 'orange' dan 'grapefruit') menjadi nilai numerik biner komputasional (misalnya 0 dan 1). Hal ini merupakan prasyarat mutlak agar data dapat diproses oleh algoritma matematis.

Penyekatan Data (Train-Test Split): Memisahkan populasi dataset menjadi dua himpunan data yang saling lepas (secara mutual eksklusif). Himpunan pertama difungsikan sebagai data latih (training set) untuk mengonstruksi model, sedangkan himpunan kedua diisolasi sebagai data uji (testing set) untuk keperluan validasi prediksi secara objektif (umumnya menggunakan rasio 80:20).

Standardisasi Fitur (Feature Scaling): Menyeragamkan rentang amplitudo seluruh variabel independen ke dalam skala yang ekuivalen menggunakan metode normalisasi Z-score (StandardScaler). Prosedur ini sangat esensial bagi algoritma SVM yang kalkulasinya amat bergantung pada perhitungan metrik jarak ruang geometris. Meskipun model Decision Tree dan Naive Bayes bersifat tahan terhadap disparitas skala (scale-invariant), standardisasi tetap diaplikasikan agar perbandingan performa (benchmarking) dapat dieksekusi secara berimbang pada struktur matriks data yang seragam.

2. Tahap Inisialisasi dan Pelatihan Model (Model Training)

Decision Tree (Pohon Keputusan): Melakukan inisialisasi objek model DecisionTreeClassifier. Algoritma dilatih untuk mempartisi ruang data berdasarkan fitur secara top-down. Pada tahap ini, penyetelan hyperparameter seperti pembatasan kedalaman maksimal pohon (max_depth) harus diterapkan secara ketat guna memitigasi risiko overfitting atau bias penghafalan pada data latih.

Naive Bayes: Mengimplementasikan varian GaussianNB (Gaussian Naive Bayes), yang dirancang secara khusus untuk distribusi nilai fitur kontinu. Model ini dilatih melalui kalkulasi probabilitas bersyarat dengan landasan Teorema Bayes. Proses komputasinya berlangsung sangat efisien berdasarkan asumsi teoretis bahwa seluruh fitur input saling berdiri bebas (independen).

Support Vector Machine (SVM): Membangun arsitektur batas klasifikasi menggunakan objek SVC. Mengingat dimensi ukuran antara kedua jenis sitrus kerap menunjukkan tumpang-tindih (zona ambiguitas), model ini diaplikasikan bersamaan dengan Trik Kernel, seperti Radial Basis Function (RBF), guna mengeksekusi pemisahan kelas secara non-linier di ruang berdimensi tinggi. Pemanfaatan metode penelusuran seperti Grid Search sangat direkomendasikan untuk melakukan optimasi hyperparameter (parameter Cost dan varians Gamma) guna mencapai performa hyperplane yang puncak.

3. Tahap Pengujian Prediksi (Model Testing)

Menginstruksikan ketiga arsitektur model yang telah rampung melalui fase pelatihan untuk melakukan proyeksi klasifikasi pada data uji (testing set). Pada proses ini, nilai target aktual disembunyikan dari model untuk mengukur validitas prediksinya secara riil.

4. Tahap Evaluasi dan Sintesis Perbandingan (Evaluation & Benchmarking)

Kalkulasi Metrik Evaluasi: Menyandingkan hasil prediksi komputasi dari masing-masing algoritma terhadap label aslinya menggunakan landasan Confusion Matrix. Ekstraksi dari matriks tersebut akan menghasilkan parameter kuantitatif yang meliputi Akurasi (Accuracy), Presisi (Precision), Sensitivitas (Recall), dan Nilai Rata-rata Harmonik (F1-Score).

Sintesis Perbandingan Kinerja:

SVM secara empiris mendemonstrasikan tingkat probabilitas akurasi yang paling unggul dalam menyelesaikan klasifikasi dengan margin data yang kompleks dan tumpang-tindih. Namun, keunggulan performa metrik ini menuntut kompensasi berupa beban komputasi (computational cost) dan durasi pelatihan yang jauh lebih lama.

Naive Bayes menawarkan kecepatan eksekusi yang amat tinggi (supersonik), yang membuatnya ideal untuk operasi pemrosesan yang masif. Walau demikian, akurasinya kerap mengalami depresiasi saat berhadapan dengan data yang memiliki kolinearitas inter-fitur tinggi (seperti korelasi absolut antara diameter dan massa buah sitrus) akibat kelemahan asumsi independensinya.

Decision Tree menghadirkan nilai akurasi komparatif yang proporsional dengan satu superioritas absolut: transparansi logis (Highly Interpretable). Mekanisme model ini dapat diekstraksi menjadi hierarki logis "If-Else" yang amat jelas dan dapat dirasionalisasikan secara langsung oleh kemampuan kognitif manusia tanpa memerlukan interpretasi kotak hitam (black-box).
