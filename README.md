# **Sistem Rekomendasi Amazon Books Menggunakan Model Pengembangan dengan Teknik Content Based Filtering dan Collaborative Filtering**
![amazon-books4831](https://github.com/user-attachments/assets/169cdf2a-b80b-4b6e-b043-9d0d8eb289ef)
## **Domain Proyek**
### **Latar Belakang**
Dalam era digital yang serba cepat, toko online seperti Amazon memiliki jutaan produk yang harus dikelola dan dipromosikan kepada pelanggan. Salah satu cara efektif untuk memastikan bahwa pelanggan menemukan produk yang relevan. Untuk mengatasi tantangan ini, diperlukan sebuah sistem rekomendasi buku yang bisa memberikan rekomendasi personal secara akurat berdasarkan preferensi pembaca, sehingga bisa membantu mereka menemukan buku - buku yang sesuai dengan minat dan selera mereka. Selain itu, sistem rekomendasi buku juga dapat membantu memberikan dukungan dan peluang baru bagi penulis dan penerbit untuk menjangkau audiens yang lebih luas. 

Menurut [Khalid Anwar et al](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3356349) dalam jurnalnya berjudul Machine Learning Techniques for Book Recommendation: An Overview menjelaskan bahwa sistem rekomendasi buku dapat membantu para pustakawan dalam mengelola katalog perpustakaan yang efisien dan mendukung pembaca dalam memilih buku terbaik dan sesuai selera mereka. Dari sisi penjualan menerapkan sistem rekomendasi buku dapat membantu mengelola inventaris mereka dan mendapatkan lebih banyak keuntungan. Oleh karena itu, dengan banyaknya kelebihan yang diperoleh, maka diperlukan sistem rekomendasi buku untuk meningkatkan pengalaman membaca dan mendukung perkembangan industri.
Sistem rekomendasi pada Amazon Books menggunakan dua pendekatan utama: **Content-Based Filtering** dan **Collaborative Filtering.**

Dengan memadukan kedua pendekatan ini, Amazon dapat memberikan rekomendasi yang lebih akurat dan personal. Penggunaan sistem rekomendasi yang efektif tidak hanya meningkatkan penjualan tetapi juga membangun loyalitas pelanggan, karena pelanggan merasa menemukan buku yang sesuai dengan minat mereka dengan mudah. Proyek ini bertujuan untuk meningkatkan performa sistem rekomendasi buku di Amazon, mengoptimalkan pengalaman berbelanja pengguna, dan meningkatkan kepuasan pelanggan.

## **Business Understanding**
### **Problem Statements**

Amazon books sebuah perusahaan penjual buku yang setelah sekian lama beroperasi, perusahaan tersebut berhasil mengumpulkan berbagai informasi mengenai pelanggan dan daftar buku yang berasal dari berbagai penerbit, serta terdapat rating yang diberikan oleh pelanggan untuk beberapa buku yang dibeli tersebut. Seluruh informasi ini terkumpul dalam [Book Recommendation Dataset](https://www.kaggle.com/datasets/saurabhbagchi/books-dataset).

Seorang Data Scientist di perusahaan tersebut, ingin memanfaatkan data tersebut untuk meningkatkan transaksi penjualan di perusahaan, maka dibuatkan sebuah sistem rekomendasi buku untuk menjawab permasalahan berikut:

1. Berdasarkan data mengenai pengguna, bagaimana membuat sistem rekomendasi yang dipersonalisasi Berdasarkan judul buku dan authornya dengan teknik content-based filtering?
2. Dengan data rating yang dimiliki, bagaimana perusahaan dapat merekomendasikan 10 buku lain yang mungkin disukai dan belum pernah dikunjungi atau dibaca oleh pengguna dengan teknik collaborative filtering ?

### **Goals**
Untuk menjawab pertanyaan tersebut, perusahaan akan membuat sebuah sistem rekomendasi dengan tujuan atau goals sebagai berikut:

1. Menghasilkan 5 jumlah rekomendasi buku yang dipersonalisasi untuk pengguna  dengan teknik content-based filtering.
2. Menghasilkan sejumlah rekomendasi buku yang sesuai dengan preferensi pengguna dan belum pernah dikunjungi atau dibaca sebelumnya dengan teknik collaborative filtering.

### **Solution Statements**
Berdasarkan tujuan atau goals yang sudah dijelaskan sebelumnya, maka akan dibuat sebuah sistem rekomendasi dengan alur sebagai berikut:

1. **Data Understanding**, merupakan tahap awal proyek untuk memahami data yang dimiliki. Dalam kasus ini, terdapat 3 file terpisah mengenai informasi tentang users, ratings, dan books. Pada tahap ini, ada beberapa tahapan untuk memahami data antara lain:
   
   a. **Data loading**, yaitu membaca data langsung dari dataset untuk mengetahui isi atau informasi yang ada di dalam dataset tersebut.

   b. **Univariate Exploratory Data Analysis**. Pada tahap ini akan dilakukan analisis dan eksplorasi setiap variabel pada data.

   c. **Data Preprocessing**. Ini merupakan tahap persiapan data sebelum data digunakan untuk proses selanjutnya. Pada tahap ini, akan dilakukan penggabungan beberapa file sehingga menjadi satu kesatuan file yang utuh dan siap digunakan dalam tahap pemodelan.

3. **Data Preparation**. Pada tahap ini, data dipersiapkan dan dilakukan beberapa teknik seperti mengatasi missing value dan menyamakan nomor ISBN buku. Pada sistem rekomendasi berbasis konten (content-based filtering) yang akan dikembangkan, satu nomor ISBN mewakili             satu kategori buku. Oleh karena itu, perlu pengecekan ulang dan memastikan setiap buku hanya memiliki satu nomor ISBN.
2. **Modeling**. Pada proses pengembangan model akan menggunakan dua metode sebagai berikut:

   a. **Model Development dengan Content Based Filtering**. Pada tahap ini, dikembangkan sistem rekomendasi dengan teknik Content Based Filtering. Teknik ini akan merekomendasikan judul buku yang sesuai dengan nama penulis buku dan disukai pengguna di masa lalu.             Pada tahap ini, akan dicari representasi fitur penting dari setiap kategori buku dengan TF-IDF (Term Frequency - Inverse Document Frequency) Vertorizer dan menghitung tingkat kesamaan (similarity measure) dengan cosine similarity. Setelah itu akan                      menghasilkan sejumlah rekomendasi buku untuk pengguna berdasarkan kesamaan yang telah dihitung sebelumnya.

   b. **Model Development dengan Collaborative Filtering**. Pada tahap ini, dikembangan sistem rekomendasi dengan teknik Collaborative Filtering. Sistem nantinya akan merekomendasikan sejumlah buku kepada pengguna berdasarkan rating yang telah diberikan                      sebelumnya. Dari data rating pengguna akan diidentifikasi nama - nama judul buku yang mirip dan belum pernah dibaca atau dibeli oleh pengguna lainnya.

   c. **Evaluation**, merupakan tahap untuk mengukur kinerja model dan menilai sejauh mana model berhasil dalam mencapai tujuannya dan memperoleh kesamaan fitur. Pada tahap ini digunakan metrik berupa Precision, Recall, dan F1 Score untuk model dengan content based 
      filtering. Sedangkan, pada model dengan collaborative filtering akan menggunakan metrik Root Mean Squared Error (RMSE) sebagai metrik evaluasi model.

### **Data Understanding**

Data yang digunakan pada proyek ini adalah [Books Dataset](https://www.kaggle.com/datasets/saurabhbagchi/books-dataset) yang diunduh dari platform Kaggle. Menurut informasi dari sumber dataset, data dikumpulkan oleh Cai-Nicolas Ziegler dengan informasi sebagai berikut :

![books_dataset](https://github.com/user-attachments/assets/ab0a05f8-3acb-4d34-9f6b-723363bfea4e)

Book Recommendation Dataset terdiri dari 3 file/dataset terpisah yaitu Books, Ratings, dan Users dalam format file CSV (Comma Separated Values). Dataset books terdiri 271.360 baris dan 8 kolom yang berisi informasi tentang buku antara lain nomor ISBN, judul buku, author, tahun publikasi, penerbit, dan 3 kolom untuk link URL gambar buku yang tersedia dalam 3 jenis ukuran yaitu Image-URL-S (small), Image-URL-M (medium), dan Image-URL-L (large). Dataset ratings terdiri dari 1.149.780 baris dan 3 kolom yang berisi informasi user ID atau pengguna, nomor ISBN dan peringkat buku yang berasal dari pengguna. Kemudian, dataset users yang terdiri dari 278.858 baris dan 3 kolom yang berisi informasi user ID atau pengguna, lokasi pengguna, dan usia pengguna.

### **Variabel - variabel pada Book Recommendation Dataset adalah sebagai berikut:**
**Variabel pada dataset Books:**

1. ISBN : nomor ISBN (International Standard Book Number) dari buku.
2. Book-Title : judul buku.
3. Book-Author : nama penulis buku.
4. Year-Of-Publication : tahun publikasi buku.
5. Publisher : nama penerbit buku.
6. Image-URL-S : ukuran gambar small (kecil) dari buku berupa link URL.
7. Image-URL-M : ukuran gambar medium (sedang) dari buku berupa link URL.
8. Image-URL-L : ukuran gambar large (besar) dari buku berupa link URL.

**Variabel pada dataset Ratings:**

1. User-ID : kode unik untuk nama pengguna anonim yang memberikan penilaian.
2. ISBN : nomor ISBN (International Standard Book Number) dari buku.
3. Book-Rating : rating atau peringkat buku dari pengguna atau pembaca.

**Variabel pada dataset Users:**

1. User-ID : kode unik untuk nama pengguna anonim.
2. Location : lokasi pengguna.
3. Age : usia pengguna.

### **Berikut adalah beberapa tahapan untuk memahami data:**

1. Data Loading
2. Univariate Exploratory Data Analysis
3. Data Preprocessing

### **Data Loading**
Pada bagian ini, dataset langsung di import dari situs kaggle sebagai berikut:

![data_loading](https://github.com/user-attachments/assets/fae57dfc-e38b-4e56-9068-81d070b48da0)

**Tabel 1. Tampilan dari Dataset Books**

![dataset_books](https://github.com/user-attachments/assets/5751b6ed-72b6-4933-954a-38ac8ce3d622)

**Tabel 2. Tampilan dari dataset Ratings**

![dataset_rating](https://github.com/user-attachments/assets/c65f0e93-89aa-4a4d-8c99-5533bd2aeffd)

**Tabel 3. Tampilan dari dataset Users**

![dataset_user](https://github.com/user-attachments/assets/7e5161e7-3b68-4abe-8e28-66f73c96ea21)

### **Univariate Exploratory Data Analysis**
Pada tahap ini, akan dilakukan analisis dan eksplorasi pada setiap variabel untuk memahami distribusi dan karakteristik individu dari variabel tersebut. Pemahaman ini nantinya akan membantu dalam menentukan pendekatan atau algoritma yang cocok diterapkan pada data. Variabel - variabel pada Book Recommendation Dataset adalah sebagai berikut:

- books : merupakan data yang berisi informasi buku.
- ratings : merupakan rating atau peringkat yang diberikan ke buku oleh pengguna atau pembaca
- users : merupakan informasi pengguna termasuk informasi demografisnya.

**Books Variabel**

Dengan menggunakan fungsi info(), diketahui bahwa dataset books sebagai berikut :

![book_info](https://github.com/user-attachments/assets/e128b9e4-978f-423e-bb98-8deacc39e3ad)

Diketahui juga bahwa kolom 'Year-Of-Publication' bertipe data object sedangkan tahun publikasi pada umumnya memiliki tipe data integer. Oleh karena itu akan dilakukan perbaikan tipe data terlebih dahulu dengan menjalankan kode berikut: `books['Year-Of-Publication'].astype('int')`. Tetapi setelah dijalankan kode tersebut, terdapat error dengan tulisan **'ValueError: invalid literal for int() with base 10: 'DK Publishing Inc'**, artinya terdapat value pada 'Year-Of-Publication' ada yang bernilai 'DK Publishing Inc'. Sepertinya ini terdapat kesalahan input, sehingga nanti akan dihapus nilai berupa teks tersebut sebelum mengubahnya ke dalam tipe data integer. Berdasarkan penelusuran, terdapat 2 nilai teks yaitu 'DK Publishing Inc' dan 'Gallimard'. Dua nilai teks ini akan dihapus dari fitur 'Year-Of-Publication'. Setelah dihapus, maka barulah dilakukan proses pengubahan tipe data pada 'Year-Of-Publication' menjadi tipe data integer.

Kemudian, langkah selanjutnya adalah menghapus variabel yang tidak diperlukan pada proses pengembangan model. Karena nantinya pada sistem rekomendasi berbasis konten (content-based filtering) akan dibuat rekomendasi berdasarkan judul buku yang sama dengan nama penulis buku yang pernah dibaca oleh pengguna. Maka informasi seperti ukuran gambar tidak diperlukan, sehingga fitur/kolom 'Image-URL-S', 'Image-URL-M', dan 'Image-URL-L' bisa dihapus. Tampilan dataset books setelah dilakukan proses penghapusan beberapa nilai dan fitur akan terlihat sebagai berikut.

**Tabel 4. Tampilan dari Dataset Books setelah proses penghapusan beberapa nilai dan fitur**

![drop_book_pic](https://github.com/user-attachments/assets/2dc17980-6816-4dc3-910c-df1b0209af80)

Setelah melalui proses penghapusan beberapa nilai dan fitur, dataset hanya tersisa 5 kolom saja, dengan masing - masing variabel memiliki entri sebagai berikut:

- Jumlah nomor ISBN Buku: 271357
- Jumlah judul buku: 242132
- Jumlah penulis buku: 102021
- Jumlah Tahun Publikasi: 116
- Jumlah nama penerbit: 16805

Perhatikan bahwa jumlah judul buku pada dataset yaitu 242.132 sedangkan jumlah nomor ISBN buku adalah 271.357, artinya ada beberapa buku yang tidak memiliki nomor ISBN, karena satu ISBN hanya boleh dimiliki oleh satu buku saja. Untuk Kasus ini nantinya dataset akan di filter agar setiap buku dipastikan memiliki satu nomor ISBN. Selanjutnya, dilakukan distribusi data untuk melihat 10 nama penulis teratas berdasarkan jumlah buku seperti terlihat pada Gambar 1.

![grafik10](https://github.com/user-attachments/assets/e6ec618a-ebdf-4ce6-a5d2-0a5daa22339e)

Gambar 1. Distribusi data tentang 10 nama penulis teratas berdasarkan jumlah buku

Berdasarkan informasi pada Gambar 1, diketahui bahwa penulis dengan nama Agatha Christie menulis paling banyak buku yaitu sebanyak lebih dari 600 buku. Dari informasi ini juga diketahui jika di dalam dataset terdapat beberapa nama penulis yang menulis buku lebih dari satu judul buku.

**Ratings Variabel**

Selanjutnya, dilakukan eksplorasi pada variabel ratings, yaitu penilaian terhadap buku dari pembaca atau pengguna. Digunakan fungsi info() untuk melihat informasi dari variabel tersebut. Berdasarkan output yang diberikan, diketahui terdapat sebanyak 1.149.780 entri dan 3 kolom yaitu User-ID yang merupakan kode unik pengguna anonim yang memberikan peringkat, ISBN yang merupakan identitas berupa nomor unik buku, dan Book-Rating yang merupakan rating buku yang diberikan oleh pembaca atau pengguna. Diketahui juga terdapat 105.283 pengguna yang memberikan rating buku, jumlah buku berdasarkan ISBN yang diberikan rating adalah 340.556 buku, dan rating yang diberikan oleh masing - masing buku memiliki niliai berkisar antara 0 sampai 10, dimana 0 adalah rating paling rendah sedangkan 10 adalah rating paling tertinggi.

![df_rating](https://github.com/user-attachments/assets/aeccbabc-3a7d-4c08-8bc4-306d70a1772e)

Seperti terlihat pada informasi sebelumnya, dataset ratings memiliki 1.149.780 baris data, dan itu merupakan jumlah yang sangat banyak. Nantinya, dataset rating ini yang akan digunakan dalam proses pengembangan model dengan collaborative filtering. Oleh karena itu, untuk menghemat alokasi memori pada saat pelatihan model nantinya, dataset rating ini tidak akan digunakan semua. Dataset rating hanya mengambil data pertama hingga data ke 5000 saja (exclude data ke 5000). Dataset ini akan digunakan untuk pengembangan model dengan collaborative filtering karena membutuhkan data rating terhadap pengguna untuk memberikan rekomendasi judul buku kepada pengguna lainnya. Untuk memudahkan supaya tidak tertukar dengan fitur lain yang serupa, variabel diubah namanya menjadi df5000_rating sebagai berikut.

![df5000](https://github.com/user-attachments/assets/a639622a-4352-429f-964b-d60bb1c154e9)

**Users Variabel**

Variabel terakhir yang akan dilakukan eksplorasi adalah variabel users. Variabel ini berisi informasi tentang pengguna anonim beserta demografinya. Digunakan fungsi info() untuk melihat informasi variabel. Berdasarkan output yang diberikan, diketahui terdapat 278.858 entri dan terdapat 3 variabel yaitu User-ID yang merupakan kode unik dari pengguna anonim, Location yang merupakan lokasi pengguna, dan Age yang merupakan usia pengguna. Diketahui juga terdapat beberapa pengguna yang usianya tidak diketahui. Data user berguna jika ingin membuat sistem rekomendasi berdasarkan demografi atau kondisi sosial pengguna. Namun, untuk studi kasus kali ini, tidak akan digunakan data users pada model. Pada pengembangan model, data yang digunakan adalah data books dan ratings.

![user_df](https://github.com/user-attachments/assets/563659a1-864b-4e1c-a397-26bba32b0e22)

### **Data Preprocessing**
Seperti yang sudah diketahui berdasarkan tahapan data understanding bahwa folder Book Recommendation Dataset terdiri dari 3 file terpisah yaitu books, ratings, dan users. Pada tahap ini, akan dilakukan proses penggabungan file menjadi satu kesatuan file agar sesuai dengan pengembangan model yang ingin dibuat. Variabel setelah dilakukan penggabungan menjadi 7 variabel dengan 1.149.780 baris data. Tampilan Dataset bisa dilihat pada Tabel 5, dataset inilah yang akan digunakan untuk membuat sistem rekomendasi.

**Tabel 5. Tampilan dari dataset yang sudah dilakukan proses penggabungan antara variabel ratings dan books**

![gabung](https://github.com/user-attachments/assets/87d865d3-6f4a-4494-ab67-22345eb38919)

### **Data Preparation**
Karena terdapat dua jenis teknik yang digunakan pada proses pengembangan model, yaitu teknik content based filtering dan collaborative filtering, maka tahap persiapan data akan dibagi menjadi dua bagian, yaitu Data Preparation untuk Model Pengembangan dengan Content Based Filtering, dan Data Preparation untuk Model Pengembangan dengan Collaborative Filtering.

Data Preparation Untuk Model Pengembangan dengan Content Based Filtering
Pada tahap ini di akan dilakukan beberapa teknik untuk mempersiapkan data seperti:

Menghilangkan missing value.
Menyamakan jenis buku berdasarkan ISBN.
Pada sistem rekomendasi berbasis konten (content-based filtering) yang akan dikembangkan, satu nomor ISBN mewakili satu judul buku, yang artinya nomor ISBN pada setiap buku bersifat unik. Sehingga perlu dipersiapkan terlebih dahulu datanya agar siap untuk digunakan pada proses pelatihan model.

Mengatasi Missing Value
Pertama dilakukan pengecekan missing value menggunakan kode berikut: books.isnull().sum(). Dari kode tersebut diketahui Terdapat banyak missing value pada sebagian besar fitur. Hanya fitur User-ID, ISBN, dan Book-Rating saja yang memiliki 0 missing value. Jumlah mising value terbesar ada di fitur 'Publisher' yaitu sebesar 118.650. 118.650 dari total dataset yaitu 1.149.780 merupakan jumlah yang tidak terlalu signifikan atau masih tergolong kecil. Oleh karena itu, untuk kasus ini dilakukan proses drop atau penghapusan pada missing value ini dan buatkan dalam bentuk variabel baru bernama books_clean. Setelah dilakukan proses penghilangan missing value, dataset terdiri dari 1.031.128 baris.

![book_clean](https://github.com/user-attachments/assets/be1388d1-f64e-4469-a4d7-387f521c536c)

Menyamakan Jenis Buku Berdasarkan ISBN
Selanjutnya, sebelum masuk tahap pemodelan, diperlukan proses menyamakan judul buku berdasarkan ISBN-nya. Jika terdapat nomor ISBN yang sama pada lebih dari satu judul buku dapat menyebabkan bias pada data. Oleh karena itu harus dipastikan bahwa hanya terdapat satu nomor ISBN pada satu judul buku saja. Pada proses ini dilakukan pengecekan ulang data setelah proses cleaning pada tahap sebelumnya. Berdasarkan informasi pada dataset, diketahui bahwa jumlah nomor ISBN dengan jumlah judul buku tidak sama, artinya terdapat nomor ISBN yang sama pada lebih dari satu judul buku. Oleh karena itu, diatasi dengan mengubah datasetnya menjadi data unik sehingga nantinya siap dimasukkan ke dalam proses pemodelan dengan cara membuang data duplikat pada kolom 'ISBN'. Setelah melewati proses menyamakan jumlah dari jenis buku berdasarkan ISBN, dataset hanya tersisa 270.144 baris data. Tahap berikutnya yaitu dibuatkan dictionary untuk menentukan pasangan key-value pada data isbn_id, book_title, book_author, year_of_publication, dan publihser yang sudah disiapkan sebelumnya untuk proses pengembangan model sistem rekomendasi berbasis konten (content-based filtering). Hasil pembuatan dictionary disimpan dalam variabel bernama prep_book dan terlihat seperti pada Tabel 6.

**Tabel 6. Tampilan dataset books_new setelah menghilangkan missing value dan menyamakan jenis buku berdasarkan ISBN**

![prep_book](https://github.com/user-attachments/assets/5e95b4e0-233a-450a-94d1-8089019bf69f)

Berdasarkan informasi sebelumnya, dataset memiliki sekitar 270.144 baris data. Karena dataset tersebut terlalu banyak dan secara otomatis alokasi memori yang digunakan nantinya akan sangat banyak untuk memproses seluruh data pada pengembangan model, maka pada proyek ini hanya akan mengambil data pertama hingga data ke 20.000 (exlude data ke 20.000). Dataset books_ok inilah yang akan digunakan pada proses pengembangan model dengan teknik Content Based Filtering.

![book_ok](https://github.com/user-attachments/assets/c77b0152-671c-4e23-b151-7ab56ad166b1)

### **Data Preparation Untuk Model Pengembangan dengan Collaborative Filtering**
Pada model pengembangan dengan collaborative filtering, data nantinya akan dibagi menjadi data training dan data validasi dalam proses pelatihan model, sebelum di bagi menjadi data training dan data validasi, data harus dipersiapkan terlebih dahulu. Data rating harus diubah ke dalam bentuk matriks numerik agar nantinya mempermudah proses pelatihan model sehingga model menjadi mudah mengenali/mempelajari data tersebut. Sebelum itu dilakukan, Pada tahap ini di dilakukan beberapa teknik untuk mempersiapkan data seperti menyandikan (encode) fitur 'User-ID' dan 'ISBN' ke dalam indeks integer, memetakan 'User-ID' dan 'ISBN'ke dataframe yang berkaitan, dan yang terakhir mengecek beberapa hal dalam data seperti jumlah pengguna, jumlah buku, kemudian mengubah nilai rating menjadi float agar bisa digunakan pada proses pelatihan model. Setelah tahap persiapan data sudah selesai, data siap dibagi menjadi data training dan data validasi untuk proses training model.

## **Modeling**
### **Model Development dengan Content Based Filtering**
Pada tahap ini, dikembangkan model dengan teknik Content Based Filtering. Content Based Filtering adalah salah satu pendekatan dalam sistem rekomendasi yang menggunakan informasi atau "konten" dari item atau pengguna untuk membuat rekomendasi. Ide dasarnya adalah mencocokkan preferensi pengguna dengan karakteristik atau konten dari item yang telah dilihat atau disukai oleh pengguna sebelumnya. Misalkan, jika seorang pengguna menyukai atau pernah membeli buku dengan judul "Introduction to Machine Learning" dan buku tersebut memiliki fitur berupa nama penulis buku yaitu "Alex Smola", maka sistem akan mencari buku lain dengan fitur serupa dan merekomendasikannya dalam bentuk top-N recommendation kepada pengguna tersebut.

**Kelebihan teknik Content Based Filtering:**

- Memberikan rekomendasi yang personal untuk setiap pengguna berdasarkan preferensi unik pengguna.
- Cocok untuk mengatasi masalah cold-start (ketika sedikit data pengguna tersedia) dan dapat memberikan rekomendasi yang baik sejak awal.
- Tidak tergantung pada data pengguna lain.
- Cocok untuk item dengan fitur atau atribut yang mudah diukur atau diidentifikasi, seperti genre, penulis, atau karakteristik lainnya.

**Kekurangan teknik Content Based Filtering:**

- Tidak efektif dalam menangani kejutan, karena hanya merekomendasikan item yang serupa dengan yang sudah diketahui pengguna.
- Kesulitan dalam menangkap preferensi yang kompleks atau dinamis dari pengguna, terutama jika item yang serupa tidak mencerminkan preferensi yang mendalam.
- Ada risiko "filter bubble" di mana pengguna hanya menerima rekomendasi yang sesuai dengan preferensi pengguna yang sudah diketahui, tanpa diverifikasi.
  
Pada proses pengembangan model dilakukan pencarian representasi fitur penting dari setiap judul buku dengan TF-IDF (Term Frequency - Inverse Document Frequency) Vectorizer. TF-IDF vectorizer adalah alat yang digunakan untuk mengonversi dokumen teks menjadi representasi vektor berdasarkan nilai TF-ID setiap kata dalam dokumen tersebut. TF (Term Frequency) mengukur seberapa sering suatu kata muncul dalam suatu dokumen. Sedangkan, IDF mengukur seberapa unik atau jarang suatu kata muncul dalam seluruh koleksi dokumen. Vektor ini nanti digunakan untuk melakukan proses pencarian representasi fitur penting dari setiap judul buku berdasarkan nama penulis buku pada model yang dikembangkan dengan teknik Content Based Filtering. Pada proyek ini digunakan fungsi tfidfvectorizer() dari library Sklearn. Pertama, dilakukan import fungsi tfidfvectorizer() untuk melakukan perhitungan idf pada data book_author, kemudian dilanjutkan dengan melakukan mapping array dari fitur index integer ke fitur nama menggunakan fungsi get_feature_name_out(). Langkah selanjutnya yaitu melakukan fit dan transformer data ke dalam bentuk matriks dengan ukuran (20000, 8746) agar bisa dikenali saat proses mencari kesamaan fitur. Nilai 20000 merupakan ukuran data dan 8746 merupakan matriks nama penulis buku. Untuk menghasilkan vektor tf-idf dalam bentuk matriks, digunakan fungsi todense(). Terakhir, tampilkan matriks tf-idf untuk beberapa judul buku dan nama penulis buku dalam bentuk dataframe, dimana kolom diisi dengan nama penulis buku sedangkan baris diisi dengan judul buku seperti terlihat pada Tabel 7.

**Tabel 7. Dataframe dari matriks tf-idf**

![tfidf](https://github.com/user-attachments/assets/a0f42723-5255-4e5a-98ec-3af04b807531)

Berdasarkan Tabel 7, matriks tf-idf berhasil mengidentifikasi representasi fitur penting dari setiap kategori judul buku dengan fungsi tfidfvectorizer. Pada Kasus ini dataset hanya ditampilkan berupa sampel data sehingga tidak terlihat keseluruhan matriks. Dari 20000 data hanya dipilih sampel data acak yang terdiri dari 10 judul buku pada baris vertikal dan 15 nama penulis buku pada baris horizontal.

Sementara itu, untuk menghitung derajat kesamaan (similarity degree) antar judul buku digunakan teknik cosine similarity. Metode ini digunakan untuk mengukur sejauh mana kesamaan antar dua vektor dalam ruang berdimensi banyak. [Cosine similarity](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.pairwise.cosine_similarity.html) mengukur sudut kosinus antara dua vektor, dan semakin kecil sudutnya, semakin besar kesamaan antara vektor - vektor tersebut. Pada proyek ini digunakan fungsi cosine_similarity dari library Sklearn. Pertama, digunakan fungsi cosine_similarity() dari library sklearn untuk menghitung nilai cosine similarity pada matriks tf-idf yang sudah dibuat sebelumnya. Dengan fungsi cosine_similarity(), didapat nilai kesamaan (similarity) antar judul buku berupa matriks kesamaan dalam bentuk array. Kemudian, dibuatkan dataframe dari hasil perhitungan cosine similarity dengan baris dan kolom berupa nama judul buku. Tampilan dataframe hasil perhitungan cosine similarity terlihat pada Tabel 8.

**Tabel 8. Dataframe hasil perhitungan cosine similarity**

![cosine_df](https://github.com/user-attachments/assets/be4f5e87-6ca4-4507-bee3-4ad46139b8ff)

Berdasarkan Tabel 8, dengan cosine similarity, berhasil diidentifikasi kesamaan antara satu judul buku dengan judul buku lainnya. Diketahui Shape (20000, 20000) yang merupakan ukuran matriks similarity dari data. Berdasarkan data yang ada, matriks diatas pada Tabel 8 sebenarnya berukuran 20000 judul buku x 20000 judul buku (masing - masing dalam sumbu X dan Y). Artinya, telah berhasil mengidentifikasi tingkat kesamaan pada 20000 judul buku. Tapi disini tidak ditampilkan semua datanya karena keterbatasan alokasi memori pada perangkat. Oleh karena itu, hanya dipilih 5 judul buku pada baris vertikal dan 5 judul buku pada baris horizontal. Dengan data kesamaan (similarity) judul buku yang diperoleh sebelumnya, akan dilakukan proses rekomendasi daftar judul buku yang mirip dengan judul buku yang sebelumnya pernah dibeli atau dibaca oleh pengguna.

**Mendapatkan Rekomendasi**
Pada tahap ini, dibuatkan sebuah fungsi bernama rekomendasi_buku dengan beberapa parameter sebagai berikut:

- book_title : nama judul buku (index kemiripan dataframe).
- similarity_data : Dataframe mengenai similarity yang telah didefinisikan sebelumnya.
- items : Nama dan fitur yang digunakan untuk mendefinisikan kemiripan, dalam hal ini adalah 'book_title' dan 'book_author'.
- k : Jumlah top-N recommendation yang diberikan oleh sistem rekomendasi. Secara default, k bernilai 5.

fungsi rekomendasi_buku adalah fungsi yang dibuat untuk menampilkan hasil rekomendasi berbasis konten berupa judul buku dengan nama penulis yang sama dengan judul buku yang pernah dibeli atau dibaca oleh pengguna. Sebelum fungsi dibuat, perlu diingat bahwa definisi dari sistem rekomendasi yang menyatakan bahwa keluaran sistem adalah berupa top-N recommendation. Oleh karena itu, nantinya untuk mendapatkan rekomendasi perlu diberikan sejumlah rekomendasi judul buku pada pengguna yang diatur pada parameter k.

Pada fungsi rekomendasi_buku digunakan juga fungsi argpartition() untuk proses pengambilan sejumlah nilai k tertinggi dari similarity data. Selanjutnya, mengambil data dari bobot (tingkat kesamaan) tertinggi ke terendah. Data ini dimasukkan ke dalam variabel bernama 'closest'. Berikutnya, perlu dihapus book_title yang dicari agar tidak muncul dalam daftar rekomendasi. Dalam kasus ini, akan dicari judul buku yang mirip dengan judul buku yang nanti di input dalam book_title, sehingga perlu drop book_title agar tidak muncul dalam daftar rekomendasi yang diberikan nanti. Contoh judul buku yang digunakan terlihat pada Tabel 9.

**Tabel 9. Contoh judul buku yang digunakan untuk menampilkan rekomendasi**

![book_s](https://github.com/user-attachments/assets/a546a1e6-4223-4fe4-85ac-52a0aaa7a47b)

Pada Tabel 9, terlihat bahwa judul buku 'A Caribbean Mystery' yang ditulis oleh 'Agatha Christie'. Selanjutnya, digunakan fungsi rekomendasi_buku untuk menampilkan rekomendasi 5 buku teratas yang direkomendasikan sistem berdasarkan judul buku di Tabel 9. Hasilnya terlihat pada Tabel 10.

**Tabel 10. Hasil rekomendasi 5 judul buku teratas dengan kateogri nama penulis (book_author)**

![book_hasil](https://github.com/user-attachments/assets/5c733b49-c34a-4b26-b7c3-acb55c604c18)

Berdasarkan Tabel 10, dapat dilihat bahwa sistem berhasil merekomendasikan 5 judul buku teratas dengan kategori nama penulis (book_author) yaitu 'Agatha Christie'.

### **Model Development dengan Collaborative Filtering**
Pada proses pengembangan model kali ini, akan diterapkan teknik collaborative filtering untuk membuat sistem rekomendasi. Teknik ini membutuhkan data rating dari pengguna atau pembaca. Collaborative filtering adalah salah satu metode dalam sistem rekomendasi yang memprediksi preferensi atau minat pengguna terhadap item berdasarkan informasi dari pengguna lain (kolaborasi). Ide dasar dibalik collaborative filtering adalah bahwa pengguna yang memiliki preferensi serupa dalam masa lalu cenderung memiliki preferensi serupa untuk item di masa depan. Pada proyek ini akan dibuat model collaborative filtering berdasarkan kesamaan antar pengguna (User-Based Collaborative Filtering).

**Kelebihan Collaborative Filtering:**

- Dapat memberikan rekomendasi yang sangat personal kepada pengguna karena memanfaatkan preferensi dan perilaku pengguna secara langsung.
- Tidak memerlukan pengetahuan mendalam tentang item atau produk yang direkomendasikan. Collaborative filtering hanya memerlukan pola preferensi pengguna.
- Dapat menangani item baru yang belum memiliki sejarah penggunaan atau peringkat, karena rekomendasi didasarkan pada pola perilaku keseluruhan pengguna.

**Kekurangan Collaborative Filtering:**

- Collaborative filtering mengalami kesulitan saat menghadapi masalah cold start, karena tanpa data sejarah, sulit memberikan rekomendasi yang akurat.
- Menghadapi masalah dengan data yang bersifat sparse (jarang), di mana mayoritas pengguna hanya memberikan peringkat atau preferensi untuk sebagian kecil item.
- Perfoma collaborative filtering dapat menurun seiring dengan pertambahan jumlah pengguna atau item, karena perhitungan kesamaan antar pengguna atau item dapat menjadi lebih kompleks dan membutuhkan sumber daya yang signifikan.

Pengembangan model dengan Collaborative filtering pada proyek ini akan menghasilkan rekomendasi sejumlah judul buku yang sesuai dengan preferensi pengguna berdasarkan rating yang telah diberikan sebelumnya. Dari data rating pengguna, akan diidentifikasi nama - nama judul buku yang mirip dan belum pernah dibaca atau dibeli oleh pengguna untuk direkomendasikan.

Setelah tahapan persiapan data untuk pengembangan model ini sudah dilakukan di bagian data preparation sebelumnya, langkah selanjutnya dilakukan pembagian data untuk data training dan data validasi, kemudian dilanjutkan dengan proses training model. Pada proses training, model menghitung skor kecocokan antara pengguna dan judul buku dengan teknik embedding. Pertama, dilakukan proses embedding terhadap data pengguna dan judul buku. Selanjutnya, lakukan operasi perkalian dot product antara embedding pengguna dan judul buku. Selain itu, ditambahkan bias untuk setiap pengguna dan judul buku. Skor kecocokan ditetapkan dalam skala [0,1] dengan fungsi aktivasi sigmoid. Model dibuatkan class RecommenderNet dengan [keras Model class](https://keras.io/api/models/model/). Kode class RecommenderNet ini terinspirasi dari tutorial dalam situs [keras](https://keras.io/examples/structured_data/collaborative_filtering_movielens/) dengan beberapa adaptasi layer yang menyesuaikan dengan kasus yang sedang dikerjakan. Model akan menggunakan Binary Crossentropy untuk menghitung loss function, Adam (Adaptive Moment Estimation) sebagai optimizer, dan Root Mean Squared Error (RMSE) sebagai metrik evaluasi.

**Membagi Data Untuk Training dan Validasi**
Sebelum dilakukan proses pembagian data. Dataset akan diacak terlebih dahulu agar distribusinya menjadi random. Setelah itu, dilakukan proses pembagian data menjadi data train dan validasi dengan komposisi 80:20. Namun sebelumnya, perlu dipetakan (mapping) data user dan judul buku menjadi satu value terlebih dahulu. Kemudian, dibuat rating dalam skala 0 sampai 1 agar mudah dalam melakukan proses training.

**Proses Training**
Pada proses training model, model akan menghitung skor kecocokan antara pengguna dan judul buku dengan teknik embedding. Pertama, dilakukan proses embedding terhadap data user dan book_title. Selanjutnya, lakukan operasi perkalian dot product antara embedding user dan book_title. Selain itu, juga dapat ditambahkan bias untuk setiap user dan book_title. Skor kecocokan ditetapkan dalam skala [0, 1] dengan fungsi aktivasi sigmoid.

Di sini, Model dibuatkan class RecommenderNet dengan keras Model class. Kode class RecommenderNet ini terinspirasi dari tutorial dalam situs keras dengan beberapa adaptasi layer yang menyesuaikan dengan kasus yang sedang dikerjakan. Class RecommenderNet ini akan berisi layer yang akan melatih model. Setelah layer model sudah dibuat, dilakukan proses compile terhadap model menggunakan Binary Crossentropy untuk menghitung loss function, Adam (Adaptive Moment Estimation) sebagai optimizer, dan root mean squared error (RMSE) sebagai metrics evaluation.

Berdasarkan hasil proses training model, didapat hasil yang cukup memuaskan dan model konvergen pada epochs sekitar 50. Dari proses ini, diperoleh nilai Root Mean Squared Error (RMSE) sebesar sekitar 0.2953 dan RMSE pada data validasi sebesar 0.3385. Nilai ini cukup bagus untuk sistem rekomendasi. Untuk mengetahui hasil dari pengembangan model, langkah selanjutnya adalah mendapatkan rekomendasi judul buku berdasarkan model yang dikembangan.

**Mendapatkan Rekomendasi Judul Buku**
Untuk mendapatkan rekomendasi judul buku, pertama diambil sampel user secara acak dan definisikan variabel book_not_read yang merupakan daftar buku yang belum pernah dibaca atau dibeli oleh pengguna. variabel book_not_read inilah yang akan menjadi judul buku yang direkomendasikan oleh sistem. Variabel book_bot_visit diperoleh dengan menggunakan operator bitwise (~) pada variabel book_read_by_user. Selanjutnya, untuk memperoleh rekomendasi judul buku, digunakan fungsi model.predict() dari library Keras dan hasil output akan menampilkan top-N recommendation berdasarkan preferensi pengguna seperti terlihat pada Tabel 11 dan Tabel 12.

Tabel 11. Hasil top-N recommendation berupa buku dengan nilai rating tertinggi dari user

![user32](https://github.com/user-attachments/assets/e0c69d98-3318-42ab-a43a-77e9f65cd49f)

Tabel 12. Hasil top-N recommendation berupa 10 buku teratas yang direkomendasikan

![10book](https://github.com/user-attachments/assets/51475f24-6c36-4784-8a5d-9854205efdf0)

Berdasarkan Tabel 11 dan Tabel 12, model telah berhasil membuat rekomendasi kepada user. Hasil tersebut adalah rekomendasi untuk user dengan id 32. Dari output tersebut, dapat dibandingkan antara 'Book with high ratings from user' dan 'Top 10 books recomendation' untuk user. Perhatikan, beberapa judul buku rekomendasi menyediakan nama penulis bukunya juga yang sesuai dengan rating user. Diperoleh 10 rekomendasi teratas buku yang disertai juga dengan nama penulisnya untuk user tersebut serta terdapat 1 judul buku yang merupakan buku dengan rating tertinggi dari user.

## **Evaluation**
Evaluasi Model dengan Content Based Filtering
Metrik yang digunakan untuk evaluasi model dengan content based filtering di proyek kali ini adalah Precision, Recall, dan F1-Score. Metrik ini adalah metrik yang umum digunakan untuk mengukur kinerja model. Precision merupakan rasio item yang revelan yang dihasilkan oleh model terhadap total item yang dihasilkan. Recall merupakan rasio item relevan yang dihasilkan oleh model terhadap total item yang seharusnya direkomendasikan. Sedangkan, F1 Score adalah gabungan dari Precision dan Recall, memberikan nilai tunggal yang mengukur keseimbangan antara keduanya. Berikut adalah rumus untuk menghitung Precision, Recall, dan F1 Score pada model sistem rekomendasi berbasis konten:

![f1score](https://github.com/user-attachments/assets/75348195-accf-4211-93b2-1f401f0c85fe)

Sebelum menghitung nilai evaluasi metrik menggunakan precision, recall dan f1 score, diperlukan sebuah data yang terdiri dari label sebenarnya dan digunakan untuk menilai hasil prediksi model, data ini disebut sebagai data ground truth. Data ground truth pada proyek ini dibuat menggunakan hasil derajat kesamaan yang dihitung menggunakan teknik cosine similarity, dimana setiap baris dan kolom mewakili judul buku, dan nilai di setiap sel pada dataframe mewakili label. Angka 1 untuk similar, dan angka 0 untuk tidak similar. Perlu ditetapkan juga sebuah nilai ambang batas atau threshold untuk memutuskan apakah nilai similarity antara dua item harus dianggap 1 (similar) atau 0 (tidak similar). Nilai ambang batas atau threshold ditetapkan sebesar 0.5 pada proyek ini. Nilai threshold ini disesuaikan dengan kebutuhan dan karakteristik setelah melihat hasil rekomendasi sebelumnya. Lalu dibuatkan matriks ground truth menggunakan fungsi np.where() dari NumPy. Matriks ini akan memiliki nilai 1 di posisi di mana nilai cosine similarity antara dua item lebih besar atau sama dengan nilai threshold yang ditetapkan, dan nilai 0 di posisi di mana nilai similarity di bawah threshold. Kemudian, setelah matriks dibuat, hasilnya disajikan dalam bentuk dataframe. Baris dan kolom Dataframe ground truth ini diindeks menggunakan judul buku dari data.

Setelah dibuatkan matriks ground truth yang berisi label sebenarnya dari hasil cosine similarity. Selanjutnya, dilakukan proses perhitungan evaluasi model dengan metrik precision, recall, dan f1 score. Pertama, mengimport fungsi [precision_recall_fscore_support](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_recall_fscore_support.html) dari library Sklearn yang digunakan untuk menghitung precision, recall dan f1 score. Lalu karena keterbatasan alokasi memori pada perangkat, data hanya diambil sekitar 10000 sampel dari cosine similarity dan ground truth matriks. Hal ini dilakukan untuk mempercepat proses perhitungan, terutama karena ukuran matriks yang cukup besar. Kemudian, matriks cosine similarity dan ground truth dikonversi menjadi array satu dimensi agar mempermudah perbandingan dan perhitungan metrik evaluasi.

Hasilnya disimpan dalam array predictions. Terakhir, digunakan fungsi precision_recall_fscore_support untuk menghitung precision, recall, dan f1 score. Parameter average='binary' digunakan karena sedang mengukur kinerja dalam konteks klasifikasi biner (1 atau 0). Parameter 'zero_division=1' digunakan untuk menghindari pembagian dengan nol jika ada kelas yang tidak terdapat di prediksi. Hasil evaluasi metriks didapat adalah sebagai berikut:

- Precision: 1.0
- Recall: 1.0
- F1-score: 1.0

Berdasarkan hasil evaluasi, didapat nilai dari masing - masing metrik evaluasi yaitu precision, recall dan F1 Score. Nilai Precision didapat sebesar 1.0, artinya semua prediksi positif model adalah benar dan tidak terdapat false positive. Nilai recall didapat nilai 1.0 menunjukkan bahwa model berhasil mengidentifikasi sekitar 100% dari semua item yang sebenarnya relevan. Nilai F1 Score didapat sekitar 1.0 juga, ini menunjukkan keseimbangan yang baik antara precision dan recall dan model cenderung memberikan hasil yang sangat baik untuk kedua kelas (positif dan negatif). Kesimpulannya, berdasarkan hasil metrik evaluasi tersebut model bekerja dengan sangat baik dalam memberikan rekomendasi item dengan content based filtering.
