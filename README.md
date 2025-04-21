# Laporan Proyek Machine Learning - Aditiya Saputra ( Recomendation System)

## Project Overview
Proyek ini bertujuan untuk mengembangkan sebuah sistem rekomendasi anime yang mampu memberikan saran personal kepada pengguna berdasarkan preferensi dan interaksi mereka terhadap berbagai judul anime. Dengan memanfaatkan data pengguna dan rating terhadap anime, sistem ini dibangun menggunakan teknik Collaborative Filtering berbasis model neural network, khususnya pendekatan Neural Collaborative Filtering (NCF).

Sistem rekomendasi ini dirancang untuk meningkatkan pengalaman pengguna dengan mempermudah penemuan anime baru yang sesuai dengan minat mereka. Hal ini penting karena banyak pengguna kesulitan menemukan anime yang relevan dari ribuan pilihan yang tersedia. Dengan memberikan rekomendasi yang akurat dan personal, sistem ini diharapkan mampu meningkatkan engagement pengguna di platform streaming anime.

Model yang dibangun memanfaatkan informasi rating yang diberikan oleh pengguna terhadap anime tertentu. Dengan pendekatan ini, sistem dapat mempelajari pola preferensi dan memberikan prediksi terhadap anime lain yang mungkin disukai pengguna tersebut. Pendekatan ini juga dapat dikembangkan untuk platform lain seperti film, musik, atau e-commerce.
  
Referensi: [[Analyzing the effectiveness of collaborative filtering and content-based filtering methods in anime recommendation systemsi]](http://repository.uin-malang.ac.id/17878/) 

## Business Understanding

Pada bagian ini, Anda perlu menjelaskan proses klarifikasi masalah.

Bagian laporan ini mencakup:

### Problem Statements
* Bagaimana memberikan rekomendasi anime yang sesuai dengan preferensi pengguna berdasarkan histori penilaian anime?
* Apakah metode collaborative filtering mampu mengidentifikasi kesamaan antar pengguna dan memberikan saran anime yang relevan?
* Bagaimana akurasi sistem rekomendasi yang dibangun dalam menyarankan anime yang disukai pengguna?
### Goals

* Membangun sistem rekomendasi anime berbasis collaborative filtering.
* Menggunakan data rating pengguna terhadap anime untuk menemukan pola kesukaan yang serupa antar pengguna.
* Mengevaluasi performa sistem rekomendasi dengan metrik akurasi rekomendasi seperti RMSE, MSE dan MAE.



Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Approach” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Mengajukan 2 atau lebih solution approach (algoritma atau pendekatan sistem rekomendasi).

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
