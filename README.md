# KLASIFIKASI-GAMBAR

# Intel Image Classification - CNN

Proyek ini merupakan implementasi **CNN** untuk melakukan klasifikasi gambar berdasarkan dataset **Intel Image Classification** dari Kaggle. Proyek ini melibatkan beberapa tahapan mulai dari pengunduhan dataset, preprocessing, training model, evaluasi, hingga konversi model ke berbagai format (TFLite dan TensorFlow.js).

---

## 📂 Dataset

- Dataset: [Intel Image Classification](https://www.kaggle.com/datasets/puneet6060/intel-image-classification)
- Jumlah kelas: 6 (Buildings, Forest, Glacier, Mountain, Sea, Street)
- Format gambar: RGB, resolusi 150x150 piksel
- Dataset telah dibagi menjadi tiga bagian:
  - `train` (11.000+ gambar)
  - `test` (1.000+ gambar)
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
- Menggunakan arsitektur CNN pre-trained pada ImageNet sebagai feature extractor.
- Bagian atas model (top classifier) ditambahkan layer `GlobalAveragePooling2D`, `Dropout`, dan `Dense`.
- Base model dibekukan pada awalnya, lalu dilanjutkan dengan **fine-tuning** pada beberapa lapisan akhir.


### 4. Training dengan Early Stopping
- Model akan **dihentikan secara otomatis** jika akurasi validasi < 85% dalam beberapa epoch pertama, untuk menghemat waktu dan sumber daya.
- Model terbaik disimpan otomatis.

### 5. Evaluasi & Visualisasi
- Menampilkan **akurasi dan loss** untuk training dan validation.
- Confusion matrix, classification report, dan contoh prediksi visual ditampilkan.

### 6. Model Conversion
- Model disimpan dalam format:
  - `SavedModel` (untuk deploy ke server)
  - `.tflite` (untuk deploy ke mobile)
  - `TensorFlow.js` (untuk deploy ke web)
- Semua file akhir dikompres ke `models.zip` untuk kemudahan distribusi.

---

## ✅ Hasil dan Kesimpulan

- Model berhasil mencapai akurasi **87%**.
- Proses pelatihan dilakukan dengan mekanisme **early stopping**, sehingga efisien secara waktu dan komputasi.
- Model telah dikonversi ke berbagai format untuk keperluan **multi-platform deployment** (mobile, web, server).

---

## 🚀 Cara Menjalankan Proyek

1. Clone repo ini:
   ```bash
   git clone https://github.com/Margohan23/KLASIFIKASI-GAMBAR.git
   cd KLASIFIKASI-GAMBAR
