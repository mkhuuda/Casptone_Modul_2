# Casptone_Modul_2

## INTRODUCTION AND PROBLEM STATEMENT

Latar Belakang:

Perusahaan Airbnb berencana untuk melakukan ekspansi dengan mendirikan properti baru di Bangkok. Untuk memastikan kesuksesan ekspansi ini, perusahaan perlu mengetahui wilayah mana yang paling tepat untuk mendirikan properti baru, jenis kamar apa yang paling diminati, dan harga optimal untuk setiap jenis kamar agar bisa mencapai profit maksimal.
Rumusan Masalah:

Bagaimana cara menentukan wilayah yang paling optimal untuk ekpansi properti baru di Bangkok?
Apa tipe kamar yang paling tepat untuk dibangun di suatu wilayah?
Berapa harga optimal untuk setiap tipe kamar agar didapatkan profit maksimal?


## DATA UNDERSTANDING

Menentukan Tabel Analisis

Berdasarkan Latar Belakang Permasalahan, Rumusan Masalah dan Data Dictionary, maka digunakan tabel yang paling relevan untuk melakukan analisis sebagai berikut:
Price
Kolom numerik ini digunakan untuk mengetahui harga kamar di masing-masing tipe kamar di wilayah tertentu. Harga juga sangat penting saat akan menentukan harga yang optimal sesuai dengan tujuan yang akan dicapai yaitu menentukan harga optimal untuk masing-masing kamar (room).
Number_of_review
Tabel numerik ini merupakan tabel yang paling relevan untuk digunakan sebagai dasar penentuan suatu kamar diminati oleh customer. Diasumsikan bahwa semakin banyak jumlah review, maka semakin banyak pula pelanggan yang tertarik menginap di kamar tersebut. Kemudian angka number_of_review ini akan dijadikan dasar dalam penentuan suatu kamar diminati oleh customer/tamu.
Room_type
Tabel kategorik ini digunakan untuk menganalisis bagaimana suatu tipe kamar diminati di wilayah tersebut. Tipe kamar memeiliki karakteristik yang berbeda sesuai yang dideskripsikan di Data Dictionary. Jika melihat ke tujuan dan rumusan masalah, maka tabel ini akan sangat penting untuk penentuan tipe kamar yang akan dibangun untuk Airbnb yang baru.
Neighbourhood
Tabel kategorik ini digunakan untuk menentukan wilayah pembangunan Airbnb baru berikutnya dengan mempertimbangkan data historis yang sudah ada. Dengan mengetahui bagaimana suatu Airbnb yang sudah berjalan sebelumnya di suatu wilayah, maka diharapkan dapat memberikan informasi sebagai dasar dalam menentukan wilayah pembangunan Airbnb yang baru.

## DATA CLEANING

Handling Missing Values

Berdasarkan Database, Missing Values hanya terdapat pada 4 kolom yaitu kolom 'last_review' , 'reviews_per_month', 'name' dan 'host_name' Berikut akan dijelaskan satu per satu untuk handling masing-masing kolom:
Kolom Last_Review dan Reviews_per_month

Terdapat 5790 data kosong untuk masing-masing kolom ini, artinya 36,52% data tidak terisi dari total baris data yang ada. Dalam hal ini dapat dilihat bahwa missing values sangat banyak dan hal yang paling tepat dilakukan adalah dengan menghapus dua kolom tersebut. Kolom dihapus dengan mempertimbangkan hal berikut:
Kepentingan Kolom: dua kolom yang memiliki banyak missing values tersebut tidak krusial untuk analisis yang ingin dilakukan, maka menghapus kolom tersebut menjadi opsi yang tepat.
Kolom yang dimaksud tidak memberikan kontribusi signifikan atau justru membuat analisis menjadi kurang efektif karena banyaknya missing values.

Dalam handling ouliers, akan fokus pada 4 tabel yang relevan digunakan untuk analisis data nantinya.

Handling Outliers di Kolom Numerik (number_of_reviews dan price)

Untuk kolom number_of_reviews dan price, akan digunakan metode Interquartile Range (IQR) untuk mendeteksi dan menangani outliers.
Interquartile Range (IQR) Method: IQR adalah metode statistik yang umum digunakan untuk mendeteksi outliers dalam data. IQR dihitung sebagai selisih antara kuartil ketiga (Q3) dan kuartil pertama (Q1). Outliers umumnya dianggap sebagai data yang berada di luar rentang berikut:
Batas bawah: Q1 - 1.5 * IQR Batas atas: Q3 + 1.5 * IQR

Handling Outliers di Kolom Kategorik (neighbourhood dan room_type)

Untuk kolom kategorik seperti neighbourhood dan room_type, tidak dicari outliers seperti di data numerik. Namun, hanya memastikan tidak ada kesalahan dalam entri atau kategori langka yang mungkin perlu penanganan khusus.

