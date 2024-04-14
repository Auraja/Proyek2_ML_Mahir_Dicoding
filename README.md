# Laporan Proyek Machine Learning - Derajat Salim Wibowo

## Project Overview
   
Sistem Rekomendasi Movie Berbasis Content-Based                           
Ledakan Konten Film Industri film mengalami pertumbuhan pesat dalam beberapa tahun terakhir, menghasilkan banyak film baru di berbagai genre dan platform. Hal ini, meskipun menyenangkan bagi pecinta film, dapat membuat pengguna kesulitan menemukan film yang sesuai dengan minat pengguna. Adomavicius dan Tuzhilin (2005) menyatakan bahwa "tantangan utama dalam sistem rekomendasi adalah membantu pengguna menemukan informasi yang relevan dalam lautan data yang berlimpah" ([1]).

Keterbatasan Sistem Rekomendasi Saat Ini         
Sistem rekomendasi film yang ada saat ini, seperti Netflix dan Rotten Tomatoes, banyak yang menggunakan metode collaborative filtering. Sistem ini merekomendasikan film berdasarkan preferensi pengguna lain dengan selera yang mirip. Namun, collaborative filtering memiliki beberapa keterbatasan:
- Cold start problem: Sistem tidak dapat memberikan rekomendasi yang akurat bagi pengguna baru karena belum memiliki data preferensi pengguna.
- Data sparsity: Sulit untuk mendapatkan data rating yang lengkap dari semua pengguna.
- Bubble filter: Pengguna hanya direkomendasikan film yang mirip dengan film yang pernah pengguna tonton sebelumnya, sehingga membatasi eksplorasi film baru.
- Potensi Sistem Rekomendasi Content-Based: Sistem rekomendasi content-based menawarkan solusi untuk mengatasi keterbatasan tersebut. Sistem ini merekomendasikan film berdasarkan analisis konten film, seperti genre, aktor, sutradara, dan deskripsi plot, dibandingkan -dengan preferensi pengguna lain. Lops, de Gemmis, dan Semeraro (2011) menjelaskan bahwa sistem content-based "menggunakan informasi tentang item yang direkomendasikan (misalnya, film, buku, musik) untuk memprediksi apakah pengguna akan menyukainya" ([2]).

Sistem content-based memiliki beberapa keuntungan:
- Mampu memberikan rekomendasi bagi pengguna baru.
- Lebih efisien dalam penggunaan data.
- Membantu pengguna menemukan film baru di luar genre favorit pengguna. Schafer, Konstan, dan Riedl (2001) mengemukakan bahwa sistem content-based "dapat membantu pengguna menemukan item yang tidak pengguna ketahui sebelumnya, tetapi kemungkinan besar pengguna akan menyukainya" ([3]).

Pentingnya Proyek Sistem Rekomendasi Content-Based:
- Meningkatkan pengalaman pengguna: Sistem ini membantu pengguna menemukan film yang sesuai dengan minat pengguna dengan lebih mudah dan efisien.
- Meningkatkan personalisasi: Sistem ini dapat memberikan rekomendasi yang lebih personal dan sesuai dengan preferensi individual pengguna.
- Membantu penemuan film baru: Sistem ini dapat membantu pengguna menemukan film baru di luar genre favorit pengguna dan memperluas wawasan film pengguna.

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


