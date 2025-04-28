# Laporan Proyek Machine Learning - Aditiya Saputra ( Recomendation System)

## Project Overview
Proyek ini bertujuan untuk mengembangkan sebuah sistem rekomendasi anime yang mampu memberikan saran personal kepada pengguna berdasarkan preferensi dan interaksi mereka terhadap berbagai judul anime. Dengan memanfaatkan data pengguna dan rating terhadap anime, sistem ini dibangun menggunakan teknik Collaborative Filtering berbasis model neural network, khususnya pendekatan Neural Collaborative Filtering (NCF).

Sistem rekomendasi ini dirancang untuk meningkatkan pengalaman pengguna dengan mempermudah penemuan anime baru yang sesuai dengan minat mereka. Hal ini penting karena banyak pengguna kesulitan menemukan anime yang relevan dari ribuan pilihan yang tersedia. Dengan memberikan rekomendasi yang akurat dan personal, sistem ini diharapkan mampu meningkatkan engagement pengguna di platform streaming anime.

Model yang dibangun memanfaatkan informasi rating yang diberikan oleh pengguna terhadap anime tertentu. Dengan pendekatan ini, sistem dapat mempelajari pola preferensi dan memberikan prediksi terhadap anime lain yang mungkin disukai pengguna tersebut. Pendekatan ini juga dapat dikembangkan untuk platform lain seperti film, musik, atau e-commerce.
  
Referensi: [[Putri, Helmy Dianti, and Muhammad Faisal. "Analyzing the effectiveness of collaborative filtering and content-based filtering methods in anime recommendation systems." Jurnal Komtika (Komputasi dan Informatika) 7.2 (2023): 124-133.]](http://repository.uin-malang.ac.id/17878/) 

## Business Understanding
Dalam era digital saat ini, meningkatnya minat terhadap anime dan pertumbuhan pesat platform streaming menciptakan tantangan dalam membantu pengguna menemukan konten yang sesuai dengan preferensi mereka. Banyaknya pilihan membuat pengguna kewalahan dan berpotensi meninggalkan platform jika tidak menemukan tontonan yang menarik. Untuk menjawab tantangan tersebut, proyek ini bertujuan membangun sistem rekomendasi anime berbasis collaborative filtering guna meningkatkan pengalaman pengguna, memperpanjang waktu konsumsi konten, serta mendorong loyalitas pengguna terhadap platform. Dengan memahami pola penilaian dan kesamaan selera antar pengguna, sistem ini diharapkan mampu memberikan rekomendasi anime yang lebih personal, relevan, dan memuaskan.
### Problem Statements
* Bagaimana memberikan rekomendasi anime yang sesuai dengan preferensi pengguna berdasarkan histori penilaian anime?
* Apakah metode collaborative filtering mampu mengidentifikasi kesamaan antar pengguna dan memberikan saran anime yang relevan?
* Bagaimana akurasi sistem rekomendasi yang dibangun dalam menyarankan anime yang disukai pengguna?
### Goals
* Membangun sistem rekomendasi anime berbasis collaborative filtering.
* Menggunakan data rating pengguna terhadap anime untuk menemukan pola kesukaan yang serupa antar pengguna.
* Mengevaluasi performa sistem rekomendasi dengan metrik akurasi rekomendasi seperti RMSE, MSE dan MAE.

 ### Solution statements
* Data Preparation: Mengambil dataset anime review dari Kaggle, melakukan pembersihan data (menghapus rating kosong atau tidak valid), normalisasi rating, dan encoding kolom categorical (Username dan Anime Title) menjadi ID numerik untuk memudahkan pemodelan.
* Model Building: Membangun model Neural Collaborative Filtering menggunakan embedding layers untuk pengguna dan anime, menghitung kecocokan menggunakan dot product, dan memproses hasil dengan fungsi aktivasi sigmoid. Regularisasi L2 digunakan untuk menghindari overfitting.
* Model Training & Evaluation: Melatih model menggunakan MSE sebagai fungsi kerugian dengan EarlyStopping untuk mencegah overfitting, dan mengevaluasi model menggunakan metrik MAE, MSE, dan RMSE untuk memastikan akurasi prediksi rating.
* Recommender System: Menggunakan model untuk memprediksi rating yang belum diberikan oleh pengguna terhadap anime, dan memberikan rekomendasi 10 anime dengan rating tertinggi berdasarkan preferensi pengguna.

## Data Understanding
Sumber Data: Dataset yang digunakan diperoleh dari platform Kaggle, dengan dataset berjudul ["Top 10K Anime Details"](https://www.kaggle.com/datasets/stoicstatic/mal-top-10k-anime-details), yang berisi data tentang anime beserta ulasan yang diberikan oleh pengguna. Dataset ini mencakup 85,953 baris data yang berisi informasi tentang anime, termasuk rating yang diberikan oleh pengguna pada berbagai aspek anime.

Struktur Dataset: Dataset ini memiliki 14 kolom dengan berbagai informasi mengenai anime dan ulasan pengguna. Berikut adalah penjelasan mengenai setiap kolom:

![Tabel](https://github.com/Ayasa18/Recomendation-System/blob/f53284fdce80ee63b8c30cdc8947ca6996492fbc/Asset/KolomData.png?raw=true)


| **Kolom**             | **Tipe Data** | **Deskripsi**                                                           |
|-----------------------|---------------|-------------------------------------------------------------------------|
| `Anime Rank`          | int64         | Peringkat anime berdasarkan popularitas di platform                      |
| `Anime Title`         | object        | Judul anime                                                            |
| `Anime URL`           | object        | URL untuk informasi lebih lanjut tentang anime                          |
| `Username`            | object        | Nama pengguna yang memberikan rating                                    |
| `Review Date`         | object        | Tanggal ulasan diberikan oleh pengguna                                  |
| `Episodes Watched`    | object        | Jumlah episode yang sudah ditonton oleh pengguna                        |
| `Review Likes`        | int64         | Jumlah suka yang diterima pada ulasan                                  |
| `Overall Rating`      | int64         | Rating keseluruhan yang diberikan oleh pengguna                         |
| `Story Rating`        | int64         | Rating khusus untuk cerita anime                                        |
| `Animation Rating`    | int64         | Rating khusus untuk animasi anime                                       |
| `Sound Rating`        | int64         | Rating khusus untuk kualitas suara anime                                |
| `Character Rating`    | int64         | Rating khusus untuk karakter anime                                      |
| `Enjoyment Rating`    | int64         | Rating berdasarkan tingkat kesenangan yang dirasakan pengguna saat menonton anime |
| `Review`              | object        | Teks ulasan yang diberikan oleh pengguna                                |

### Exploratory Data Analysis
#### Top 10 Anime yang di Nilai Atau Di Review
  Tujuan dari analisis ini adalah untuk mengetahui anime yang mendapat perhatian atau popularitas tertinggi berdasarkan seberapa sering anime tersebut dinilai atau direview. Hal ini membantu untuk mengidentifikasi anime yang sedang tren atau menarik bagi banyak orang, serta memberikan wawasan mengenai preferensi atau minat pengguna dalam kategori anime tertentu. Pada visualisasi dibawah sekitar 10 anime teratas mendapat penilaian sebanyak 80 review atau penilaian
      
![10Anime](https://github.com/Ayasa18/Recomendation-System/blob/63026845010c340fb1abd6609dc32b81cc0745ff/Asset/KolomData.png?raw=true)

#### Distribusi Overall Rating
  Untuk memvisualisasikan sebaran atau distribusi rating keseluruhan yang diberikan oleh pengguna pada anime dalam dataset. Dengan mengetahui distribusi rating, kita bisa memahami bagaimana pengguna memberikan penilaian terhadap anime secara umum, apakah kebanyakan rating cenderung tinggi, rendah, atau tersebar merata di berbagai kategori rating. Ini membantu untuk mengidentifikasi tren umum dalam penilaian pengguna terhadap anime dan juga dapat menunjukkan bias atau ketidakseimbangan dalam pemberian rating.Berdasarkan diagram dibawah, nilai rating yang paling umum diberikan oleh user yaitu 8, dan yang paling rendah 1

![Rating](https://github.com/Ayasa18/Recomendation-System/blob/63026845010c340fb1abd6609dc32b81cc0745ff/Asset/Top10Anime.png?raw=true)

#### Korelasi Antar Rating
  Untuk menganalisis hubungan antara berbagai kategori rating yang diberikan oleh pengguna, seperti Story Rating, Animation Rating, Sound Rating, Character Rating, dan Enjoyment Rating. Dengan mengetahui korelasi antar rating, kita dapat memahami apakah pengguna yang memberikan rating tinggi pada satu aspek anime (misalnya cerita) juga cenderung memberikan rating tinggi pada aspek lainnya (seperti animasi atau karakter). Hal ini membantu untuk mengidentifikasi pola atau hubungan yang mungkin ada antara kualitas berbagai elemen anime dalam persepsi pengguna.

 ![Korelasi](https://github.com/Ayasa18/Recomendation-System/blob/a9187ba190e6dc05f1e7999834eaf404fc0bdfa8/Asset/KorelasiantarRating.png?raw=true)
 
  Matriks korelasi rating aspek menunjukkan hubungan antar kategori seperti Overall, Story, Animation, Sound, Character, dan Enjoyment. Nilai korelasi tertinggi (1.00) terlihat pada hubungan masing-masing kategori dengan dirinya sendiri, yang diharapkan. Korelasi tertinggi antar kategori berbeda ada antara Story dan Overall (0.73), Character dan Overall (0.73), serta Character dan Enjoyment (0.86), menunjukkan bahwa aspek cerita dan karakter memiliki pengaruh kuat terhadap rating keseluruhan dan kepuasan. Sebaliknya, korelasi terendah terlihat antara Animation dan Overall (0.48) serta Sound dan Overall (0.52), mengindikasikan bahwa animasi dan suara memiliki pengaruh lebih kecil terhadap rating keseluruhan. Secara umum, aspek Story, Character, dan Enjoyment saling berkorelasi cukup kuat (0.84-0.86), sementara Animation dan Sound cenderung memiliki korelasi lebih rendah dengan aspek lainnya (0.48-0.81).

#### Jumlah Review Per Tahun
   Untuk menganalisis tren atau pola jumlah ulasan yang diberikan oleh pengguna setiap tahunnya. Dengan mengetahui jumlah review yang diberikan per tahun, kita dapat melihat apakah ada peningkatan atau penurunan aktivitas pengguna dalam memberikan ulasan seiring waktu. Hal ini juga bisa memberikan insight tentang popularitas anime pada periode tertentu, serta memberikan gambaran tentang kecenderungan pengguna dalam memberikan feedback sepanjang waktu. Pada visualisasai dibawah review di mulai dari tahun 2007 dan review tertinggi atau terbanyak di berikan pada tahun 2020

![Review](https://github.com/Ayasa18/Recomendation-System/blob/a9187ba190e6dc05f1e7999834eaf404fc0bdfa8/Asset/JumlahReviewTahun.png?raw=true)

## Data Preparation
Pada tahap ini kita akan melakukan proses transformasi pada data sehingga menjadi bentuk yang cocok untuk proses pemodelan. Ada beberapa tahap persiapan data perlu dilakukan, yaitu:
 1. Memeriksa Struktur dan Informasi Dataset, pengecekan jumlah kolom, tipe data, dan missing values.
    
    Melihat jumlah baris, kolom, tipe data, dan mengecek apakah terdapat data yang kosong atau hilang.
    
![infodata](https://github.com/Ayasa18/Recomendation-System/blob/25e7d3cb4f068fdc3938bf42e672e47219a9fd5a/Asset/null.png?raw=true)
    
 2. Memfilter Data Berdasarkan Rating
    
    Memilih hanya data dengan rating tertentu untuk menjaga kualitas input bagi model rekomendasi.
    
![Filter](https://github.com/Ayasa18/Recomendation-System/blob/7af86543835da62029c05ebed171bbef42167515/Asset/FilterRating.png?raw=true)

   Memilih hanya data dengan rating tertentu untuk menjaga kualitas input bagi model rekomendasi.
   
 3. Memilih dan Merename Kolom
    
    Mengambil kolom yang relevan seperti user, anime title, dan rating, lalu mengganti nama kolom agar lebih konsisten.
    
![rename](https://github.com/Ayasa18/Recomendation-System/blob/7af86543835da62029c05ebed171bbef42167515/Asset/MemilihdanRenameKolom.png?raw=true)

 4. Normalisasi Rating
    
    Melakukan transformasi rating ke dalam skala yang seragam agar model dapat belajar secara optimal.
    
![Normalisasi](https://github.com/Ayasa18/Recomendation-System/blob/7af86543835da62029c05ebed171bbef42167515/Asset/NormalisasiRating.png?raw=true)

 5. Encode Username dan Anime Title ke bentuk angka
    
    Mengubah data kategorikal seperti nama pengguna dan judul anime menjadi representasi numerik menggunakan label encoding.

![encode](https://github.com/Ayasa18/Recomendation-System/blob/7af86543835da62029c05ebed171bbef42167515/Asset/SetelahNormalisasiEncode.png?raw=true?raw=true)

 6. Split Dataset dengan Ratio 80:20
    
    Membagi data menjadi 80% data latih dan 20% data uji untuk mengevaluasi performa model.
    
![split](https://github.com/Ayasa18/Recomendation-System/blob/7af86543835da62029c05ebed171bbef42167515/Asset/SplitDataset.png?raw=true)

## Modeling
Model ini merupakan pendekatan deep learning dalam sistem rekomendasi, yang mempelajari interaksi antara pengguna dan item (anime) melalui embedding layers dan teknik pembelajaran non-linear.

 1. Inisialisasi Model
    Model didefinisikan melalui subclassing dari tf.keras.Model dengan nama AnimeRecommender.
        * User Embedding dan Anime Embedding: Masing-masing pengguna dan anime diubah menjadi vektor berdimensi embedding_size (misalnya 50). Layer ini belajar merepresentasikan fitur laten dari pengguna dan anime.
        * Bias: Selain vektor embedding, masing-masing pengguna dan anime juga memiliki bias scalar untuk menyesuaikan prediksi lebih akurat.
        * Regularisasi: l2 regularization digunakan untuk mencegah overfitting.
        * Dot Product: Interaksi antara pengguna dan anime dimodelkan sebagai dot product antara embedding mereka, ditambahkan dengan bias masing-masing.
        * Aktivasi: Output dari model diproses dengan fungsi aktivasi sigmoid untuk menjaga nilai prediksi berada di rentang [0, 1].
2. Kompilasi Model
   Model dikompilasi dengan konfigurasi sebagai berikut:
        * Loss Function: Menggunakan MeanSquaredError, cocok untuk regresi prediksi rating.
        * Optimizer: Menggunakan Adam, optimasi berbasis adaptif yang sangat baik untuk deep learning.
        * Metrics:
        - MeanAbsoluteError (MAE): Mengukur rata-rata selisih absolut antara prediksi dan nilai asli.
        - RootMeanSquaredError (RMSE): Mengukur deviasi prediksi dari nilai sebenarnya, lebih sensitif terhadap error besar.
3. Callback - Early Stopping
   
   Menggunakan EarlyStopping untuk menghentikan pelatihan jika tidak ada peningkatan val_loss selama 5 epoch, dengan restore_best_weights=True untuk mengembalikan bobot model terbaik.

4. Pelatihan Model
    Model dilatih menggunakan fungsi .fit() dengan parameter:
          * Data: x_train dan y_train untuk training, x_val dan y_val untuk validasi.
          * Epochs: Maksimal 50 iterasi pelatihan.
          * Batch Size: Menggunakan 256 sampel per batch.
          * Shuffle: Data diacak tiap epoch untuk membantu generalisasi.
          * Verbose: Menampilkan progress pelatihan.
          * Callbacks: Menggunakan EarlyStopping untuk efisiensi pelatihan.
   
### Uji Rekomendasi Model Yang Telah dibuat (Result)
  1. Prediksi Rating dari Pasangan User-Anime
     Pertama kita mencoba untuk mendapatkan Rekomendasi, hal pertama adalah saya mencari anime_id untuk Gintama°(Untuk menyesuaikan Prediksi)

![Uji](https://github.com/Ayasa18/Recomendation-System/blob/33ec79497c1e54991a4c4c5781630925caaa9df4/Asset/MencariID.png?raw=true)
      Lalu untuk mengetahui Prediksi Rating untuk Satu Pasangan User–Anime
      Misalnya  ingin tahu Gintama yang telahh kita dapatkan anime_id nya:
      "Kalau user dengan ID 10 (setelah encoding) menonton anime dengan ID 1196, berapa rating yang kemungkinan akan dia berikan?"

 ![uji](https://github.com/Ayasa18/Recomendation-System/blob/bf22b83833639897832dbf699de72cb6702a4f3b/Asset/PrediksiRating.png?raw=true)

  2. Menemukan 10 anime terbaik yang direkomendasikan oleh model untuk 1 user tertentu.
     
     Dengan kata lain, model memprediksi semua anime mana saja yang kemungkinan besar akan disukai oleh user tersebut, lalu mengambil 10 prediksi tertinggi.

![10terbaik](https://github.com/Ayasa18/Recomendation-System/blob/bf22b83833639897832dbf699de72cb6702a4f3b/Asset/10AnimeRekomendasi.png?raw=true)

  Model rekomendasi berhasil mengidentifikasi 10 anime terbaik yang diprediksi paling disukai oleh user dengan ID 10, berdasarkan rating yang telah dipelajari selama pelatihan. Model ini mengevaluasi seluruh daftar anime dan memberikan skor prediksi (rating) untuk masing-masing, lalu memilih 10 dengan nilai tertinggi. Rekomendasi tersebut mencerminkan preferensi pengguna secara personal, seperti terlihat dari munculnya judul-judul populer seperti Gintama°, Shingeki no Kyojin Season 3 Part 2, dan Mononoke, yang kemungkinan besar akan memberikan pengalaman menonton yang memuaskan bagi pengguna tersebut.


![terbaik](https://github.com/Ayasa18/Recomendation-System/blob/bf22b83833639897832dbf699de72cb6702a4f3b/Asset/Visualisasiuser10.png?raw=true)


  Berdasarkan hasil visualisasi rekomendasi, terlihat bahwa Gintama° menjadi anime dengan prediksi rating tertinggi untuk User 10, diikuti oleh Sora yori mo Tooi Basho dan Shingeki no Kyojin Season 3 Part 2, yang menunjukkan bahwa model cenderung merekomendasikan anime dengan popularitas dan kualitas tinggi sesuai preferensi user tersebut.

## Evaluation

Bagian Evaluasi dan Visualisasi bertujuan untuk mengukur performa model rekomendasi setelah proses pelatihan selesai serta menampilkan hasil evaluasi tersebut dalam bentuk visual. Evaluasi biasanya dilakukan dengan menggunakan metrik seperti MAE (Mean Absolute Error) dan RMSE (Root Mean Squared Error) untuk melihat seberapa akurat prediksi model dibandingkan dengan nilai rating sebenarnya.

### ✅ Mean Squared Error (MSE)

**Penjelasan:**
MSE adalah rata-rata dari kuadrat selisih antara nilai prediksi dan nilai aktual. Karena selisih dikuadratkan, MSE akan memberikan penalti besar terhadap kesalahan yang besar (outlier).

**Rumus:**

$$
\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
$$

**Keterangan:**

- `y_i` = nilai aktual
  
- `ŷ_i` = nilai prediksi
  
- `n` = jumlah data
  
- Nilai MSE **tidak dalam satuan asli** (karena dikuadratkan)

---

### ✅ Root Mean Squared Error (RMSE)

**Penjelasan:**
RMSE adalah akar dari MSE. Metrik ini digunakan untuk mengukur rata-rata jarak antara hasil prediksi dengan nilai aktual dalam satuan yang sama dengan data aslinya, sehingga lebih mudah dipahami secara intuitif.

**Rumus:**

$$
\text{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}
$$

**Keterangan:**
- RMSE **menggunakan satuan yang sama dengan target**
- Sensitif terhadap kesalahan besar (karena berasal dari MSE)

---

### ✅ Mean Absolute Error (MAE)

**Penjelasan:**
MAE adalah rata-rata dari nilai absolut selisih antara prediksi dan nilai aktual. MAE memberikan gambaran langsung tentang rata-rata kesalahan prediksi tanpa terlalu dipengaruhi oleh outlier.

**Rumus:**

$$
\text{MAE} = \frac{1}{n} \sum_{i=1}^{n} \left| y_i - \hat{y}_i \right|
$$

**Keterangan:**
- MAE **lebih tahan terhadap outlier** dibanding MSE dan RMSE
- Nilai MAE **dalam satuan yang sama** dengan target

Hasil evaluasi menunjukkan bahwa model memiliki nilai Validation Loss (MSE) sebesar 0.0466, MAE sebesar 0.1557, dan RMSE sebesar 0.1981, yang mencerminkan performa prediksi model terhadap data validasi.


![Evaluasi](https://github.com/Ayasa18/Recomendation-System/blob/9d76a6f045241720a1ea49a63497bd42f58b2c81/Asset/EvaluasiGrafik.png?raw=true)

Berdasarkan grafik MSE, MAE, dan RMSE selama 50 epoch, model menunjukkan tren penurunan yang konsisten pada kedua metrik (train dan validasi), dengan nilai akhir mendekati nol. Penurunan MSE dari 0.10 ke 0, MAE dari 0.25 ke 0.05, dan RMSE dari 0.30 ke 0.10 mengindikasikan bahwa model semakin akurat dalam memprediksi data, baik pada data latih maupun validasi, tanpa tanda overfitting (karena val loss mengikuti tren train loss). Konsistensi penurunan tanpa fluktuasi besar menunjukkan proses pelatihan yang stabil dan efektif. Dengan demikian, model dapat disimpulkan memiliki kemampuan generalisasi yang baik, meskipun perlu dipastikan bahwa data validasi representatif dan tidak terjadi underfitting pada epoch akhir.

 ### Kesimpulan
 
Model sistem rekomendasi anime berbasis Neural Collaborative Filtering yang dibangun dalam proyek ini berhasil memenuhi tujuan utamanya, yaitu memberikan rekomendasi anime yang sesuai dengan preferensi pengguna berdasarkan histori rating. Dengan menggunakan dataset dari Kaggle dan melalui proses preprocessing yang komprehensif, model dilatih menggunakan fungsi loss MSE dan teknik EarlyStopping untuk mencegah overfitting.

Hasil evaluasi model menunjukkan performa yang cukup baik berdasarkan metrik evaluasi berikut:

* Mean Absolute Error (MAE): 0.1557 nilai rendah, menunjukkan bahwa rata-rata selisih antara prediksi dan rating asli relatif kecil.

* Mean Squared Error (MSE): 0.0466 nilai rendah, memperkuat bahwa kesalahan prediksi tidak terlalu menyimpang jauh dari nilai aktual.

* Root Mean Squared Error (RMSE): 0.1981 nilai rendah, mengindikasikan bahwa model cukup akurat dalam merekomendasikan anime yang disukai pengguna.

Model ini terbukti mampu mengidentifikasi pola kesamaan antar pengguna dan menangkap preferensi individual secara efisien. Dalam uji coba, sistem mampu merekomendasikan 10 anime teratas yang relevan dengan selera pengguna, bahkan untuk pengguna yang belum memberikan banyak rating sebelumnya (cold-start problem ringan).

Dengan demikian, sistem rekomendasi ini dapat diandalkan sebagai solusi yang efektif dan personalisasi dalam membantu pengguna menemukan anime yang mereka sukai. Sistem ini juga berpotensi meningkatkan user engagement, memperpanjang waktu interaksi dengan platform, dan mendorong loyalitas pengguna dalam jangka panjang

## Reference
[1] [Jayaperwira, Iklil, Agung Toto Wibowo, and Dade Nurjanah. "Anime Rekomendasi Menggunakan Collaborative Filtering." eProceedings of Engineering 10.3 (2023).](https://openlibrarypublications.telkomuniversity.ac.id/index.php/engineering/article/view/20612/0)

[2] [Roziqiin, Nazhif Muafa, and Muhammad Faisal. "Sistem rekomendasi pemilihan anime menggunakan user-based collaborative filtering." JIPI (Jurnal Ilmiah Penelitian dan Pembelajaran Informatika) 9.1 (2024): 299-306.](https://www.jurnal.stkippgritulungagung.ac.id/index.php/jipi/article/view/4222)

[3] [Penyaringan Kolaboratif Neural. Meningkatkan penyaringan kolaboratif… | oleh Abhishek Sharma | Arsip TDS | Medium
Accessed: 2025-04-22](https://medium.com/data-science/neural-collaborative-filtering-96cef1009401)
