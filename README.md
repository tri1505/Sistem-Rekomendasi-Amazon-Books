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

1. Berdasarkan data mengenai pengguna, bagaimana membuat sistem rekomendasi yang dipersonalisasi dengan teknik content-based filtering?
2. Dengan data rating yang dimiliki, bagaimana perusahaan dapat merekomendasikan buku lain yang mungkin disukai dan belum pernah dikunjungi atau dibaca oleh pengguna?

### **Goals**
Untuk menjawab pertanyaan tersebut, perusahaan akan membuat sebuah sistem rekomendasi dengan tujuan atau goals sebagai berikut:

1. Menghasilkan sejumlah rekomendasi buku yang dipersonalisasi untuk pengguna dengan teknik content-based filtering.
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
### **Variabel pada dataset Books:**

1. ISBN : nomor ISBN (International Standard Book Number) dari buku.
2. Book-Title : judul buku.
3. Book-Author : nama penulis buku.
4. Year-Of-Publication : tahun publikasi buku.
5. Publisher : nama penerbit buku.
6. Image-URL-S : ukuran gambar small (kecil) dari buku berupa link URL.
7. Image-URL-M : ukuran gambar medium (sedang) dari buku berupa link URL.
8. Image-URL-L : ukuran gambar large (besar) dari buku berupa link URL.

### **Variabel pada dataset Ratings:**

1. User-ID : kode unik untuk nama pengguna anonim yang memberikan penilaian.
2. ISBN : nomor ISBN (International Standard Book Number) dari buku.
3. Book-Rating : rating atau peringkat buku dari pengguna atau pembaca.

### **Variabel pada dataset Users:**

1. User-ID : kode unik untuk nama pengguna anonim.
2. Location : lokasi pengguna.
3. Age : usia pengguna.

**Berikut adalah beberapa tahapan untuk memahami data:**

1. Data Loading
2. Univariate Exploratory Data Analysis
3. Data Preprocessing