![image](https://github.com/Auraja/Proyek2_ML_Mahir_Dicoding/assets/116571074/83f61304-c5ff-448f-96ba-fcfc97a98602)               
Gambar 1.1         
Diagram bar tersebut mengindikasikan bahwa distribusi nilai rating terjadi secara merata dalam rentang skala 0,5 hingga 5, dengan puncak distribusi terjadi pada kisaran nilai 4.

![image](https://github.com/Auraja/Proyek2_ML_Mahir_Dicoding/assets/116571074/ce24b239-ed17-4c60-a46c-c02364e8f211)               
Gambar 1.2            
Diagram bar menunjukkan bahwa genre drama memiliki jumlah film terbanyak, diikuti oleh genre lainnya. Selain itu, terdapat film yang tidak memiliki genre, yang dapat menjadi anomali dalam data dan memengaruhi kinerja model yang akan dibuat. Oleh karena itu, diperlukan pembersihan data sebelum model dibangun untuk mengatasi anomali tersebut.

![image](https://github.com/Auraja/Proyek2_ML_Mahir_Dicoding/assets/116571074/cd3077ff-e6a7-46c7-84a1-ae76ce6d86b2)         
Gambar 1.3         
Boxplot menunjukkan bahwa terdapat korelasi yang signifikan antara genre film dan nilai rating, terutama pada genre documentary dan film-noir. Kedua genre tersebut cenderung mendapatkan nilai rating yang tinggi, sementara genre lainnya memiliki persebaran nilai rating yang hampir seragam.

## Data Preparation

Dalam proyek ini, dilakukan beberapa tahapan persiapan data untuk mempersiapkan data untuk analisis dan pemrosesan selanjutnya. 

1. Penggabungan Seluruh MovieID dan UserID:
- Penggunaan fungsi ```np.concatenate()``` untuk menggabungkan array yang berbeda menjadi satu pada variable movie_all dan user_all.
- Penggunaan fungsi ```np.sort()``` untuk mengurutkan array pada variable movie_all dan user_all.
- Penggunaan fungsi ```np.unique()``` untuk menghapus data yang duplikat variable movie_all yang menghasilkan nilai unik movieId sebanyak 9742 film dan user_all yang menghasilkan nilai unik userId sebanyak 610 user.

2. Penggabungan DataFrame dengan Metode Join:
- Menggunakan fungsi ```pd.merge()``` untuk menggabungkan dataframe berdasarkan kolom kunci tertentu.
- Penggunaan metode left join untuk menyertakan semua baris dari dataframe kiri (pertama) dan baris yang cocok dari dataframe kanan (kedua).
- Spesifikasi kunci penggabungan dengan parameter on='movieId' untuk menggabungkan berdasarkan ID film.

3. Pembersihan Data Missing Values:
- Penggunaan fungsi ```isnull()``` untuk mengidentifikasi nilai yang hilang (NaN).
- Penggunaan fungsi ```dropna()``` untuk menghapus baris yang memiliki nilai kosong yaitu tag yang berjumlah 52549 menjadikan data dari 285762 rows menjadi 233213 rows, hal ini bertujuan membuat data bersih dari anomali yang nantinya mempengaruhi hasil dari sistem rekomendasi yang akan dibangun.

4. Pengurutan dan Penghapusan Duplikat:
- Penggunaan fungsi ```sort_values()``` untuk mengurutkan dataframe berdasarkan kolom movieId pada variabel preparation.
- Penggunaan fungsi ```drop_duplicates()``` untuk menghapus kolom movieId dengan nilai duplikat dari informasi np.unique() sebelumnya terdapat 1554 movieId unik jadi setelah dihapus duplikat data tetap berjumlah 1554 nilai.

5. Konversi Data Series menjadi List:
- Penggunaan metode ```.tolist()``` pada data series untuk mengonversinya menjadi list.

6. Membuat Dictionary:
- Penggunaan fungsi ```pd.DataFrame()``` untuk membuat dataframe baru dari kolom-kolom.
- Penggunaan fungsi ```.to_dict()``` pada dataframe untuk mengonversinya menjadi dictionary yang berisi id, movie_name, dan genre.
  
semua tahapan diatas dilakukan supaya data dapat dengan mudah di jalankan dengan model yang akan digunakan dan mendapatkan hasil yang cukup baik dan efisien.

## Modeling

Model yang digunakan pada proyek kali ini dengan menghitung derajat kesamaan dalam data yang sudah dijadikan tf_idf matrix
Model cosine similarity cocok untuk content-based filtering pada dataset film karena dapat mengukur kemiripan antara vektor fitur film, yang berguna untuk memahami konten film seperti judul, genre, dan tag. Metode ini efisien secara komputasi, skalabel untuk dataset besar, dan dapat mengatasi data yang sparse. Dengan memanfaatkan informasi kaya dari dataset film dan kemampuan cosine similarity, model ini dapat memberikan rekomendasi yang relevan dan personalisasi kepada pengguna berdasarkan preferensi konten pengguna.   

Cosine similarity dihitung dengan rumus berikut:

$$cosine_similarity(x, y) = (x * y) / ||x|| * ||y||$$
dimana:
- x dan y adalah vektor yang mewakili dua film.
- x * y adalah perkalian dot antara vektor x dan y.
- ||x|| dan ||y|| adalah norma Euclidean dari vektor x dan y.


Hasil dari Content Based :
Dimasa lalu user yang menyukai film dibawah ini
|    |   id       |  movie_name                  |  genre         |   
|---:|-----------:|-----------------------------:|----------------|
|  8 |         17 | Sense and Sensibility (1995) | Drama\|Romance | 

Tabel 1.1

Mendapatkan hasil top 5 film rekomendasi untuk user yang menyukai film tersebut yaitu :
|            |    movie_name                                     |  genre         |   
|-----------:|--------------------------------------------------:|---------------:|
|      0     | Widow of St. Pierre, The (Veuve de Saint-Pierr... | Drama\|Romance |  
|      1     |                            Far from Heaven (2002) | Drama\|Romance |  
|      2     |                          Nicholas Nickleby (2002) | Drama\|Romance |  
|      3     |                                        Gia (1998) | Drama\|Romance |  
|      4     |               Talk to Her (Hable con Ella) (2002) | Drama\|Romance |

Tabel 1.2

Berdasarkan hasil rekomendasi sistem terhadap user yang menyukai film Sense and Sensibility (1995), sistem akan menampilkan film yang sejenis dilihat dari genre filmnya yang sama.

## Evaluation
Hasil dari Top-5 rekomendasi film(Tabel 1.2) menggunakan cosine similiarity dengan menggunakan key movie_name dan genre dengan inputan 'Sense and Sensibility (1995)' dengan genre yang ditampilkan yaitu Drama|Romance (Tabel 1.1). berdasarkan rekomendasi menampilkan  film dengan genre yang sama dari kelima film yang direkomendasikan, hal ini menunjukkan bahwa precision sistem rekomendasi berbasis content-based yang telah dibuat berhasil mencapai 5/5 atau 100%.

Rumus dari precision yang digunakan dalam mengukur metrik evaluasi :

$$Precision= Total item yang direkomendasikan/Jumlah item relevan yang direkomendasikan$$
dimana :
- Jumlah item relevan yang direkomendasikan: Ini adalah jumlah item yang benar-benar relevan atau sesuai dengan preferensi atau kebutuhan pengguna di antara semua item yang direkomendasikan oleh sistem. Misalnya, jika dari 10 item yang direkomendasikan, 5 di antaranya relevan dengan preferensi pengguna, maka jumlah item relevan yang direkomendasikan adalah 5.
- Total item yang direkomendasikan: Ini adalah jumlah total item yang diberikan sebagai rekomendasi oleh sistem. Dalam contoh sebelumnya, jika sistem merekomendasikan 10 item kepada pengguna, maka total item yang direkomendasikan adalah 10.
                 
​
Proyek ini dinilai berhasil dalam membuat rekomendasi film kepada user menggunakan data masa lalu dengan menggunakan metrik evaluasi precission, dengan mengetahui bahwa user menyukai suatu film maka sistem dapat merekomendasikan film film yang memiliki kesamaan dengan film yang disukai user tersebut.

## References
[1] Adomavicius, G., & Tuzhilin, A. (2005). Toward the next generation of recommender systems: A survey of the state-of-the-art and possible extensions. IEEE transactions on knowledge and data engineering, 17(6), 734-749.                    
[2] Lops, P., de Gemmis, M., & Semeraro, G. (2011). Content-based recommender systems: State of the art and trends. In Recommender systems handbook (pp. 73-105). Springer US.              
[3] Schafer, J. B., Konstan, J. A., & Riedl, J. (2001). E-commerce recommendation systems. In The adaptive web (pp. 295-334). Springer Berlin Heidelberg.
