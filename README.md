# Laporan Proyek 1 Machine Learning Terapan - Fadhillah Akmal

## Domain Proyek

Harga tiket pesawat pada saat ini memiliki perubahan harga yang dinamis, dimana maskapai penerbangan mengubah harga untuk memaksimalkan profit berdasarkan faktor-faktor tertentu [[1](https://dl.acm.org/doi/abs/10.1145/956750.956767)]. Hal ini menyebabkan banyak konsumen yang berstrategi dalam membeli harga tiket pesawat untuk mendapatkan harga paling rendah [[2]( https://www.sciencedirect.com/science/article/pii/S131915781830884X)]. 
Prediksi harga yang dinamis ini akan dapat membantu konsumen dalam menghemat uang mendapatkan tiket yang terjangkau.

Terdapat beberapa faktor-faktor yang berpengaruh pada tiket pesawat. Contohnya seperti maskapai penerbangan itu sendiri, kota tujuan, jumlah pemberhentian, waktu keberangkatan, waktu tiba, dan waktu penerbangan [[3](https://www.atlantis-press.com/proceedings/icemed-22/125975408)]. Dengan menggunakan dataset yang memiliki beberapa variabel ini, maka harga tiket pesawat dapat diestimasi dengan mempertimbangkan korelasi antar faktor-faktor tersebut.

Prediksi harga tiket pesawat ini dapat dilakukan menggunakan berbagai teknik mulai dari teknik statistik seperti regresi hingga menggunakan teknik *machine learning* [[4](https://arxiv.org/abs/1705.07205)] [[5](https://dergipark.org.tr/en/pub/veri/issue/64538/962789)] *Machine learning* dipilih untuk menyelesaikan masalah ini karena kemampuannya dalam menangani pola yang kompleks dan perubahan dinamis dalam data. Di mana sebuah model yang telah dilatih untuk memprediksi harga tiket pesawat dapat membantu konsumen dalam memesan tiket dengan harga yang optimum.


---
## Business Understanding

Model *machine learning* dalam memprediksi harga tiket pesawat dapat memiliki manfaat pada konsumen atau industri penerbangan dalam mengambil keputusan. Prediksi harga tiket pesawat yang akurat dapat membantu konsumen mendapatkan harga tiket yang terjangkau. 

### Problem Statements

Berdasarkan kondisi yang telah dibahas sebelumnya, permasalahan yang akan diselesaikan adalah sebagai berikut :
- Apa saja fitur-fitur yang paling berpengaruh terhadap harga tiket pesawat ?
- Berapakah harga tiket pesawat dengan kriteria tertentu ?
- Apa model *machine learning* yang paling cocok digunakan dalam menentukan harga tiket pesawat ? 

### Goals

Untuk menjawab permasalahan diatas, maka akan dibuat sebuah sistem prediksi dengan tujuan sebagai berikut:
- Mengetahui fitur-fitur yang paling berpengaruh terhadap harga tiket pesawat dengan melakukan *exploratory data analysis*.
- Membuat model *machine learning* yang dapat memprediksi harga tiket pesawat berdasarkan fitur-fitur yang ada.
- Membandingkan beberapa model *machine learning* berdasarkan metrik tertentu untuk medapatkan model yang paling akurat.

### Solution statements

Untuk mencapai tujuan diatas, maka berikut hal yang akan dilakukan pada pengembangan sistem prediksi harga tiket pesawat :
- Melakukan *exploratory data analysis* untuk mengetahui fitur-fitur yang berpengaruh pada harga tiket menggunakan teknik analisis univariat dan multivariat.
- Menggunakan beberapa algoritma model *machine learning* yaitu *K-nearest neighbor*, *random forest*, *adaptive boosting*, dan *XGBoost* (*extreme gradient boosting*).
- Mengukur performa model menggunakan beberapa metrik evaluasi yaitu $MSE$ , $R^2$ , dan $MAPE$ .

---
## Data Understanding

Data yang digunakan dalam pengembangan sistem prediksi pada proyek ini merupakan hasil ekstraksi halaman web *Ease My Trip* yang merupakan penyedia pemesanan tiket perjalanan. Data didapatkan untuk pemesanan tiket pesawat pada 6 kota metropolis di India. Data yang telah diekstraksi kemudian dirapihkan menjadi data tabular berdasarkan opsi pemesanan tiket pada web *Ease My Trip*.

Jumlah data pada dataset berjumlah 300261 sampel data, dengan 11 fitur variabel. 

Sumber dataset : https://www.kaggle.com/datasets/shubhambathwal/flight-price-prediction

### Variabel-variabel pada dataset
- Airline: Nama maskapai penerbangan, terdapat 6 maskapai pada dataset ini
- Flight: Variabel yang menyimpan nomer penerbangan. Format dari nomer ini terdiri dari dua huruf yang menunjukan kode maskapai, dan nomer spesifik untuk mengidentifikasi penerbangan tersebut. Data ini berjenis data kategori.  
- Source City: Variabel yang menyimpan data kota asal penerbangan, terdapat 6 kota asal pada dataset ini
- Departure Time: Variabel ini menyimpan informasi mengenai waktu keberangkatan penerbangan. Data ini dalam bentuk fitur kategori dengan membagi data dalam 6 rentang waktu.
- Stops: Variabel ini menyimpan informasi mengenai jumlah pemberhentian antara kota asal dengan kota tujuan saat penerbangan. Data ini dikategorikan sebagai tanpa adanya pemberhentian, satu pemberhentian, dan dua atau lebih perberhentian.
- Arrival Time: Variabel ini menyimpan informasi mengenai waktu tiba penerbangan. Data ini dalam bentuk fitur kategori dengan membagi data dalam 6 rentang waktu.
- Destination City: Variabel yang menyimpan data kota tujuan penerbangan, terdapat 6 kota tujuan.
- Class: Informasi mengenai kelas tempat duduk dari penumpang. Terdapat dua kelas, yaitu kelas ekonomi (*Economy*) dan bisnis (*business*)
- Duration: Fitur yang menunjukan lamanya durasi penerbangan. Data dihitung dalam satuan jam.
- Days Left: Variabel ini menyimpan informasi waktu selang antara pemesanan tiket dengan waktu keberangkatan. Data dihitung dalam satuan hari.
- Price: Variabel yang menyimpan informasi harga dari tiket pesawat. Data ini disimpan dalam format integer.

### Exploratory Data Analysis

Proses selanjutnya adalah melakukan analisis data dengan menggunakan metode *exploratory data analysis*. Teknik analisis data yang digunakan adalah dengan melakukan analisis univariat dan analisis multivariat yang didukung dengan visualisasi data.

Analisis univariat merupakan teknik analisis data yang berfokus pada satu variabel pada satu waktu. Teknik ini dilakukan untuk mengetahui distribusi dan frekuensi data dari suatu dataset. Visualisasi data yang dilakukan menggunakan catplot() untuk data kategori dan histogram untuk data numerik. Hal ini dilakukan untuk mengetahui distribusi data dari setiap fitur.

Berikut hasil analisis univariat terhadap seluruh fitur kategori pada dataset tervisualisasi di Gambar 1 hingga Gambar 8. 

![download](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/8a0ac850-f69f-4401-8dfa-eb81360662f5)

Gambar 1. Analisis Univariat untuk Kategori 'airline'

![download (1)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/9f07cdb8-35a4-40db-bd7f-d77cd0682f1b)

Gambar 2. Analisis Univariat untuk Kategori 'flight'

![download (2)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/e76b3cff-73df-45df-8aca-890ef57a6489)

Gambar 3. Analisis Univariat untuk Kategori 'source_city'

![download (3)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/61b73a4b-5ff6-4add-8e26-1e117966cbbb)

Gambar 4. Analisis Univariat untuk Kategori 'departure_time'

![download (4)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/bd163fbb-243f-4a02-9f1b-8d1967dd2dd3)

Gambar 5. Analisis Univariat untuk Kategori 'stops'

![download (5)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/4116f6d3-3ba2-4de0-893d-8a2b8291c1cc)

Gambar 6. Analisis Univariat untuk Kategori 'arrival_time'

![download (6)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/9b7a7c7c-60d1-4b97-946e-514c42f1e6dc)

Gambar 7. Analisis Univariat untuk Kategori 'destination_city'

![download (7)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/7bb26c3d-5cc8-4898-9911-aa8ef679939f)

Gambar 8. Analisis Univariat untuk Kategori 'class'

Dari plot grafik fitur kategori pada Gambar 1 hingga Gambar 8, dapat diketahui bahwa :

- Dari 6 kategori 'airline' dapat ditunjukan maskapai paling banyak pada dataset adalah maskapai Vistara dengan 42.6%
- Terdapat 1561 nomor penerbangan berbeda yang terdata pada dataset. Data menunjukan bahwa penerbangan kode maskapai UK memiliki jumlah penerbangan paling banyak, dengan nomer penerbangan UK-706 memiliki 3116 penerbangan. Dataset ini memiliki jumlah kategori yang sangat banyak dibandingkan kategori lainnya dengan distribusi yang tidak merata. Beberapa kategori hanya memiliki 1 sampel.
- Dari ke enam kota asal penerbangan, mayoritas penerbangan berasal dari kota Delhi dan Mumbai.
- Dari 6 rentang waktu keberangkatan penerbangan, jumlah penerbangan paling banyak terjadi pada waktu pagi hari.
- Dari jumlah pemberhentian, mayoritas penerbangan akan melakukan satu pemberhentian.
- Waktu tiba penerbangan mayoritas pada waktu sore hingga malam.
- Kota tujuan penerbangan mayoritas bertuju ke kota Mumbai dan Delhi.
- Mayoritas sampel sebanyak 68.9 % merupakan tiket yang dipesan merupakan tiket kelas ekonomi.

Berikut hasil analisis univariat terhadap seluruh data numerik pada dataset tervisualisasi di Gambar 9.

![download (9)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/024a5df7-4355-4767-93e5-f860168fa6df)

Gambar 9. Analisis Univariat untuk Data Numerik

Dari histogram fitur numerik yang terdapat pada Gambar 9, dapat diketahui bahwa :  

- Peningkatan harga tiket pesawat berhubungan dengan penurunan jumlah sampel.  
- Sampel data tiket pesawat mayoritas berada pada harga dibawah 15000.
- Distribusi data cenderung miring ke kanan (right-skewed) dengan distribusi yang tidak simetris. Hal ini akan berimplikasi pada model

Analisis selanjutnya adalah analisis multivariat. Analisis data ini merupakan teknik analisis yang melibatkan beberapa variabel pada satu waktu. Teknik ini dilakukan untuk mengetahui hubungan dan pola antara satu variabel dengan variabel lainnya. Visualisasi data dilakukan menggunakan catplot() untuk data kategori, pairplot serta heatmap untuk data numerik. Hal ini dilakukan untuk mengetahui korelasi antara fitur terhadap target label.

Berikut hasil analisis multivariat terhadap seluruh fitur kategori pada dataset tervisualisasi di Gambar 10 hingga Gambar 17.

![download (10)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/03c0cc51-7592-496a-88fa-703511b44cb0)

Gambar 10. Grafik Nilai Rata-Rata 'price' terhadap Kategori 'airline'

![download (17)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/e7a27515-c521-4952-89a0-fc017e6e3a7f)

Gambar 11. Grafik Nilai Rata-Rata 'price' terhadap Kategori 'flight'

![download (11)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/b43fe1a7-69d3-4cab-bdac-2be4b614e9e9)

Gambar 12. Grafik Nilai Rata-Rata 'price' terhadap Kategori 'source_city'

![download (12)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/292db664-bbc2-4cf7-bd2d-0f0d1c0d8717)

Gambar 13. Grafik Nilai Rata-Rata 'price' terhadap Kategori 'departure_time'

![download (13)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/513c5f3e-3175-4c17-949b-165aa582e63b)

Gambar 14. Grafik Nilai Rata-Rata 'price' terhadap Kategori 'stops'

![download (14)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/78c8e3fe-0461-4f0f-a363-e28c2b244ce6)

Gambar 15. Grafik Nilai Rata-Rata 'price' terhadap Kategori 'arrival_time'

![download (15)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/3f32d414-f5bb-4a1a-a688-73b705332fcf)

Gambar 16. Grafik Nilai Rata-Rata 'price' terhadap Kategori 'destination_city'

![download (16)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/d59433e3-0e46-4a5b-8879-71adad40deaf)

Gambar 17. Grafik Nilai Rata-Rata 'price' terhadap Kategori 'class'

Hasil pengamatan pada nilai rata-rata 'price' terhadap fitur kategori dapat diketahui informasi sebagai berikut :

- Dari fitur 'airline', terlihat bahwa maskapai Vistara dan Air India memiliki rata-rata harga tiket yang lebih tinggi dibandingkan dengan maskapai lainnya. Hal ini menandakan kategori ini memiliki pengaruh terhadap harga
- Dari fitur 'source_city', rata-rata harga tiket berada di sekitar harga 20000. Hal ini menandakan kategori ini memiliki pengaruh yang rendah terhadap harga.
- Dari fitur 'departure_time', waktu 'late_night' memiliki rata-rata harga yang lebih rendah dibandingkan waktu lainnya.
- Dari fitur 'stops', terlihat bahwa jumlah pemberhentian memiliki rata-rata nilai yang berbeda satu sama lainnya. 'one' atau satu pemberhentian memiliki rata-rata harga tertinggi.
- Dari fitur 'arrival time', 3 waktu memiliki rata-rata nilai diatas harga 20000 dengan 3 waktu lainnya berada dibawah 20000. 'late_night' menjadi waktu tiba dengan nilai rata-rata terendah.
- Dari fitur 'destination_city', rata-rata harga tiket berada di sekitar rentang 20000. Hal ini menandakan kategori ini memiliki pengaruh yang rendah terhadap harga.
- Dari fitur 'class', terlihat bahwa harga rata-rata dari kelas ekonomi dan bisnis memiliki perbedaan yang sangat berbeda. Hal ini menandakan kategori ini sangat berpengaruh terhadap harga.
- Dari fitur 'flight', karena jumlah kategori yang sangat banyak, maka hanya dapat ditampilkan 10 penerbangan yang terbanyak. Nilai rata-rata 'price' menurun seiring jumlah penerbangan.

Terlihat dari hasil pengamatan bahwa fitur kategori memiliki pengaruh terhadap target label 'price'

Berikut hasil analisis multivariat terhadap seluruh fitur numerik pada dataset tervisualisasi di Gambar 18 dan Gambar 19.

![download (18)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/3d8073d6-4c2a-4c83-81fe-50a9afbcdadd)

Gambar 18. Grafik pairplot() antara Fitur Target 'price' terhadap Fitur Numerik

![download (19)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/2d15c33c-ec1d-46b8-a336-ea44438663e5)

Gambar 19. Matriks Korelasi antar Fitur Numerik dengan Fitur 'price'

Pada grafik pada Gambar 18, hubungan antara 'price' dengan fitur numerik lainnya tidak membentuk pola yang jelas, menandakan korelasi yang lemah. Korelasi dapat dievaluasi menggunakan koefisien korelasi. Nilai koefisien ini adalah dari -1 hingga 1. Nilai koefisien ini digunakan untuk mengetahui hubungan antar dua variabel, dimana nilai -1 atau 1 menandakan korelasi yang kuat, sedangkan nilai 0 menandakan tidak ada nya korelasi sama sekali. 

Pada matriks korelasi di Gambar 19, dapat terlihat bahwa fitur 'duration' dan 'days_left' memiliki nilai koefisien yang rendah, yaitu 0.22 dan -0.09. Hal ini menunjukan korelasi yang lemah antara dua variabel tersebut terhadap nilai 'price'. Fitur 'days_left' memiliki nilai korelasi yang sangat kecil yang dapat diasumsikan tidak memiliki hubungan terhadap 'price'

Dari fitur kategori, terdapat fitur 'source_city' dan 'destination_city' yang memiliki pengaruh rendah terhadap nilai 'price'. Fitur numerik 'duration' dan 'days_left' memiliki koefisien korelasi yang kecil terhadap nilai 'price'. Walau fitur-fitur ini memiliki korelasi yang lemah, namun fitur ini akan dipertahankan dikarenakan masih memiliki korelasi terhadap nilai 'price'.

Fitur 'airline' memiliki jumlah kategori yang sangat banyak yang tidak efisien untuk diproses model. Maka fitur 'airline' akan dihapus dari dataset.

---
## Data Preparation

Preparasi data merupakan tahapan yang dilakukan untuk mempersiapkan dataset sebelum dimasukan ke proses pemodelan. Tahapan ini melakukan transformasi pada data agar memiliki bentuk yang cocok ketika dimodelkan nanti. Proses preparasi data yang dilakukan pada bagian ini yaitu :

- *Data cleaning*
- *Encoding* fitur kategori
- Pembagian dataset
- Standarisasi

### *Data Cleaning*

Dataset yang telah diimport kemudian akan dicek beberapa hal, yaitu : data duplikat, data yang hilang, serta data outlier. 

Dalam dataset ini tidak ditemukannya data duplikat atau data yang hilang. Data outlier pada dataset diproses dengan melakukan *dropping* atau menghapus sejumlah sampel data. Identifikasi data outlier menggunakan metode *Interquartile Range* (IQR).

Metode IQR dilakukan dengan menghitung nilai IQR dengan cara : 

$$IQR = Q3 - Q1$$

dengan IQR merupakan *interquartile range*, Q3 adalah kuartil ketiga dari dataset, dan Q1 adalah kuartil pertama dari dataset. Setelah nilai IQR diketahui, dihitung batas atas dan batas bawah dari dataset dimana data yang berada di luar rentang batas ini diidentifikasi sebagai outlier. Perhitungan batas atas dan bawah dapat dihitung sebagai berikut :

- Batas atas : $Q_1 - 1.5 \cdot IQR$

- Batas bawah : $Q_3 + 1.5 \cdot IQR$

Setelah mengidentifikasi data outlier dan melakukan *dropping* data. Jumlah dataset berkurang dari 300261 sampel data menjadi 297920 sampel data. 

### *Encoding* data kategori

Proses *encoding* adalah proses mengubah data dari satu bentuk menjadi bentuk lainnya. Proses ini dilakukan untuk mengubah data fitur kategori yang masih berbentuk text menjadi data numerik yang dapat diproses pada pelatihan nantinya.

Salah satu metode *encoding* adalah menggunakan metode *label encoding*. Metode ini merubah setiap nilai kategori menjadi nilai numerik yang unik. Contohnya adalah merubah fitur kategori 'departure_time', seperti 'morning' menjadi 1, 'afternoon' menjadi 2, dan seterusnya. Proses ini dilakukan menggunakan LabelEncoder() dari pustaka scikit-learn.

### Pembagian Dataset

Selanjutnya adalah proses pembagian dataset. Proses ini dilakukan untuk membagi dataset menjadi data latih (*training*) dan data uji (*test*). Proses ini dilakukan untuk menyimpan sebagian data untuk menguji model selain dari data yang digunakan ketika pelatihan. Pemisahan ini memastikan bahwa pengujian model dilakukan dengan data baru yang tidak pernah dilihat model sebelumnya. Pembagian dataset dilakukan dengan proporsi 90 % data pelatihan dan 10 % data uji.

### Standarisasi

Proses standarisasi merupakan tahapan yang dilakukan untuk menyeragamkan nilai-nilai pada fitur. Beberapa algoritma *machine learning* seperti regresi linear sangat sensitf terhadap perbedaan skala pada dataset. Proses ini juga akan membuat pemodelan algoritma lebih cepat serta meningkatkan kinerja model.

Proses standarisasi yang digunakan adalah StandardScaler. Teknik ini mamastikan dataset dapat seragam dengan mengubah nilai variabel pada dataset agar memiliki rata-rata (mean) senilai nol dan standar deviasi senilai satu. Hal ini dilakukan dengan cara menghitung mean dan standar deviasi dari setiap fitur, kemudian nilai setiap fitur akan dikurangi dengan mean fitur dan dibagi oleh standar deviasi fitur.

---
## Modeling

Berdasakan kasus prediksi harga tiket pesawat, salah satu algoritma yang umum digunakan untuk membuat model prediksi adalah regresi. Regresi merupakan metode statistik yang digunakan untuk memodelkan hubungan antara satu atau lebih variabel independen dengan satu variabel dependen. Tujjuan pemodelan tersebut adalah untuk memprediksi nilai variabel dependen berdasarkan nilai variabel independen. Bentuk persamaan regresi yang sederhana adalah sebagai berikut :

$$y = ax + b$$
Dengan $y$ adalah variabel dependen, $a$ adalah koefisien regresi, $x$ adalah variabel indepeden, dan $b$ adalah intersep (nilai yang berpotongan dengan sumbu Y).

Pada proyek ini, terdapat empat algoritma regresi *machine learning* yang dibandingkan untuk mendapatkan prediksi harga tiket paling mendekati harga sebenarnya. Algoritma yang digunakan adalah sebagai berikut :

- K-Nearest Neighbor (KNN)
  
	Algoritma KNN merupakan algoritma sederhana yang memprediksi nilai dengan cara membandingkan data prediksi terhadap data latihnya. Hal ini dilakukan membandingkan jarak satu sampel ke sampel lainnya dengan memilih sejumlah tetangga terdekat.
	
	Kelebihan dari algoritma ini adalah bentuk model yang sederhana dan tidak memerlukan pelatihan.
	
	Kekurangan dari algoritma ini adalah perlunya kemampuan komputasi yang besar ketika ingin memprediksi pada dataset yang besar serta memiliki peforma yang buruk ketika fitur tidak berada pada skala yang sama . 
	
- Random Forest
  
	Algoritma *random forest* adalah algoritma *supervised learning* yang dapat menyelesaikan kasus klasifikasi atau regresi. Model ini dapat memprediksi nilai dengan kumpulan algoritma *decision tree* yang hasil prediksinya akan dirata-ratakan sebagai prediksi akhir.
	
	Kelebihan dari algoritma ini adalah performanya yang baik untuk berbagai macam  kasus, termasuk dengan regresi. Algoritma ini juga lebih baik dalam memproses dataset banyak dimensi
	
	Kekurangan dari algoritma ini adalah cukup lambat dalam memprediksi apabila dengan  jumlah *decision tree* yang banyak, serta tidak baik dalam melakukan ekstrapolasi.
	
- Adaptive Boosting
  
	Algoritma ini merupakan model ensembel menggunakan serangkaian model dengan prediksi yang lemah (seringkali *decision tree*) dan menggabungkan prediksi model-model tersebut menjadi prediksi yang lebih akurat.
	
	Kelebihan dari algoritma ini adalah akurasi yang tinggi dengan model yang sederhana serta dapat memproses data yang memiliki *noise* dan outlier
	
	Kekurangan dari algoritma ini adalah sensitif denga jumlah iterasi pelatihan. Algoritma  ini juga memiliki pelatihan yang lambat. 
	
- Extreme Gradient Boosting (XGBoost)
  
	Algoritma XGBoost adalah algoritma yang menggunakan metode *gradient boosting* untuk mendapatkan hasil prediksi akhir. Algoritma ini secara sekuen menambahkan model (*tree*) untuk memperbaiki error yang dibuat ketika pelatihan. Algoritma ini merupakan pendekatan yang cukup populer dalam penyelesaian kasus klasifikasi ataupun regresi.
	
	Kelebihan algoritma ini adalah pelatihan model yang lebih cepat dengan proses paralel dan dapat memproses data yang hilang.
	
	Kekurangan dari algoritma ini adalah perlunya penentuan hyperparameter yang baik untuk menghindari overfit. 

Pembuatan model dilakukan dengan parameter sebagai berikut :

- KNN

```python
knn = KNeighborsRegressor(n_neighbors=50)
```

Parameter yang ditentukan pada algoritma KNN adalah 'n_neighbors' yaitu nilai tetangga yang akan dipertimbangkan oleh model.

- Random Forest

```python
RF = RandomForestRegressor(n_estimators=100, max_depth=25, random_state=123, n_jobs=-1)
```

Parameter yang ditentukan pada algoritma ini adalah 'n_estimators' untuk menentukan jumlah *decision tree* yang digunakan pada model. Parameter 'max_depth' digunakan untuk menentukan kedalaman maksimum dari setiap pohon keputusan. 'random_state' digunakan untuk mendapatkan keadaan model yang sama ketika dilatih.

- Adaptive Boost

```python
boosting = AdaBoostRegressor(n_estimators = 100, learning_rate=0.05, random_state=123)
```

Pembuatan model ini menggunakan parameter 'n_estimators' untuk menentukan jumlah *decision tree* sebagai model prediksi lemah yang digunakan pada model.'learning_rate' sebesar 0.05 untuk mengontrol kecepatan belajar model. 'random_state' digunakan untuk mendapatkan keadaan model yang sama ketika dilatih.


- XGBoost

```python
xgb = xgboost.XGBRegressor(n_estimators = 100, learning_rate=0.05, random_state=123)
```

Pembuatan model XGBoost tidak menggunakan parameter 'n_estimators' untuk menentukan jumlah *decision tree* sebagai model prediksi lemah yang digunakan pada model.'learning_rate' sebesar 0.05 untuk mengontrol kecepatan belajar model. 'random_state' digunakan untuk mendapatkan keadaan model yang sama ketika dilatih.

---
## Evaluation

Metrik evaluasi yang akan digunakan adalah metrik *mean square error* (MSE), $R^2$ , dan *mean absolute percentage error* (MAPE). Berikut persamaan dari setiap metrik evaluasi :
$$MSE = \frac{1}{n} \sum (y_i - \hat{y}_i)^2$$
$$R^2 = 1 - \frac{\sum (y_i - \hat{y}_i)^2}{\sum(y_i - \bar{y})^2}$$
$$MAPE = \frac{1}{n} \sum |\frac{y_i - \hat{y_i}}{y_i}|$$
Dengan $n$ merupakan jumlah data, $y_i$ adalah nilai sebenarnya dari target label, $\hat{y_i}$ adalah nilai prediksi model, dan $\bar{y}$ adalah rata-rata dari nilai label. 

MSE merupakan metrik umum dalam mengevaluasi performa model regresi. Metrik ini menghitung rata-rata dari perbedaan nilai sebenarnya dengan nilai prediksi yang dikuadratkan. Nilai MSE yang kecil menandakan performa model yang baik.

$R^2$ merupakan metrik yang menunjukan proporsi varian antara variabel dependen dengan variabel independen pada model. Nilai $R^2$ memiliki rentang dari 0 hingga 1, dimana nilai 1 menunjukan model memiliki prediksi yang mendekati aslinya dan 0 menunjukan performa model yang buruk.

MAPE merupakan metrik yang digunakan untuk menghitung rata-rata perbedaan antara nilai prediksi dengan nilai sebenarnya. Nilai MAPE dihitung dapat bisa dalam bentuk persentase atau tidak, dimana nilai MAPE yang rendah menunjukan performa yang lebih baik.

Berikut perbandingan performa antara keempat model menggunakan tiga metrik evaluasi.

|       | KNN      | *Random Forest* | *Adaptive Boost* | *XGBoost* |
| ----- | -------- | --------------- | ---------------- | --------- |
| MSE   | 17522.92 | 7067.60         | 33022.24         | 729186.55 |
| $R^2$ | 0.9662   | 0.9863          | 0.9363           | -0.4063   |
| MAPE  | 0.1759   | 0.0695          | 0.2740           | 0.4850    |

Tabel 1. Perbandingan Performa Model pada Dataset Uji

Berdasarkan data dari Tabel 1, model *random forest* memiliki hasil performa yang paling baik dibandingkan dengan ketiga model lainnya dengan parameter MSE sebesar 7067.6, $R^2$ sebesar 0.9863, dan MAPE sebesar 0.0695. Terlihat juga model XGBoost memiliki performa yang buruk dibandingkan ketiga model. 

Visualisasi dari perbandingan performa antara setiap model dapat ditunjukan pada Gambar 20. Dimana performa dataset latih dan uji dari keempat model dapat dibandingkan. model *random forest* lebih baik dibandingkan model lainnya.

![download (20)](https://github.com/fadhillaha/project-pertama-predictive-analysis/assets/40687068/d6b33c48-19b6-4269-bb20-760a274ad027)

Gambar 20. Grafik Batang Perbandingan Model Berdasarkan Metrik MAPE

Gambar 20 menunjukan bahwa model *random forest* memiliki performa yang lebih baik pada dataset latih dan uji. Model XGBoost memiliki performa yang baik pada dataset latih, namun memiliki performa yang buruk pada dataset uji. Hal ini dapat menandakan adanya *overfitting* pada model dan diperlukannya pengaturan hyperparameter lebih lanjut untuk mendapatkan hasil yang lebih baik.

Hal lain yang dapat dilakukan adalah menguji hasil prediksi dari keempat model terhadap nilai harga tiket yang sebenarnya. Hasilnya dapat dilihat pada Tabel 2.

| y_true | KNN     | *Random Forest* | *Adaptive Boosting* | XGBoost |
| ------ | ------- | --------------- | ------------------- | ------- |
| 60396  | 49437.1 | 60396.0         | 57917.3	           | 5376.3  |

Tabel 2. Perbandingan Hasil Prediksi Model terhadap Nilai Harga Tiket Sebenarnya.

Berdasarkan evaluasi menggunakan metrik evaluasi dan perbandingan hasil prediksi, dapat disimpulkan bahwa model yang telah dikembangkan telah dapat memprediksi harga tiket pesawat dengan baik dengan menggunakan algoritma *random forest*.

---
## Referensi

[1]  Etzioni, Oren., & Tuchinda, Rattapoom., &  Knoblock, Craig A., & Yates, Alexander. (2003). To buy or not to buy: mining airfare data to minimize ticket purchase price. In: 9th ACM SIGKDD international conference on Knowledge discovery and data mining, ACM, New York, USA. 119-128.

[2] Juhar Ahmed Abdella &  NM Zaki & Khaled Shuaib & Fahad Khan. (2021) Airline ticket price and demand prediction: A survey. Journal of King Saud University - Computer and Information Sciences. 33 (4). 375-391

[3] Dechang Lin. (2022). Research on the Airline Industry Airfare Pricing Factors under Difficult Circumstances. In: Proceedings of the 2022 2nd International Conference on Enterprise Management and Economic Development (ICEMED 2022). 868-873

[4] Jun Lu. (2018). Machine learning modeling for time series problem: Predicting flight ticket prices. 

[5] BUYRUKOĞLU, S., & YILMAZ, Y. (2021). An Approach for Airfare Prices Analysis with Penalized Regression Methods. Veri Bilimi, 4(2), 57-61.