Data Bersih didapatkan melalui Data Understanding dan Data Cleaning dengan jumlah baris 12346 rows dan 10 columns/variabel untuk kemudian data ini digunakan dalam analisis.

## EXPLORATORY DATA ANALYSIS

Menentukan Wilayah yang tepat

Apakah ada Korelasi antara wilayah dan number_of_review (Analisis Korelasi 'Neighbourhood dan Number_of_review)

Menganalisis Korelasi antara neighbourhood dan number_of_review: Karena data terdistribusi tidak normal, akan digunakan uji korelasi yang ideal untuk non-parametrik yaitu Kruskal-Wallis untuk melihat apakah ada hubungan antara neighbourhood dan number_of_review.

Hasil uji Kruskal-Wallis menunjukkan nilai statistik sebesar 618.17 dan p-value yang sangat kecil (1.65e-99). Ini berarti bahwa terdapat perbedaan yang signifikan secara statistik pada harga di antara berbagai tipe kamar (room_type). Dengan p-value yang jauh lebih kecil dari tingkat signifikansi umum (misalnya, 0.05), hipotesis nol dapat ditolak bahwa median harga di antara tipe kamar adalah sama.
Penentuan wilayah yang tepat berdasarkan number_of_review

Penentuan wilayah ekspansi yang tepat akan menggunakan data neighbourhood dan number_of_reviews. Di sini akan diasumsikan bahwa number_of_review semakin banyak di suatu wilayah, maka Airbnb di wilayah tersebut semakin diminati oleh tamu.
Menentukan Wilayah berdasarkan number_of_reviews Untuk penentuan wilayah yang paling diminati berdasarkan number_of_reviews merupakan langkah yang masih relevan dan signifikan. Selain adanya korelasi tinggi setelah dilakukan uji Kruskal Wallis, memilih wilayah dengan jumlah ulasan terbanyak masih memberikan wawasan tentang area mana yang menarik perhatian lebih banyak tamu.
Alasan Mengapa Ini Signifikan:
Popularitas Wilayah: Menentukan wilayah dengan number_of_reviews terbanyak dapat memberikan informasi tentang popularitas atau daya tarik wilayah tertentu di Bangkok. Ini penting bagi bisnis untuk menargetkan wilayah-wilayah yang diminati.
Perencanaan Ekspansi: Memahami wilayah dengan aktivitas ulasan yang tinggi dapat membantu dalam perencanaan ekspansi atau investasi, terutama jika bisnis bertujuan untuk menarik lebih banyak tamu atau meningkatkan visibilitas di wilayah-wilayah tertentu.
Strategi Pemasaran: Dengan mengetahui wilayah yang paling banyak diulas, maka perusahaan pemilik properti dapat menyesuaikan strategi pemasaran mereka untuk fokus pada wilayah-wilayah ini, meningkatkan promosi, atau menyesuaikan harga.
Selanjutnya akan diambil 10 wilayah dengan tingkat popularitas tertinggi berdasarkan number_of_review sebagai alternatif dalam penentuan wilayah yang tepat. Berdasarkan data understanding variabel neighbourhood cukup banyak sehingga hanya akan diambil 10 alternatif terbaik agar penentuan wilayah semakin spesifik. Selain itu,


Menentukan 10 wilayah terbaik dengan menghitung number_of_reviews terbanyak

Berdasarkan hasil perhitungan jumlah number_of_reviews terbanyak, wilayah yang paling tepat dilakukan ekspansi adalah Khlong Toei. Kemudian untuk alternatif lain wilayah yang paling tepat adalah Vadhana, Ratchathewi, Huai Khwang, Sathon, Bang Rak, Phra Nakhon, Chatu Chak, Phra Khanong dan Din Daeng.
Artinya untuk menentukan wilayah ekpansi Aribnb baru akan optimal jika berada di 10 wilayah tersebut. Penentuan wilayah ini mungkin akan dipengaruhi oleh faktor lain di luar data yang diketahui. Namun setidaknya cukup mewakili untuk pengambilan keputusan wilayah.
Menentukan Tipe Kamar yang Tepat

Untuk menentukan tipe kamar yang tepat di wilayah yang telah dipilih, maka akan dilakukan analisis berikut:
Langkah-langkah Analisis Penentuan Tipe Kamar


Mengumpulkan Data Tipe Kamar: Fokus pada data yang berkaitan dengan room_type dan price untuk wilayah yang terpilih.
Analisis Harga Berdasarkan Tipe Kamar:
Menghitung rata-rata harga per tipe kamar untuk setiap wilayah. Menilai variasi harga per tipe kamar untuk memahami rentang harga yang mungkin diterima oleh pasar di wilayah tersebut.
Analisis Popularitas Tipe Kamar: Menghitung jumlah ulasan per tipe kamar untuk masing-masing wilayah. Menilai tipe kamar yang paling banyak diulas atau paling sering dibooking untuk setiap wilayah.
Analisis Korelasi Tipe Kamar dengan Jumlah Ulasan: Menggunakan uji statistik atau visualisasi untuk melihat apakah tipe kamar tertentu memiliki hubungan yang signifikan dengan jumlah ulasan.
Visualisasi Data: Membuat visualisasi seperti bar plot atau box plot untuk membandingkan harga dan jumlah ulasan antara tipe kamar di wilayah terpilih.
Mengumpulkan Data Tipe Kamar

Berdasarkan data wilayah terpilih, maka analisis berikutnya akan ditentukan data dari top 10 wilayah paling tepat. Kemudian dataframe akan diubah ke variabel df_cleaned_neighbourhoods.

Hasil uji Kruskal-Wallis menunjukkan statistik uji sebesar 481.414 dan p-value sebesar 5.084956612908748e-104. Berikut adalah interpretasi hasil tersebut:
Interpretasi Hasil Uji Kruskal-Wallis:
Statistik Uji (Kruskal-Wallis H Test Statistic = 481.414): Nilai statistik uji yang besar ini mengindikasikan bahwa ada perbedaan yang signifikan antara grup-grup yang diuji. Semakin besar nilai statistik uji Kruskal-Wallis, semakin besar kemungkinan adanya perbedaan di antara grup-grup.
P-value (5.084956612908748e-104):
P-value yang sangat kecil (lebih kecil dari 0.05, bahkan jauh lebih kecil dari 0.01) menunjukkan bahwa perbedaan di antara grup-grup tersebut adalah sangat signifikan secara statistik.
Dalam konteks ini, dapat menolak hipotesis nol (H0) yang menyatakan bahwa tidak ada perbedaan median yang signifikan antara grup-grup yang diuji.
Kesimpulan: Perbedaan Signifikan: Hasil ini menunjukkan bahwa ada perbedaan yang sangat signifikan dalam distribusi harga antara tipe kamar yang berbeda (room_type), berdasarkan harga (price). Artinya, median harga di antara tipe kamar berbeda secara signifikan.


Analisis Popularitas Tipe Kamar


Berdasarkan Bar Plot yang telah dibuat, dapat dilihat bahwa Entire home/apt menjadi tipe kamar yang paling populer dilihat dari jumlah ulasannya. Kemudian diikuti tipe Private room, hotel room dan shared room.

Penentuan Tipe Kamar yang Tepat

Berdasarkan Popularitas kamar dan Bar Plot yang telah dibuat, dapat dilihat bahwa Entire home/apt menjadi tipe kamar yang paling populer dilihat dari jumlah ulasannya. Kemudian alternatif lain yang paling populer adalah Private room, diikuti hotel room dan shared room.
Perusahaan seharusnya melakukan ekspansi di wilayah terpilih dengan memprioritaskan tipe kamar Entire home/apt. Namun jika menginginkan adanya variasi, maka private room dapat menjadi pilihan berikutnya diikuti dengan hotel room dan shared room sebagai pilihan terkahir.
Menentukan Harga yang Optimal

Deskriptif Statistik Harga


Uji Signifikansi Harga

Sebelum melakukan uji signifikasi harga, perlu melakukan uji normalitas terhadap data yang sudah di cleaning untuk menentukan uji normalitas yang sesuai.


**Berdasarkan hasil uji normalitas data yang sudah dibersihkan ouliers nya, data masih terdistribusi tidak normal, maka uji Kruskal-Wallis menjadi pilihan yang tepat untuk melihat apakah ada perbedaan signifikan untuk harga di masing-masing kamar.**


Hasil uji Kruskal-Wallis menunjukkan statistik uji sebesar 983.761 dan p-value sebesar 5.994631309946457e-213.
Interpretasi Hasil Uji Kruskal-Wallis:
Statistik Uji (Kruskal-Wallis H Test Statistic = 983.761):
Nilai statistik uji yang sangat besar ini menunjukkan bahwa terdapat perbedaan yang signifikan antara grup-grup yang diuji. Semakin besar nilai statistik uji Kruskal-Wallis, semakin besar kemungkinan adanya perbedaan di antara grup-grup tersebut.
P-value (5.994631309946457e-213):
P-value yang sangat kecil (bahkan jauh lebih kecil dari 0.05) menunjukkan bahwa hasil ini sangat signifikan secara statistik. Dengan p-value sebesar ini, kita dapat dengan sangat yakin menolak hipotesis nol (H0) yang menyatakan bahwa tidak ada perbedaan median yang signifikan antara grup-grup yang diuji. Dengan kata lain, ada bukti yang sangat kuat bahwa setidaknya satu pasang grup memiliki perbedaan median yang signifikan.
Kesimpulan:
Perbedaan Signifikan: Hasil ini menunjukkan bahwa terdapat perbedaan yang sangat signifikan dalam distribusi harga di antara berbagai tipe kamar (room_type) berdasarkan harga (price). Artinya, median harga berbeda secara signifikan di antara tipe kamar yang diuji.
Analisis Harga berdasarkan tipe kamar

Menentukan Harga Optimal Masing-Masing Tipe Kamar

Data terdistibusi tidak normal, sehingga penggunaan median sebagai sentral tendency menjadi pilihan yang tepat.


Menentukan Rentang Harga yang Optimal

Rentang harga yang signifikan dapat ditentukan sebagai kuartil pertama (25%) hingga kuartil ketiga (75%). Ini adalah rentang di mana sebagian besar data berada dan biasanya dianggap representatif karena tidak dipengaruhi oleh outliers.


Berdasarkan analisis penentuan harga yang optimal didapatkan hasil harga untuk masing-masing tipe kamar dalam dollar, sebagai berikut: 1. Shared Room: Harga optimal di 486 dengan rentang harga optimal di 390 hingga 550 2. Private Room: Harga optimal di 1282 dengan rentang harga optimal di 890 hingga 1990 3. Entire room/apt: Harga optimal di 1543 dengan rentang harga optimal di 1097,5 hingga 2277 4. Hotel room: Harga optimal di 1600 dengan rentang harga optimal di 984 hingga 2583



## KESIMPULAN DAN REKOMENDASI

Kesimpulan

Berdasarkan data understanding, data cleaning dan analisis data yang dilakukan, maka dapat disimpulkan:
Dari data 'Airbnb Listings Bangkok.csv', digunakan empat variabel yang relevan untuk dilakukan analisis data berdasarkan rumusan masalah dan tujuan yang akan dicapai yaitu: price, number_of_reviews, neighbourhood, dan room_type.
Data Bersih didapatkan melalui Data Understanding dan Data Cleaning dengan jumlah baris 12346 rows dan 10 columns/variabel untuk kemudian data ini digunakan dalam analisis.
Berdasarkan hasil analisis data dengan menggunakan variabel 'neighbourhood' dan 'number_of_reviews' didapatkan hasil wilayah yang tepat untuk dilakukan ekspansi Airbnb baru yaitu Khlong Toei, kemudian diikuti dengan Vadhana, Ratchathewi, Huai Khwang, Sathon, Bang Rak, Phra Nakhon, Chatu Chak, Phra Khanong dan Din Daeng.
Tipe Kamar yang paling tepat berdasarkan popularitas kamar dan Bar Plot yang telah dibuat adalah Entire home/apt, kemudian alternatif lain yang paling populer adalah Private room, diikuti hotel room dan shared room.
Harga optimal dan rentang harga optimal untuk masing-masing tipe kamar dalam dollar adalah: Shared Room: harga di 486 dan rentang harga di 390-550, Private Room: harga di 1282 dan rentang harga di 890-1990, Entire room/apt: Harga di 1543 dan rentang harga optimal di 1097,5 hingga 2277 serta Hotel room: Harga di 1600 dengan rentang harga di 984-2583.
Rekomendasi

Berdasarkan analisis dan kesimpulan yang didapatkan, maka dapat diberikan rekomendasi untuk Perusahaan Airbnb yang akan melakukan ekspansi properti baru sebagai berikut:
Wilayah yang paling tepat dilakukan ekspansi adalah Khlong Toei, kemudian untuk alternatif lain wilayah yang paling tepat adalah Vadhana, Ratchathewi, Huai Khwang, Sathon, Bang Rak, Phra Nakhon, Chatu Chak, Phra Khanong dan Din Daeng. Artinya untuk menentukan wilayah ekpansi Aribnb baru akan optimal jika berada di 10 wilayah tersebut. Penentuan wilayah ini mungkin akan dipengaruhi oleh faktor lain di luar data yang diketahui.
Perusahaan seharusnya melakukan ekspansi di wilayah terpilih dengan memprioritaskan tipe kamar Entire home/apt. Namun jika menginginkan adanya variasi, maka private room dapat menjadi pilihan berikutnya diikuti dengan hotel room dan shared room sebagai pilihan terkahir.
Berdasarkan analisis penentuan harga yang optimal didapatkan hasil harga untuk masing-masing tipe kamar dalam dollar, sebagai berikut:
a. Shared Room: Harga optimal di 486 dengan rentang harga optimal di 390 hingga 550
b. Private Room: Harga optimal di 1282 dengan rentang harga optimal di 890 hingga 1990
c. Entire room/apt: Harga optimal di 1543 dengan rentang harga optimal di 1097,5 hingga 2277
d. Hotel room: Harga optimal di 1600 dengan rentang harga optimal di 984 hingga 2583



