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
* Menghasilkan sejumlah rekomendasi buku yang sesuai dengan preferensi pengguna dan belum pernah dibaca sebelumnya dengan teknik *collaborative filtering.

### Solution approach
Berdasarkan problem statement dan goals diatas maka saya menggunakan 1 pendekatan sistem rekomendasi yaitu collaborative filtering yang digunakan untuk merekomendasikan buku yang memiliki penjelasan sebagai berikut:

* Collaborative Filtering
<br>Pada model ini merupakan salah satu metode rekomendasi yang menggunakan data rating dari seorang pengguna, dan pengguna lain untuk menghasilkan rekomendasi. Untuk model ini saya menggunakan metode deep learning dimana bekerja untuk candidate generation (pembuatan kandidat) dan menentukan ranking (peringkat). Pada model ini memiliki beberapa kelebihan yaitu bekerja dengan item atau user yang sedikit atau bahkan tidak ada serta kualitas dari prediksi yang dihasilkan akurat dan algoritma yang digunakan juga relative sederhana untuk diterapkan.</br>

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

1. Pengecekan data null

 ![null](https://user-images.githubusercontent.com/81318203/140051743-f16b2229-3a63-486a-9172-dce3256191be.jpg)
 
Pada gambar diatas, dilakukan pengecekan data null dengan menggunakan fungsi *isnull* dimana  terdiri dari 3 dataset yaitu data_books, data_rating dan data_train yang merupakan gabungan dari data_books dan data_rating. Bila dilihat pada gambar diatas maka data tidak memiliki null sehingga tidak perlu dilakukan teknik penghapusan data null, teknik dilakukan bila disalah satu data terdapat nilai null.

2. Pengecekan data duplikat

Selanjutnya dilakukan persiapan penghapusan data duplikat, dengan membuat variable baru dengan nama ‘data_prep’ yang berisi dataframe ‘data_train’ yang diurutkan berdasarkan ‘ISBN’. Berikut ini merupakan hasil dari persiapan penghapusan data duplikat:

![duplikat](https://user-images.githubusercontent.com/81318203/140052235-d9035e9c-dbaa-4a30-9c13-1f5a55b0df19.jpg)

Kemudian, setelah dilakukan persiapan dilanjutkan dengan penghapusan data duplikat menggunakan fungsi *drop_duplicates*. Penghapusan data duplikat berguna bila data train dan data test ada yang sama. Bila di lihat dari gambar diatas dan di bawah jumlah rows berkurang ketika dilakukan penghapusan data duplikat. Gambar dibawah ini merupakan hasil drop duplicates:

![duplikat2](https://user-images.githubusercontent.com/81318203/140052299-298a2660-534c-4e76-b6e1-28612a6fde8a.jpg)

3.	Melakukan konversi data series dan pembuatan dictionary

![isbn](https://user-images.githubusercontent.com/81318203/140054259-cc7c4459-8a65-4ed8-9a1e-c9ce0012edfe.jpg)

Pada gambar diatas dilakukan proses pengkonversian data series dalam bentuk list. Pada proses menggunakan fungsi ‘tolist()’ dari library numpy. Bila dilihat dari hasil output menampilkan jumlah dari books_id, books_title dan books_author yang memiliki jumlah yang sama yaitu 2519. Tahap berikutnya, membuat dictionary yang gunanya untuk menentukan pasangan key-value dari data books_id, books_title dan books_author seperti gambar dibawah ini.

![booknew](https://user-images.githubusercontent.com/81318203/140097162-4149a37c-0272-43f9-8951-4aae21e3ff47.jpg)

4.	Encoding Data

Setelah melakukan proses diatas maka masuk ke proses encoding data. Dimana pada proses ini digunakan untuk menyandikan (encode) fitur ke dalam indeks integer dimana fitur yang digunakan yaitu fitur ‘UserID’ dan ‘ISBN’.

 * Encoding fitur UserID
    ![user](https://user-images.githubusercontent.com/81318203/140052719-f6924832-a035-4572-bf5b-1bf6c20224b2.jpg)
<br>Pada gambar diatas merupakan output dari encode fitur ‘UserID’ dimana terdiri dari list UserID dmana list tidak memiliki nilai yang sama, encoded UserId dan encoded angka ke UserID.</br>

 * Encoding Fitur ISBN

    ![encoding2](https://user-images.githubusercontent.com/81318203/140053187-61bbaa75-f684-4c96-9ba2-88d362892a30.jpg)

<br>Untuk proses encoding fitur ISBN sama seperti proses encoding fitur UserID yang dilanjutkan dengan memetakan userID dan ISBN ke dataframe yang berkaitan seperti userID ke dataframe user dan ISBN ke dataframe book.</br>

Tahap terakhir yaitu melakukan pengecekan data seperti jumlah user, jumlah book dan mengubah nilai rating yang awalnya memiliki tipe data integer menjadi float. Pada gambar dibawah ini memiliki output jumlah user, jumlah book, minimum rating dan maksimal rating.

![book_rating](https://user-images.githubusercontent.com/81318203/140054116-6aa6a2be-fc33-4f21-855d-eb14bc612108.jpg)

5.	Membagi data untuk Training dan Validasi

Untuk tahap ini dilakukan pengacakan dataset agar distribusi yang dilakukan menjadi random. Berikut ini merupakan hasil dari tahapan tersebut:

![training](https://user-images.githubusercontent.com/81318203/140054442-9f7db809-711d-4d06-b8fd-a155f30d6899.jpg)

Kemudian, dilakukan pembagian data train dan validasi dengan komposisi 90:10 dimana perlu dipetakkan (mapping) terlebih dahulu pada data user dan book menjadi satu value. Proses ini dilakukan untuk menguji model terhadap data baru. Selanjutnya, membuat rating dalam skala 0 sampai 1 agar mudah dalam melakukan proses training.

![prosestraining](https://user-images.githubusercontent.com/81318203/140054666-0ceb4d09-953b-474f-82ee-2b6360f7204a.jpg)

## Modeling

Pada tahap ini saya menggunakan model collaborative filtering dimana menggunakan metode deep learning yang bertujuan menghasilkan rekomendasi buku.

*	Tahap awal yang dilakukan yaitu melakukan proses embedding terhadap data user dan book. Lalu dilanjutkan dengan operasi perkalian dot product antara embedding user dan book serta menambahkan bias untuk kedua data. Skor kecocokan di tetapkan dalam skala [0,1] dengan fungsi aktivasi sigmoid
*	Langkah selanjutnya dengan melakukan proses compile terhadap model yang terdiri dari loss function yang menggunakan Binary Crossentropy, optimizer yang menggunakan Adam (Adaptive Moment Estimation) dan untuk metrics evaluation yaitu root mean squared error (RMSE) kemudian dilanjutkan dengan proses training
*	Tahap akhir yaitu dengan mengambil sampel user secara acak dan definisikan variabel book_not_visited yang merupakan daftar book yang belum pernah dikunjungi oleh pengguna. Variabel book_not_visited diperoleh dengan menggunakan operator bitwise (~) pada variabel book_visited_by_user. Kemudian dalam memperoleh rekomendasi buku menggunakan fungsi model.predict() dari library Keras.

![hasil_rekomendasi](https://user-images.githubusercontent.com/81318203/140055240-f4b01338-4f91-452d-a54c-fa39403aaf95.jpg)

Pada gambar diatas merupakan hasil rekomendasi dari model collaborative filtering dimana user dengan id 508. Kita dapat melihat bahwa terdapat dua perbandingan yaitu Buku dengan peringkat tinggi dari pengguna yaitu ‘Echoes : Maeve Binchy’ dan ‘Kissing in Manhattan : DAVID SCHICKLER’ Serta 10 Rekomendasi Buku Teratas yang salah satunya yaitu ‘The Watsons Go to Birmingham - 1963 (Yearling Newbery) : CHRISTOPHER PAUL CURTIS’.

## Evaluation

Pada tahap ini saya menggunakan metrik root mean squared error (RMSE) dimana metode estimasi yang mempunyai Root Mean Square Error (RMSE) lebih kecil dikatakan lebih akurat daripada metode estimasi yang mempunyai Root Mean Square Error (RMSE) lebih besar. Rumus dari RMSE sebagai berikut:

![RMSE](https://user-images.githubusercontent.com/81318203/140055377-4d17cda4-61ab-428f-a6c7-c3bc21af551b.jpg)

Pada gambar dibawah ini merupakan hasil visualisasi metrik RMSE dari proses training yang menggunakan matplotlib. Dimana menampilkan plot root_mean_squared_error dan val_root_mean_squared_error

![grafikepoch](https://user-images.githubusercontent.com/81318203/140055633-20337bae-f0dc-42cb-ab9e-cb4391101235.jpg)

## Kesimpulan

Dari proses yang telah dilakukan didapatkan hasil perbandingan buku dengan peringkat tinggi dari pengguna dan 10 Rekomendasi Buku Teratas. Pada proyek ini saya menggunakan model Colaborative Filtering dimana menggunakan metrik Root Mean Square Error (RMSE). Serta untuk model ini data yang diperlukan dalam membuat rekomendasi yaitu data rating dari pengguna.
