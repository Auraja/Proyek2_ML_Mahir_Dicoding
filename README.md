# Laporan Proyek Machine Learning - Derajat Salim Wibowo

## Project Overview
   
Sistem Rekomendasi Movie Berbasis Content-Based
Ledakan Konten Film: Industri film mengalami pertumbuhan pesat dalam beberapa tahun terakhir, menghasilkan banyak film baru di berbagai genre dan platform. Hal ini, meskipun menyenangkan bagi pecinta film, dapat membuat pengguna kesulitan menemukan film yang sesuai dengan minat mereka. Adomavicius dan Tuzhilin (2005) menyatakan bahwa "tantangan utama dalam sistem rekomendasi adalah membantu pengguna menemukan informasi yang relevan dalam lautan data yang berlimpah" ([1]).

Keterbatasan Sistem Rekomendasi Saat Ini: Sistem rekomendasi film yang ada saat ini, seperti Netflix dan Rotten Tomatoes, banyak yang menggunakan metode collaborative filtering. Sistem ini merekomendasikan film berdasarkan preferensi pengguna lain dengan selera yang mirip. Namun, collaborative filtering memiliki beberapa keterbatasan:
- Cold start problem: Sistem tidak dapat memberikan rekomendasi yang akurat bagi pengguna baru karena belum memiliki data preferensi mereka.
- Data sparsity: Sulit untuk mendapatkan data rating yang lengkap dari semua pengguna.
- Bubble filter: Pengguna hanya direkomendasikan film yang mirip dengan film yang pernah mereka tonton sebelumnya, sehingga membatasi eksplorasi film baru.
- Potensi Sistem Rekomendasi Content-Based: Sistem rekomendasi content-based menawarkan solusi untuk mengatasi keterbatasan tersebut. Sistem ini merekomendasikan film berdasarkan analisis konten film, seperti genre, aktor, sutradara, dan deskripsi plot, dibandingkan -dengan preferensi pengguna lain. Lops, de Gemmis, dan Semeraro (2011) menjelaskan bahwa sistem content-based "menggunakan informasi tentang item yang direkomendasikan (misalnya, film, buku, musik) untuk memprediksi apakah pengguna akan menyukainya" ([2]).

Sistem content-based memiliki beberapa keuntungan:
- Mampu memberikan rekomendasi bagi pengguna baru.
- Lebih efisien dalam penggunaan data.
- Membantu pengguna menemukan film baru di luar genre favorit mereka. Schafer, Konstan, dan Riedl (2001) mengemukakan bahwa sistem content-based "dapat membantu pengguna menemukan item yang tidak mereka ketahui sebelumnya, tetapi kemungkinan besar mereka akan menyukainya" ([3]).

Pentingnya Proyek Sistem Rekomendasi Content-Based:
- Meningkatkan pengalaman pengguna: Sistem ini membantu pengguna menemukan film yang sesuai dengan minat mereka dengan lebih mudah dan efisien.
- Meningkatkan personalisasi: Sistem ini dapat memberikan rekomendasi yang lebih personal dan sesuai dengan preferensi individual pengguna.
- Membantu penemuan film baru: Sistem ini dapat membantu pengguna menemukan film baru di luar genre favorit mereka dan memperluas wawasan film mereka.

## Business Understanding

### Problem Statements

Bagaimana cara efektif dalam merekomendasikan film kepada banyak orang hanya dengan menggunakan data aktivitas masa lalu terkait dengan film menggunakan teknik content-based filtering?

### Goals

Membuat sistem rekomendasi mengenai buku pada aplikasi toko buku menggunakan teknik Content-Based filtering.


## Data Understanding
Dataset yang digunakan pada proyek kali ini terdiri dari 4 Dataset yaitu links.csv, movies.csv, ratings.csv, tags.csv dengan judul [Movie Lens Small Latest Dataset] (https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset)

Variabel-variabel pada Movie Lens Small Latest Dataset adalah sebagai berikut:

Links: Daftar tautan film.
- Terdapat 9742 baris dan 3 kolom.
- Kolomnya adalah movieId, imdbId, dan tmdbId.
- movieId adalah ID unik untuk setiap film.
- imdbId adalah ID IMDb untuk setiap film.
- tmdbId adalah ID TMDb untuk setiap film.
  
Movies: Daftar film yang tersedia.                                    
- Terdapat 9742 baris dan 3 kolom.
- Kolomnya adalah movieId, title, dan genres.
- movieId adalah ID unik untuk setiap film.
- title adalah judul film.
- genres adalah genre-genre yang terkait dengan film tersebut.
  
Ratings: Daftar penilaian yang diberikan pengguna terhadap film.                                 
- Terdapat 100836 baris dan 4 kolom.
- Kolomnya adalah userId, movieId, rating, dan timestamp.
- userId adalah ID pengguna yang memberi penilaian.
-  movieId adalah ID unik untuk setiap film.
- rating adalah penilaian yang diberikan oleh pengguna untuk film tersebut.
- timestamp adalah waktu ketika penilaian diberikan.
  
Tags: Daftar kata kunci dari film.                     
- Terdapat 3683 baris dan 4 kolom.
- Kolomnya adalah userId, movieId, tag, dan timestamp.
- userId adalah ID pengguna yang memberi tag.
- movieId adalah ID unik untuk setiap film.
- tag adalah kata kunci yang terkait dengan film tersebut.
- timestamp adalah waktu ketika tag diberikan.

Berdasaarkan pengolahan data lebih lanjut hasil menunjukan bahwa rating dalam dataset ratings memiliki skala 0.5 hingga 5.0 dan didalam dataset links dan movies memiliki kesamaan dalam movieId

## Data Preparation

Dalam proyek ini, dilakukan beberapa tahapan persiapan data untuk mempersiapkan data untuk analisis dan pemrosesan selanjutnya. 
- Dilakukan penggabungan dengan dataset lain kemudian data gabungan dibersihakan jika terjadi data yang tidak normal dilakukan secara terus menerus hingga data bersih.
- Mengkonversi data yang sudah bersih yang sudah digabungkan menjadi list, data yang dipilih untuk di konversi menjadi list adalah movieId, title, dan genres.
- Data yang sudah di konversikan menjadi list dibuat kamus supaya mempermudah model dalam membacanya.
- TF_IDF juga dilakukan pada preparation data yang sudah menjadi list sehingga data diubah menjadi bentuk matriks yang akan digunakan dalam model.
  
semua tahapan diatas dilakukan supaya data dapat dengan mudah di jalankan dengan model yang akan digunakan dan mendapatkan hasil yang cukup baik dan efisien.

## Modeling

Model yang digunakan pada proyek kali ini adalah Content Based Filtering dengan menghitung derajat kesamaan dalam data yang sudah dijadikan tf_idf matrix
Hasil dari Content Based :
Dimasa lalu user yang menyukai film dibawah ini
|    |   id       |  movie_name                  |  genre         |   
|---:|-----------:|-----------------------------:|----------------|
|  8 |         17 | Sense and Sensibility (1995) | Drama\|Romance | 

Mendapatkan hasil top 5 film rekomendasi untuk user yang menyukai film tersebut yaitu :
|            |    movie_name                                     |  genre         |   
|-----------:|--------------------------------------------------:|---------------:|
|      0     | Widow of St. Pierre, The (Veuve de Saint-Pierr... | Drama\|Romance |  
|      1     |                            Far from Heaven (2002) | Drama\|Romance |  
|      2     |                          Nicholas Nickleby (2002) | Drama\|Romance |  
|      3     |                                        Gia (1998) | Drama\|Romance |  
|      4     |               Talk to Her (Hable con Ella) (2002) | Drama\|Romance |  

Berdasarkan hasil rekomendasi sistem terhadap user yang menyukai film Sense and Sensibility (1995), sistem akan menampilkan film yang sejenis dilihat dari genre filmnya yang sama.

## Evaluation
Matriks yang digunakan dalam proyek sistem rekomendasi film ini adalah matriks cosine similiarity. Matriks cosine similarity merupakan representasi matematis dari kesamaan antara dua dokumen (dalam hal ini, film) berdasarkan cosine similarity. Matriks ini dihasilkan dengan menghitung cosine similarity antara setiap pasangan film dalam dataset film.

Peran dalam Content-Based Filtering:

Dalam sistem rekomendasi film berbasis content-based, matriks cosine similarity digunakan untuk:
- Menemukan film yang serupa: Film dengan nilai cosine similarity tinggi dianggap memiliki konten yang serupa dan direkomendasikan kepada pengguna.
- Memprediksi rating pengguna: Nilai cosine similarity dapat digunakan untuk memprediksi kemungkinan pengguna menyukai film yang belum pernah ditontonnya.
Rumus:

Cosine similarity dihitung dengan rumus berikut:

$$cosine_similarity(x, y) = (x * y) / ||x|| * ||y||$$
dimana:
- x dan y adalah vektor yang mewakili dua film.
- x * y adalah perkalian dot antara vektor x dan y.
- ||x|| dan ||y|| adalah norma Euclidean dari vektor x dan y.

Proyek ini dinilai berhasil dalam membuat rekomendasi film kepada user menggunakan data masa lalu dengan menggunakan matrix cosine similiarity, dengan mengetahui bahwa user menyukai suatu film maka sistem dapat merekomendasikan film film yang memiliki kesamaan dengan film yang disukai user tersebut.

## References
[1] Adomavicius, G., & Tuzhilin, A. (2005). Toward the next generation of recommender systems: A survey of the state-of-the-art and possible extensions. IEEE transactions on knowledge and data engineering, 17(6), 734-749.                    
[2] Lops, P., de Gemmis, M., & Semeraro, G. (2011). Content-based recommender systems: State of the art and trends. In Recommender systems handbook (pp. 73-105). Springer US.              
[3] Schafer, J. B., Konstan, J. A., & Riedl, J. (2001). E-commerce recommendation systems. In The adaptive web (pp. 295-334). Springer Berlin Heidelberg.
