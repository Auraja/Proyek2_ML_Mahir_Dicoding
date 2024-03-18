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

Bagaimana cara efektif dalam merekomendasikan film kepada banyak orang hanya dengan menggunakan data aktivitas masa lalu terkait dengan film?

### Goals

Solusi yang dapat diberikan ada dengan membuat sistem rekomedasi berbasis content filtering, user dapat dengan mudah mendapatkan rekomendasi film dari model proyek machine learning ini.



## Data Understanding
Dataset yang digunakan pada proyek kali ini terdiri dari 4 Dataset yaitu links.csv, movies.csv, ratings.csv, tags.csv dengan judul [Movie Lens Small Latest Dataset] (https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset)

Variabel-variabel pada Movie Lens Small Latest Dataset adalah sebagai berikut:
- Links: Daftar tautan film.
- Movies: Daftar film yang tersedia.
- Ratings: Daftar penilaian yang diberikan pengguna terhadap film.
- Tags: Daftar kata kunci dari film.

Berdasaarkan pengolahan data lebih lanjut hasil menunjukan bahwa rating dalam dataset ratings memiliki skala 0.5 hingga 5.0 dan didalam dataset links dan movies memiliki kesamaan dalam movieId

## Data Preparation

Dalam proyek ini, dilakukan beberapa tahapan persiapan data untuk mempersiapkan data untuk analisis dan pemrosesan selanjutnya. Pertama, dilakukan penggabungan UserId dari dua DataFrame yang berbeda, yaitu ratings dan tags, untuk mendapatkan satu set UserId yang unik. Selanjutnya, data yang telah digabungkan tersebut diolah dengan menghapus data duplikat dan mengurutkannya dengan baik untuk memastikan keteraturan. Setelah itu, dilakukan pencetakan jumlah total user yang ada dalam data setelah pengolahan. Selanjutnya, beberapa DataFrame yang terpisah, seperti links, movies, ratings, dan tags, digabungkan menjadi satu DataFrame yang disebut movie untuk memudahkan analisis dan pemrosesan data lebih lanjut. Penggabungan DataFrame ini memungkinkan informasi terkait dengan film, seperti link, judul, rating, dan tag, digabungkan ke dalam satu entitas yang lengkap, memfasilitasi analisis yang lebih menyeluruh. Tahapan-tahapan ini diperlukan untuk mempersiapkan data dengan baik sebelum dilakukan analisis dan pemodelan lanjutan dalam proyek ini.

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

## References
[1] Adomavicius, G., & Tuzhilin, A. (2005). Toward the next generation of recommender systems: A survey of the state-of-the-art and possible extensions. IEEE transactions on knowledge and data engineering, 17(6), 734-749.                    
[2] Lops, P., de Gemmis, M., & Semeraro, G. (2011). Content-based recommender systems: State of the art and trends. In Recommender systems handbook (pp. 73-105). Springer US.              
[3] Schafer, J. B., Konstan, J. A., & Riedl, J. (2001). E-commerce recommendation systems. In The adaptive web (pp. 295-334). Springer Berlin Heidelberg.
