# **Predicting Used Car Price in the UK**
Created By : Rafidghadah Damarta dan Zahir Ilham

## **Business Problem Understanding**
### **Context**

Pandemi covid 19 memberikan efek ke berbagai macam bisnis termasuk bisnis jual-beli mobil bekas. Berdasarkan data [Society of Motor Manufacturers and Traders](https://www.smmt.co.uk/category/vehicle-data/used-car-sales-data/), sepanjang tahun 2022 transaksi mobil bekas di Inggris Raya mengalami penurunan. Namun pada tahun 2023 transaksi mobil bekas di Inggris Raya mengalami pemulihan. Hal ini dibuktikan dengan [pertumbuhan transaksi mobil bekas sebesar 4.1% di Q1 tahun 2023](https://www.smmt.co.uk/2023/05/used-car-sales-q1-2023/) dan menjadi awal terbaik semenjak tahun 2020. Pertumbuhan moderate ini terus terjadi hingga Q3 tahun 2023. Walaupun pada Q4 mengalami penurunan sebesar -4.3%, hal ini masih menunjukan bahwa bisnis jual-beli mobil bekas di Inggris Raya sedang mengalami pertumbuhan kembali. 

Webuy Used Cars merupakan perusahaan yang bergerak di bidang jual-beli mobil bekas sebagai perantara, dengan cara memfasilitasi transaksi antara penjual dan pembeli melalui platform khusus yaitu website jual-beli. Penjual dapat membuat iklan untuk mobil yang ingin dijual dan menentukan harganya berdasarkan rentang harga yang diberikan Webuy Used Cars. Setelah beroperasi di beberapa negara, perusahaan memutuskan untuk melakukan ekspansi ke Inggris Raya.

Untuk melakukan ekspansi dengan baik, tim riset dan pengembangan dari perusahaan Webuy Used Cars ingin mencari tau bagaimana perushaan dapat mengidentifikasi karakteristik mobil bekas di Inggris Raya berdasarkan rentang harganya karena, jika perusahaan melakukan ekspansi tanpa memahami karakteristik mobil bekas di Inggris Raya akan menimbulkan tantangan bahkan kesalahan strategi bagi perusahaan dalam melakukan ekspansi itu sendiri.

Selain karakteristik mobil, penentuan harga juga menjadi penting. Jika perusahaan memberikan rentang harga yang terlalu mahal dari harga pasar, maka akan menyebabkan mobil sulit terjual. Hal ini juga akan menyebabkan kerugian bagi perushaan, karena pembeli mobil akan beralih ke pesaing lainya. Sementara jika perusahaan memberikan rentang harga yang terlalu murah dari harga pasar, maka akan menyebabkan penjual dan perusahaan tidak mendapatkan keuntungan yang optimal. Oleh karena itu, mengetahui harga optimal menjadi penting.  

### **Problem Statement**

- Siapa stakeholder yang memiliki masalah?
    - Tim riset dan pengembangan Webuy Used Cars
    - Penjual Mobil Bekas
- Masalah yang dihadapi oleh stakeholder tersebut?
    - Kesulitan mengetahui karakteristik mobil bekas yang ada di Inggris Raya, membuat stakeholder kesulitan untuk mengetahui informasi dasar mengenai mobil bekas di daerah ekspansi mereka.
    - Kesulitan untuk menentukan harga mobil yang sesuai dengan harga pasar secara effisien.
- Mengapa masalah perlu dipecahkan?
    - Tidak memahami karakteristik mobil bekas di Inggris Raya akan menimbulkan tantangan bahkan kesalahan strategi bagi perusahaan dalam melakukan ekspansi itu sendiri.
    - Untuk memperoleh estimasi harga, penjual harus menunggu tim Webuy Used Cars memeriksa informasi yang telah diisi mengenai mobil yang hendak dijual. Proses ini memakan waktu dan menambah beban kerja, sehingga kurang efisien.

### **Goals**

- Apa tujuan dan target dari penyelesaian masalah?
     - Mengembangkan model prediktif dengan metric evaluation MAPE kurang dari 12% untuk memastikan akurasi tinggi dalam memprediksi harga mobil bekas. Hal ini berdasarkan [percobaan lain yang memprediksi harga mobil bekas di India yang berhasil menghasilkan MAPE <12%](https://www.atlantis-press.com/article/125971556.pdf).
    - Mengidentifikasi karakteristik mobil bekas di Inggris Raya, berdasarkan kategori harga, sehingga memberikan wawasan yang actionable bagi para stakeholder.
 
### **Analytic Approach**

- Apa rancangan solusi yang anda tawarkan untuk menyelesaikan masalah dari stakeholder?
    - Pendekatan analitis dimulai dengan Exploratory Data Analysis (EDA) menyeluruh untuk mendapatkan pemahaman mendalam tentang dataset. Selain itu, penjelasan rinci tentang teknik regresi itu sendiri. Pemodelan juga akan melibatkan validasi silang dan penyesuaian hiperparameter untuk memastikan kekokohan dan generalisasi model.

- Kapan dan bagaimana stakeholder akan memanfaatkan atau menggunakan solusi tersebut?
  - Wawasan yang diperoleh dari analisis ini dapat membantu tim riset dan pengembangan Webuy Used Cars dalam membuat keputusan berbasis data, memfasilitasi transaksi yang lebih terinformasi di pasar mobil bekas Inggris Raya.
  - Penjual mobil mendapatkan kemudahan untuk menentukan harga mobil bekas yang sesuai dengan harga pasar mobil bekas di Inggris Raya Jika menggunakan jasa Webuyusedcar.
 
### **Metric Evaluation**

Untuk megetahui performa suatu model memprediksi targetnya maka kita membutuhkan metric evaluation dengan mengukur nilai errornya. Pada percobaan ini kita menggunakan beberapa metric evaluation diantaranya:

| Metrics | Explaination |
|--------|-------------------|
| MAPE (Mean Absolute Percentage Error) | - MAPE mengevaluasi kesalahan prediksi sebagai persentase dari nilai sebenarnya. <br> - Kemudahan interpretasi kesalahan sebagai persentase membuatnya lebih intuitif dalam konteks bisnis. <br> - Memfasilitasi perbandingan akurasi antar model atau prediksi pada skala yang berbeda. |

Semakin kecil nilai metric evaluation, maka semakin kecil errornya menunjukkan semakin baik suatu model memprediksi nilai targetnya.

## **Data Understanding**
Dataset source: https://www.kaggle.com/datasets/adityadesai13/used-car-dataset-ford-and-mercedes/data

Terdapat 10 kolom di dalam dataset. Berikut adalah infromasi tiap kolom pada dataset:
| Attribute | Data Type | Description |
| --- | --- | --- |
| Brand | Object | Merek mobil |
| Model | Object | Nama model mobil |
| Year | Integer | Tahun produksi mobil |
| Price | Integer | Harga mobil |
| Transmission | Object | Transmisi mobil |
| Mileage | Integer | Jarak tempuh yang sudah tercapai oleh mobil tersebut |
| Fuel Type | Object | Jenis bahan bakar mobil |
| Tax | Integer | Harga pajak mobil |
| Mpg | Float | Rata-rata jarak yang ditempuh per unit energi yang dikonsumsi mobil tersebut |
| Engine Size | Float | Ukuran mesin dari mobil tersebut |

## **Data Analysis**

Untuk mengetahui karakteristik mobil yang ada di Inggris Raya berdasarkan kategori harga, kami akan mencoba menjawab pertanyaan berikut:

- Kapan tahun produksi mobil yang memiliki jumlah terbanyak pada daftar berdasarkan kategori harga?
- Apa merek mobil yang paling sering muncul pada daftar berdasarkan kategori harga?
- Apa model mobil yang umumnya muncul dalam daftar berdasarkan kategori harga?
- Jenis transmisi mobil mana yang sering muncul dalam daftar berdasarkan kategori harga?
- Jenis bahan bakar mana yang sering muncul dalam daftar berdasarkan kategori harga?
- Berapa tenaga mesin yang sering digunakan mobil dalam daftar berdasarkan kategori harga?
- Berapa rentan nilai efisiensi bahan bakar per mil (Mpg) yang sering muncul dalam daftar berdasarkan kategori harga?

Analisis lengkap terlampir pada notebook

## **Data Preparation**
Tahapan preprocessing yang dilakukan sebelum modeling

    Drop Duplicate
    Remove Whitespace
    Check Outliers
    Check Multicolinearity
    Encoding
    Scaling

## **Conclussion and Recommendation**

### **Conclusion**

**Karakteristik Mobil Berdasarkan Segment Harga:**

1. **Kategori Budget**: 
    Kategori Budget mencakup mobil produksi lama (4 tahun) yang berukuran kecil, memiliki mesin bertenaga kecil hingga menengah, bertransmisi manual, dan memiliki efisiensi bahan bakar yang sangat baik, membuat kendaraan pada kategori ini sangat cocok untuk kebutuhan transportasi perkotaan.

2. **Kategori Standard**: 
    Kategori Standard mencakup mobil-mobil dengan variasi yang beragam, dengan perpaduan karakteristik kendaraan dari kategori Budget dan Standar, membuat kendaraan pada kategori ini dapat memenuhi preferensi dan kebutuhan yang berbeda-beda.

3. **Kategori Premium**: 
    Kategori Premium mencakup mobil produksi baru (1 tahun) yang berukuran besar, memiliki mesin bertenaga menegah hingga besar, bertransmisi modern seperti semi-auto dan automatic, dan memiliki efisiensi bahan bakar yang cukup.
    
Dengan karakteristik tersebut, stakeholder mendapatkan gambaran mengenai mobil bekas di Inggris Raya berdasarkan kategori harga dari data listing mobil bekas di sana.


<br>

**Karakteristik Model Machine Learning yang Diperoleh:**

1. **Metric yang Digunakan**: 
   Penggunaan Mean Absolute Percentage Error (MAPE) memungkinkan interpretasi kesalahan prediksi secara intuitif sebagai persentase, yang lebih mudah dimengerti dalam konteks bisnis.

2. **Model Terbaik dari Cross-Validation**: 
   Model terbaik sebelum penyetelan (tuning) adalah model Random Forest dengan MAPE sebesar **7.401%**.

3. **Model Terbaik setelah Penyetelan (Tuning)**: 
   Setelah penyetelan, MAPE berhasil diturunkan menjadi **6.953%**, menunjukkan peningkatan performa sebesar 4.48%.

4. **Parameter Terbaik untuk Model Random Forest**:
   - Jumlah Pohon (n_estimators): 76
   - Minimal Sampel untuk Split (min_samples_split): 8
   - Minimal Sampel di Setiap Leaf (min_samples_leaf): 1
   - Jumlah Fitur Maksimum untuk Setiap Split (max_features): 7
   - Kedalaman Maksimum Pohon (max_depth): 20
   - Penggunaan Bootstrap (bootstrap): False

5. **Fitur yang Paling Berpengaruh** dalam Model Random Forest untuk Memprediksi Harga:
   - Engine Size
   - Year
   - Mpg (Miles Per Gallon)
   - Transmission
   - Mileage

6. **Error Residual**: 
    Berikut adalah ringkasan insight mengenai distribusi residual pada harga prediksi:

    a. **Overestimate pada Rentang -40000 hingga -20000:**
    - Terdapat dua data *Overestimate*.
    - Model cenderung overestimate harga mobil Mercedes Benz S Class dengan tahun pembuatan di bawah 2010 karena kurangnya data pada rentang tersebut.
    - Harga actual pada data test underpriced jika dibandingkan harga pasaran pada data train sehingga menyebabkan prediksi *overestimate*.

    b. **Underestimate pada Rentang 20000 hingga 90000:**
    - Terdapat tujuh data dengan persentase ekstrim antara 33.28% hingga 90.33%.
    - Prediksi underestimate pada rentang ini disebabkan oleh kurangnya data mobil pada rentang tersebut dalam data train. Akibatnya, ketika model digunakan untuk memprediksi karakteristik mobil yang sedikit berbeda pada data test, prediksi menjadi tidak akurat. Selain itu, harga aktual pada data test juga cenderung overpriced jika dibandingkan dengan harga pasaran yang ada dalam data train.
    - Harga actual pada data test *Overpriced* dibandingkan dengan harga pasaran pada data train, menyebabkan prediksi underestimate.

7. **Performa Model Berdasarkan Rentang Harga**:
    - Rentang harga kendaraan mempengaruhi tingkat kesalahan prediksi (MAPE), dengan rentang harga di bawah 10.000 menunjukkan MAPE di atas rerata keseluruhan 6.95%, menandakan peningkatan error.
    - Rentang harga 80.000-90.000 menunjukkan MAPE sangat rendah, kurang dari 2%, menunjukkan prediksi yang sangat akurat.
    - Rentang harga 90.000-100.000 menunjukkan peningkatan error yang signifikan dengan MAPE di atas 11%, mengindikasikan prediksi yang kurang akurat.
    - Rentang harga 130.000-140.000 juga menunjukkan MAPE sangat rendah, di bawah 2%, menandakan prediksi yang sangat akurat.

8. **Analisis Performa Model Berdasarkan Rentang Harga**:
    - Error terbesar disebabkan oleh Mercedes Benz S Class Engine Size 4.0 dan Year 2019 dengan error sebesar 26.18%. Model mempelajari cukup baik untuk karakteristik mobil serupa, namun harga yang diberikan pada data test jauh di atas rerata harga mobil serupa sehingga menyebabkan prediksi menjadi *underestimate*.
    - Prediksi untuk rentang harga 0-10.000 cenderung melebihi nilai aktual, karena kurangnya data kendaraan dengan tahun produksi sebelum 2011, yang membuat model sulit untuk menyesuaikan prediksi secara akurat.
    - Rentang harga 80.000-90.000 dan 130.000-140.000 menunjukkan performa prediksi yang sangat baik dengan error yang sangat kecil. Hal ini disebabkan persebaran data harga prediksi pada rentang tersebut sangat sedikit namun memiliki karakteristik yang serupa berdasarkan feature importance seperti `Engine Size`, `Year`, `Mpg`, dan `Transmission`.

9. **Cost Benefit**:

    - **Tanpa Menggunakan Model :**<br>
        -   Untuk mendapatkan estimasi harga tanpa menggunakan model, penjual harus menunggu tim Webuy Used Cars untuk memeriksa informasi yang sudah diisi terkait mobil yang dijual. Hal ini akan memakan banyak waktu dan menambah tenaga kerja
        -   Sebagai contoh, upah minimum pekerja di Inggris Raya adalah [£2013.44](https://id.tradingeconomics.com/united-kingdom/minimum-wages) per bulan, dengan asumsi bahwa mereka bekerja selama 8 jam setiap hari kerja. Tanpa menggunakan model kita perlu mengeluarkan tambahan biaya setidaknya £2013.44 (dengan asumsi pekerja mau dibiayar dengan upah minimum) per bulan untuk satu tenaga kerja yang bertugas mencari tahu estimasi harga mobil bekas yang akan dijual.
    
    - **Menggunakan Model:**<br>
    Dengan memanfaatkan model, perusahaan bisa memprediksi harga mobil tanpa biaya tambahan untuk tenaga kerja sebagai estimator harga mobil bekas. Estimasi harga mobil bekas dengan model ini memerlukan waktu singkat, berbeda dengan metode konvensional yang memakan waktu lama untuk memprediksi harga satu mobil.
    
        Perusahaan dapat menggunakan model prediksi harga mobil yang telah dikembangkan. Sebagai contoh, kami melakukakn simulasi prediksi harga mobil dengan spesifikasi sebagai berikut:  
        
            Merek: Audi
            Model: A1
            Tahun: 2019
            Transmisi: Semi-Auto
            Jarak Tempuh: 2500 mil
            Jenis Bahan Bakar: Petrol
            Pajak: £145
            Konsumsi BBM: 44.5 mpg
            Ukuran Mesin: 1.5

        Prediksi harga pasaran untuk mobil ini adalah `£22,510.469`, yang masuk dalam rentang harga `£20,000 - £30,000` dengan error sebesar `6.33%`. Artinya, harga mobil sebenarnya diperkirakan berada di kisaran `£21,079.94 - £23,941.00.` Prediksi tersebut dapat kita ketahui dalam waktu sekitar 1 detik. Dengan menerapkan model ini, diharapkan perusahaan dapat meningkatkan efisiensi biaya perusahaan terutama biaya pekerja sebagai estimator harga mobil.

### **Recommendation**

Dataset yang kami miliki merupakan data mobil yang terpampang di iklan. Karena data tidak sepenuhnya mencerminkan preferensi atau minat sebenarnya dari pelanggan. Dalam hal ini, ada beberapa rekomendasi yang dapat kami berikan kepada webuyused car antara lain:

1. **Sumber Data Untuk Analysys:** Selain data iklan, perusahaan sebaiknya juga mengumpulkan dan menganalisis data historis penjualan mobil bekas, survei pelanggan, dan sumber data lainnya. Dengan demikian, akan terbentuk pemahaman yang lebih holistik tentang preferensi dan perilaku pembeli.

2. **Penelitian Pasar yang Komprehensif:** Perlu dilakukan penelitian pasar yang menyeluruh untuk memahami tren dan preferensi konsumen dalam kategori mobil bekas. Ini termasuk analisis kompetitor, survei pelanggan potensial, serta pemahaman mendalam tentang kondisi dan tren pasar yang sedang berlangsung.

3. **Segmentasi Pelanggan yang Lebih Terperinci:** Identifikasi segmen pelanggan yang lebih terperinci berdasarkan preferensi, anggaran, dan kebutuhan mereka. Dengan memahami secara mendalam kebutuhan dan keinginan setiap segmen, perusahaan dapat menyesuaikan strategi pemasaran dan penawaran produk untuk melayani pelanggan dengan lebih baik.

4. **Kemitraan Strategis dengan Dealer:** Pertimbangkan untuk menjalin kemitraan strategis dengan dealer mobil bekas lokal atau platform jual beli mobil terkemuka seperti facebook marketplace. Melalui kemitraan ini, perusahaan dapat memperoleh wawasan langsung dari profesional di lapangan, serta akses ke data penjualan yang lebih akurat dan terkini.

5. **Integrasi Karakteristik Mobil dalam Strategi Penetapan Harga:** Gabungkan analisis data yang mendalam dan segmentasi pelanggan dengan karakteristik mobil yang ditemukan, seperti tahun pembuatan, merek, model, transmisi, bahan bakar, tenaga mesin, dan efisiensi bahan bakar. Dengan demikian, perusahaan dapat menyesuaikan harga mobil secara lebih tepat sesuai dengan nilai tambah yang ditawarkan oleh setiap kendaraan, meningkatkan daya saing dan potensi penjualan mobil bekas.


-----

Berikut adalah rekomendasi untuk meningkatkan kehandalan pemodelan yang telah kami bangun:

1. **Pertimbangkan Fitur Tambahan**: Pertimbangkan untuk menambahkan fitur tambahan yang dapat meningkatkan kinerja model. Seperti kondisi body kendaraan, interior dan mesin.

2. **Eksplorasi Model Alternatif**: Selain Random Forest, kita mengetahui pada tahapan cross validasi diperoleh model lain yang juga stabil yaitu, Catboost. Dengan melakukan tuning model alternatif lainnya diharapkan akan diperoleh model yang lebih handal.

3. **Penanganan Overestimate dan Underestimate**: Perlu dilakukan penyesuaian harga pasaran yang lebih akurat pada data test untuk memastikan bahwa harga aktual mencerminkan nilai pasaran yang sebenarnya. Hal ini akan membantu model dalam membuat prediksi yang lebih akurat dengan meminimalkan perbedaan antara harga aktual dan harga pasaran yang dipelajari oleh model.

4. **Penambahan Data**: Penambahan dataset mobil terutama pada fitur-fitur yang memiliki banyak outliers dapat meningkatkan kinerja model terutama pada features yang paling penting untuk model Random Forest yang telah dibangun. Penambahan data tersebut diharapkan agar model dapat lebih belajar dari data yang sudah ada sebelumnya namun jumlahnya masih sedikit. 

## **Tableau**
[Link Dashboard](https://public.tableau.com/views/FinalProjectAlphaTeam/Dashboard?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link)

## **Best Model**
[Link Model](https://drive.google.com/file/d/1rjNbQ8gpbyaUUaCryF1zU-R7na3C6rnK/view?usp=sharing)
