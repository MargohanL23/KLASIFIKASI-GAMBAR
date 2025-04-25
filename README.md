# KLASIFIKASI-GAMBAR

# Intel Image Classification - CNN Based Image Classifier

Proyek ini merupakan implementasi **Convolutional Neural Network (CNN)** untuk melakukan klasifikasi gambar berdasarkan dataset **Intel Image Classification** dari Kaggle. Proyek ini melibatkan beberapa tahapan mulai dari pengunduhan dataset, preprocessing, training model, evaluasi, hingga konversi model ke berbagai format (TFLite dan TensorFlow.js).

---

## 📂 Dataset

- Dataset: [Intel Image Classification](https://www.kaggle.com/datasets/puneet6060/intel-image-classification)
- Jumlah kelas: 6 (Buildings, Forest, Glacier, Mountain, Sea, Street)
- Format gambar: RGB, resolusi 150x150 piksel
- Dataset telah dibagi menjadi tiga bagian:
  - `train` (14.000+ gambar)
  - `test` (3.000+ gambar)
  - `val` (1.000+ gambar)

---

## 🔧 Langkah-Langkah Membangun Model

### 1. Library dan Dataset Preparation
- Mengimpor library seperti TensorFlow, NumPy, PIL, Matplotlib, dan lainnya.
- Dataset diunduh menggunakan `kagglehub` dan dipersiapkan dalam struktur direktori yang sesuai.

### 2. Data Preprocessing
- Menggunakan `image_dataset_from_directory` untuk membuat dataset terstruktur.
- Pembagian data: training (80%), validation (10%), test (10%)
- Menerapkan **data augmentation**: rotasi, flip horizontal/vertikal, zoom, dan lainnya.

### 3. Pembuatan Model CNN
- Arsitektur model terdiri dari beberapa layer: `Conv2D`, `MaxPooling2D`, `BatchNormalization`, `Dropout`, dan `Dense`.
- Optimizer: `Adam`
- Loss Function: `SparseCategoricalCrossentropy`

### 4. Training dengan Early Stopping
- Model akan **dihentikan secara otomatis** jika akurasi validasi < 85% dalam beberapa epoch pertama, untuk menghemat waktu dan sumber daya.
- Model terbaik disimpan otomatis.

### 5. Fine-Tuning
- Dilakukan untuk mencapai target akurasi > 90%
- Teknik yang digunakan: penyesuaian learning rate, penambahan regularisasi, dan penambahan data augmentation.

### 6. Evaluasi & Visualisasi
- Menampilkan **akurasi dan loss** untuk training dan validation.
- Confusion matrix, classification report, dan contoh prediksi visual ditampilkan.

### 7. Model Conversion
- Model disimpan dalam format:
  - `SavedModel` (untuk deploy ke server)
  - `.tflite` (untuk deploy ke mobile)
  - `TensorFlow.js` (untuk deploy ke web)
- Semua file akhir dikompres ke `models.zip` untuk kemudahan distribusi.

---

## ✅ Hasil dan Kesimpulan

- Model berhasil mencapai akurasi **87%**, dan setelah fine-tuning berhasil menembus **>90% akurasi pada data validasi dan testing**.
- Proses pelatihan dilakukan dengan mekanisme **early stopping**, sehingga efisien secara waktu dan komputasi.
- Model telah dikonversi ke berbagai format untuk keperluan **multi-platform deployment** (mobile, web, server).
- Proyek ini menunjukkan bahwa **CNN sederhana dengan augmentasi data yang baik** dapat memberikan hasil yang akurat pada klasifikasi gambar skala menengah.

---

## 🚀 Cara Menjalankan Proyek

1. Clone repo ini:
   ```bash
   git clone https://github.com/Margohan23/KLASIFIKASI-GAMBAR.git
   cd KLASIFIKASI-GAMBAR
