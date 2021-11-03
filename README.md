# Laporan Proyek Machine Learning - Zulfazazalia Putri Candra Wati

## Project Overview
Selama beberapa dekade terakhir, dengan munculnya Youtube, Amazon, Netflix, dan banyak layanan web sejenis lainnya, sistem pemberi rekomendasi semakin banyak mengambil tempat dalam kehidupan kita. Menurut jurnal [“Sistem REKOMENDASI BUKU MENGGUNAKAN METODE ITEM-BASED COLLABORATIVE FILTERING”](http://download.garuda.ristekdikti.go.id/article.php?article=1748276&val=1291&title=Sistem%20Rekomendasi%20Buku%20Menggunakan%20Metode%20Item-Based%20Collaborative%20Filtering) bahwa Sistem rekomendasi dapat digunakan untuk memprediksi barang tertentu yang disukai oleh pengguna atau untuk mengidentifikasi beberapa barang yang mungkin disukai oleh pengguna tertentu. Terlebih zaman yang semakin canggih menimbulkan beberapa tempat untuk mencari refrensi buku bacaan baik melalui aplikasi ataupun melihat secara langsung.

Banyaknya jumlah buku membuat pembaca terkadang kesulitan dalam menentukan buku yang hendak mereka baca selanjutnya.Terkadang dijumpai pembaca yang hanya ingin membaca buku-buku yang dengan reputasi penjualan terbaik. Ada pula pembaca yang hanya ingin membaca buku yang mirip dengan buku-buku yang pernah dibaca sebelumnya. Tidak jarang juga ditemui pembaca yang menentukan buku-buku yang akan dibaca selanjutnya berdasarkan rating dari buku-buku yang telah dilihatnya.

Oleh karena itu, Sistem rekomendasi memberikan solusi terhadap permasalahan dalam menentukan buku yang belum pernah dibaca oleh pengguna. Sehingga, pada proyek ini saya membuat rekomendasi buku yang ditujukan untuk merekomendasikan pengguna dalam memilih buku yang ingin dibaca. Pada dataset ini saya menggunakan data ‘rating’ dimana berisi informasi dari rating buku dan ‘Book’ yang berisi data-data buku. Pada rating ini terdiri dari beberapa penilaian pengguna terhadap salah satu buku dimana beberapa buku memiliki banyak penilaian rating dan beberapa buku memiliki sedikit penilaian rating oleh pengguna.

## Business Understanding

### Problem Statements
Dari kondisi diatas, maka kita dapat membuat sistem rekomendasi buku sebagai berikut:
* Berdasarkan data rating yang ada, bagaimana merekomendasikan buku lain yang mungkin di sukai pengguna dan belum pernah dibaca oleh pengguna?

### Goals
Dari pernyaatan masalah diatas maka kita dapat membuat tujuan atau goals seperti berikut:
* Menghasilkan sejumlah rekomendasi buku yang sesuai dengan preferensi pengguna dan belum pernah dibaca sebelumnya dengan teknik collaborative filtering.

### Solution approach
Berdasarkan problem statement dan goals diatas maka saya menggunakan 1 pendekatan sistem rekomendasi yaitu collaborative filtering yang digunakan untuk merekomendasikan buku yang memiliki penjelasan sebagai berikut:

* Collaborative Filtering
<br>Pada model ini merupakan salah satu metode rekomendasi yang menggunakan data rating dari seorang pengguna, dan pengguna lain untuk menghasilkan rekomendasi. Untuk model ini saya menggunakan metode deep learning dimana bekerja untuk candidate generation (pembuatan kandidat) dan menentukan ranking (peringkat). Pada model ini memiliki beberapa kelebihan yaitu bekerja dengan item atau user yang sedikit atau bahkan tidak ada serta kualitas dari prediksi yang dihasilkan akurat dan algoritma yang digunakan juga relative sederhana untuk diterapkan.<br>

## Data Understanding
Pada proyek ini saya menggunakan dataset yang tersedia pada Kaggle. Untuk Dataset ini saya menggunakan data “Books” dan “Rating”. Dikarenakan data yang terlalu banyak saya mengggunakan beberapa data dari total data yang ada seperti pada data ‘Books’ jumlah yang saya gunankan sebanyak 12.000 dan data ‘Rating’ jumlah yang saya gunakan sebanyak 12.000. Untuk variable yang ada pada dataset [Book Recommendation Dataset](https://www.kaggle.com/arashnic/book-recommendation-dataset) adalah sebagai berikut:

> Books.csv
  * ISBN: merupakan id pada buku dengan tipe data object
  * Book-Title: merupakan judul dari buku dengan tipe data object
  * Book-Author: merupakan pengarang dari buku dengan tipe data object
  * Year-Of-Publication: merupakan tahun di publikasinya buku dengan tipe data object
  * Publisher: merupakan penerbit dari buku dengan tipe data object
  * Image-URL-S: merupakan sampul gambar dari buku yang berukuran kecil dengan tipe data object
  * Image-URL-M: merupakan sampul gambar dari buku yang berukuran sedang dengan tipe data object
  * Image-URL-L: merupakan sampul gambar dari buku yang berukuran besar dengan tipe data object
  
> Rating.csv
  * User-ID: merupakan ID dari user dengan tipe data int64
  * ISBN: merupakan id pada buku dengan tipe data object
  * Book-Rating: merupakan rating yang diberikan untuk buku dengan tipe data int64

Namun untuk proyek ini saya menggabungkan kedua dataset itu menjadi satu sehingga menghasilkan sebagai berikut:

![data_train](https://user-images.githubusercontent.com/81318203/140049205-2cbf8cc8-b9b1-4f71-8e40-95f973f6cb4c.jpg)

> Untuk proyek ini saya menggunakan salah satu tahapan yaitu Teknik visualisasi data. Penjelasan serta visualisasi data akan dibahas sebagai berikut:

Pada tahap data understanding saya membuat barplot untuk tahun publikasi yang digunakan untuk melihat lonjakan terbanyak dalam publikasi buku. Seperti gambar dibawah dimana barplot ini ditampilkan dari dataset Books.csv yang tahun publikasi terbanyak ada di tahun 2002 dibandingkan dengan tahun-tahun sebelumnya.

![year](https://user-images.githubusercontent.com/81318203/140049466-657cd5d4-4b40-4aac-aea6-53a28e1bfa1d.jpg)

Kemudian untuk menampilkan 10 penulis terpopuler saya menggunakan barplot dimana menampilkan count dan nama penulis. Berikut merupakan tampilan dari barplot 10 penulis terpopuler:

![penulis](https://user-images.githubusercontent.com/81318203/140049928-605b9138-88dd-4d9a-a77e-92befe3d77e4.jpg)

Dari gambar diatas didapatkan bahwa penulis dengan nama “James Patterson” menjadi peringkat teratas pada penulis terpopuler serta peringkat dua dan peringkat ketiga berada pada penulis dengan nama “John Grisham” dan Mary Higgins Clark”. Namun bila di lihat dengan seksama penulis peringkat ketiga dan keempat memiliki jumlah yang sedikit berbeda.

Selanjutnya, saya menggunakan barplot kembali untuk menampilkan 10 publisher teratas dimana terdiri dari nama publisher dan count. Berikut ini merupakan tampilan dari barplot 10 publisher teratas:

![publisher](https://user-images.githubusercontent.com/81318203/140050099-1e9d9b84-9f5c-4401-bad5-d3d77203fa90.jpg)

Bila dilihat dari gambar diatas maka publisher yang berada di peringkat atas yaitu “Ballantine Books” dengan jumlah yang lebih banyak dibandingkan dengan publisher yang lain. Namun bila dilihat kembali pada peringkat sembilan dan sepuluh memiliki jumlah yang sama.

Terakhir, saya membuat rata-rata rating dengan buku terbanyak dibaca dimana untuk menampilkannya saya menggunakan barplot. Saat menampilkannya terdapat data “Book_Title” dan “Book_Rating”. Berikut ini hasil dari tampilan rata-rata rating dengan buku terbanyak dibaca:

![Rata2](https://user-images.githubusercontent.com/81318203/140050290-accba027-6114-495b-b0a2-38bd68a6a37c.jpg)

Pada gambar diatas didapatkan bahwa buku dengan judul “A Painted House” memiliki rating terbanyak dari pengguna dibandingkan buku yang lainnya.

## Data Preparation
Pada data preparation saya menggunakan dataset dengan nama data_books, data_rating dan gabungan dari kedua dataset yaitu data_train. Untuk preparation ini saya menggunakan beberapa teknik dengan penjelasan sebagai berikut:


