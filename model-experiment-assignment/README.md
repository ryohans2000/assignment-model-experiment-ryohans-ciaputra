## Objective
 Mengklasifikasikan ulasan pelanggan e-commerce secara otomatis ke dalam kategori sentimen (positif atau negatif) untuk analisa kepuasan produk secara cepat dan akurat.

## Dataset
Total memiliki 200 baris ulasan berbahasa Indonesia yang terdiri dari 110 ulasan positif dan 90 ulasan negatif.

## Ringkasan eksperimen kedua pendekatan.
- ML (Scikit-Learn)
    Metode: Feature extraction menggunakan TF-IDF Vectorizer dilanjutkan model klasifikasi linear Logistic Regression.

- LLM API (Gemini)
    Metode: Zero-shot prompting menggunakan model Gemini 3.5 Flash Lite 

## Tabel hasil evaluasi dan perbandingan.
Kesimpulan :
Kedua metode tersebut memprediksi 40 sample data tanpa ada kesalahan

=== Model Klasik (Scikit-learn) ===
Accuracy: 1.0
              precision    recall  f1-score   support

     negatif       1.00      1.00      1.00        18
     positif       1.00      1.00      1.00        22

    accuracy                           1.00        40
   macro avg       1.00      1.00      1.00        40
weighted avg       1.00      1.00      1.00        40

Confusion Matrix:
 [[18  0]
 [ 0 22]]

 === LLM API (Gemini) ===
Accuracy: 1.0
              precision    recall  f1-score   support

     negatif       1.00      1.00      1.00        18
     positif       1.00      1.00      1.00        22

    accuracy                           1.00        40
   macro avg       1.00      1.00      1.00        40
weighted avg       1.00      1.00      1.00        40

Confusion Matrix:
 [[18  0]
 [ 0 22]]

## Analisis trade-off dan limitation.
| Aspek | TF-IDF + Logistic Regression | LLM API (Gemini) |
|---|---|---|
| Performa | Efektif untuk klasifikasi sentimen berdasarkan pola dan frekuensi kata dalam data training. | Mampu memahami konteks bahasa dan makna kalimat melalui model bahasa yang telah dilatih. |
| Effort (Usaha) | Membutuhkan preprocessing, ekstraksi fitur TF-IDF, training, dan evaluasi model. | Tidak memerlukan training model sendiri, tetapi membutuhkan penyusunan prompt dan integrasi API. |
| Kecepatan | Prediksi relatif cepat setelah model selesai dilatih. | Bergantung pada koneksi internet dan waktu respons API. |
| Biaya | Relatif rendah karena dapat dijalankan secara lokal tanpa biaya API per prediksi. | Berpotensi menimbulkan biaya berdasarkan penggunaan token dan API. |
| Konsistensi | Hasil prediksi cenderung konsisten selama model dan preprocessing tidak berubah. | Hasil dapat dipengaruhi oleh prompt, konfigurasi, dan versi model. |

| Metode | Limitation |
|---|---|
| TF-IDF + Logistic Regression | Tidak sepenuhnya memahami konteks dan makna kalimat. |
| TF-IDF + Logistic Regression | Sangat bergantung pada kualitas dan representasi data training. |
| LLM API (Gemini) | Membutuhkan koneksi internet dan ketersediaan layanan API. |
| LLM API (Gemini) | Memiliki potensi biaya penggunaan API. |

## Rekomendasi technical approach beserta alasannya.
Rekomendasi : ML (TF-IDF + Logistic Regression)
Alasan :
- Biaya & Kecepatan: Memberikan akurasi data yang tinggi dengan biaya operasional rendah tanpa latensi internet.
- Diproses secara lokal: Dapat di-deploy secara lokal tanpa membocorkan data ke pihak ketiga

## Cara menjalankan notebook/script.
- Buka VS Code 
- Pastikan library yang diperlukan sudah terinstall (sesuai dengan yang tertera requirement.txt)
- Buat file .env di folder root dan masukkan API key pribadi dengan cara
  'GEMINI_API_KEY=your_actual_gemini_api_key_here'
- Jalankan Virtual Enviroment
- Jalankan program dengan 'Run All'



