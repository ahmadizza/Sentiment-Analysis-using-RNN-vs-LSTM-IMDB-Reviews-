# Sentiment-Analysis-using-RNN-vs-LSTM-IMDB-Reviews-

# 🎬 Sentiment Analysis with RNN vs LSTM (IMDB Movie Reviews)  

## 📌 Deskripsi Proyek  
Analisis sentimen adalah tugas klasifikasi teks untuk menentukan polaritas (positif/negatif).  
Proyek ini membandingkan **Recurrent Neural Network (RNN)** dan **Long Short-Term Memory (LSTM)** pada dataset **50.000 review film IMDB**.  

RNN cocok untuk data sekuensial seperti teks, namun sering bermasalah dengan **long-term dependencies** akibat *vanishing gradient*.  
LSTM, sebagai varian RNN, dirancang untuk mengatasi masalah tersebut dengan **cell state** dan **gates**.  

---

## 🎯 Tujuan  
- Membandingkan performa RNN dan LSTM dalam memprediksi sentimen review film IMDB.  
- Menganalisis fenomena *vanishing gradient* pada kedua model saat training.  
- Mengevaluasi kemampuan kedua model dalam menangani *long-term dependencies*.  

---

## 📂 Dataset  
- Sumber: [IMDB Movie Reviews](https://ai.stanford.edu/~amaas/data/sentiment/)  
- Total: **50.000 review** berlabel (positif/negatif)  
- Split data:  
  - 80% training (39.665 data)  
  - 10% validation (4.959 data)  
  - 10% testing (4.958 data)  
- Karakteristik: review panjang, kompleks, mengandung kata tidak baku & simbol HTML.  

---

## 🔎 Metodologi  
1. **Preprocessing**: lowercase, hapus HTML tags, tanda baca, angka, stopwords → tokenisasi → padding (max length = 256).  
2. **Encoding Sentiment**: 1 = positif, 0 = negatif.  
3. **Pemodelan**:  
   - `nn.Embedding` → mengubah kata jadi vektor berdimensi 64.  
   - `nn.RNN` / `nn.LSTM` → lapisan inti (bidirectional).  
   - `nn.Linear` + `nn.Sigmoid` → klasifikasi akhir (0/1).  
   - Dropout: 0.2, Hidden Dimension: 32.  
4. **Evaluasi**: Accuracy, Precision, Recall, Loss Curve, Gradient Analysis.  

---

## 📊 Hasil  

### Akurasi  
- **RNN**: Training 94%, Validation stagnan < 82% (overfitting).  
- **LSTM**: Training 98%, Validation stabil hingga 87% (lebih baik).  

### Loss  
- RNN: loss menurun tapi cepat overfit setelah epoch 8–9.  
- LSTM: loss menurun tajam dan konsisten, overfit lebih lambat (~epoch 13).  

### Gradient  
- RNN: gradien tidak stabil → vanishing & exploding gradient.  
- LSTM: gradien stabil → lebih konsisten belajar.  

### Evaluasi Test Data  
- LSTM outperform RNN di hampir semua metrik evaluasi.  
- LSTM lebih baik dalam menjaga **long-term dependencies**, terutama pada review panjang (>400 kata).  

---

## 💡 Insight & Kesimpulan  
- **RNN** rentan overfitting, kesulitan menangani review panjang.  
- **LSTM** terbukti lebih andal, stabil, dan seimbang antara precision & recall.  
- LSTM mengatasi masalah *vanishing gradient* sehingga unggul untuk analisis teks panjang.  
- Secara keseluruhan, **LSTM lebih superior dibandingkan RNN untuk sentiment analysis pada dataset IMDB**.  

---

## 👨‍💻 Tim  
**Kelompok 5 – UAS NLP 2025**  
- Ahmad Izza (11220940000006)  
- Dani Hidayat (11220940000014)  

---

## 📜 Lisensi  
Proyek ini dibuat untuk tujuan akademik (**UAS NLP**) dan dapat digunakan untuk pembelajaran.  
