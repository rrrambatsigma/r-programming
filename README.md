# R PROGRAMMING - EDA (Exploratory Data Analysis)

This repository contains a collection of R scripts and notebooks used to explore fundamental and intermediate data wrangling techniques. 
Exploratory Data Analysis (EDA) is the process of exploring and understanding data before doing any formal analysis or building models.

It covers essential topics such as:
- Handling missing values
- Removing duplicates
- Filtering and grouping data
- Reshaping datasets (pivoting and unpivoting)
- Merging datasets
- Data visualization

# EDA SYNTAX
```r
install.packages("kaggle")
library(kaggle)
install.packages("kaggle", repos = "http://cran.us.r-project.org")
library(kaggle)

A <- (Latihan.Soal.EDA.Kelas.B....Kelas.B)
#1
#MEAN FOR SALARY
mean(A$Salary)
#MEDIAN FOR SALARY
median(A$Salary)
#MODE FOR SALARY
Mode = function(A){
  ta = table(A)
  tam = max(ta)
  if(all(ta==tam))
    mod = NA
  else
    if(is.numeric(A))
      mod = as.numeric(names(ta)[ta == tam])
  else
    mod = names(ta)[ta == tam]
  return(mod)
}
Mode(A$Salary)
#STANDARD DEVIASI SALARY
sd(A$Salary)
#VARIANS SALARY
var(A$Salary)

#MEAN FOR AGE
mean(A$Age)
#MEDIAN FOR AGE
median(A$Age)
#MODE FOR AGE
Mode = function(A){
  ta = table(A)
  tam = max(ta)
  if(all(ta==tam))
    mod = NA
  else
    if(is.numeric(A))
      mod = as.numeric(names(ta)[ta == tam])
  else
    mod = names(ta)[ta == tam]
  return(mod)
}
Mode(A$Age)
#STANDARD DEVIASI AGE
sd(A$Age)
#VARIANS AGE
var(A$Age)
```

Berikut penjelasan lengkap dalam bentuk paragraf yang berfokus pada input dan output dari sintaks R berikut:

---

Kode R ini bertujuan untuk melakukan analisis deskriptif pada data gaji yang terdapat dalam sebuah dataset yang dinamai `Latihan.Soal.EDA.Kelas.B....Kelas.B`.

Setelah memuat data ke dalam objek `A`, analisis dimulai dengan menghitung nilai mean (rata-rata)dari kolom `Salary` menggunakan fungsi `mean(A$Salary)`, yang mengembalikan nilai rata-rata dari semua data gaji. Selanjutnya, fungsi `median(A$Salary)` menghitung **median**, yaitu nilai tengah ketika data `Salary` diurutkan, yang berguna untuk memahami pusat distribusi data yang mungkin tidak simetris.

Untuk mencari modus (mode), didefinisikan fungsi khusus bernama `Mode` yang menghitung frekuensi setiap nilai dalam vektor masukan (dalam hal ini `A$Salary`) dan mengembalikan nilai yang paling sering muncul. Fungsi ini juga mempertimbangkan apakah seluruh nilai memiliki frekuensi yang sama (tidak ada modus) dan apakah datanya numerik atau bukan.

Setelah itu, digunakan fungsi `sd(A$Salary)` untuk menghitung standar deviasi, yang menunjukkan seberapa besar variasi atau penyebaran data gaji dari rata-ratanya. Terakhir, fungsi `var(A$Salary)` digunakan untuk menghitung varians, yaitu kuadrat dari standar deviasi, yang juga menggambarkan tingkat penyebaran data.

Secara keseluruhan, input dalam kode ini adalah kolom `Salary` dari dataset, sedangkan output-nya berupa ringkasan statistik deskriptif: mean, median, mode, standar deviasi, dan varians yang membantu memahami karakteristik distribusi data gaji dalam populasi tersebut.

---
Mean (Rata-rata): Fungsi `mean(A$Age)` menghitung nilai rata-rata usia dari seluruh data dalam kolom Age. Outputnya adalah angka yang mewakili usia rata-rata dari dataset tersebut.

Median (Nilai Tengah): Fungsi `median(A$Age)` digunakan untuk mencari nilai median usia, yaitu nilai yang terletak di tengah-tengah dataset setelah diurutkan. Jika data terurut, maka median adalah nilai yang membagi data menjadi dua bagian yang sama besar.

Mode (Modus): Fungsi Mode yang didefinisikan di dalam kode ini menghitung nilai yang paling sering muncul (modus) dalam kolom Age. Fungsi ini pertama-tama menghitung frekuensi kemunculan setiap nilai dalam A$Age dengan fungsi table(A). Kemudian, modusnya adalah nilai yang memiliki frekuensi tertinggi. Jika seluruh nilai memiliki frekuensi yang sama, maka hasilnya adalah NA (tidak ada modus). Fungsi ini dapat mengembalikan hasil dalam bentuk numerik atau karakter tergantung pada apakah kolom Age berisi data numerik atau bukan.

Standard Deviation (Standar Deviasi): Fungsi `sd(A$Age)` menghitung seberapa jauh data usia tersebar dari nilai rata-ratanya. Hasil outputnya adalah nilai standar deviasi, yang menunjukkan tingkat penyebaran data usia.

Variance (Varians): Fungsi `var(A$Age)` menghitung varians usia, yang merupakan kuadrat dari standar deviasi. Varians ini juga menggambarkan seberapa besar data usia tersebar dari rata-ratanya, meskipun dalam unit kuadrat.

```r
#2 
#ANALISIS KORELASI
cor(A$Years.of.Service , A$Salary)
```

---

Baris kode ini digunakan untuk melakukan *analisis korelasi* antara dua variabel dalam dataset, yaitu `Years.of.Service` (lama bekerja) dan `Salary` (gaji). Fungsi `cor()` dalam R digunakan untuk menghitung *koefisien korelasi Pearson*, yang mengukur kekuatan dan arah hubungan linear antara dua variabel numerik.

Sebagai input, fungsi ini menerima dua vektor numerik: `A$Years.of.Service` dan `A$Salary`. `A$Years.of.Service` berisi data mengenai jumlah tahun seseorang telah bekerja, sedangkan `A$Salary` adalah data gaji masing-masing individu dalam dataset.

Output dari fungsi ini adalah sebuah angka antara -1 dan 1:
* Nilai positif (misalnya 0.75) menunjukkan bahwa semakin lama seseorang bekerja, semakin tinggi gajinya—dengan kata lain, ada hubungan linear searah (positif).
* Nilai negatif (misalnya -0.4) menunjukkan hubungan berlawanan arah, yaitu semakin lama bekerja, justru gajinya cenderung lebih rendah.
* Nilai mendekati nol (misalnya 0.05) berarti tidak ada hubungan linear yang kuat antara lama bekerja dan gaji.
---

```r
#3 VISUALIZATION
#HISTOGRAM
hist(A$Age, main = "AGE", xlab="usia", ylab = "jumlah pekerja",col="purple")
#BARPLOT
barplot(table(A$Position), las=3)
#BOXPLOT
boxplot(A$Salary ~ A$Position)
```

---

Histogram: Baris `hist(A$Age, main = "AGE", xlab="usia", ylab = "jumlah pekerja", col="purple")` menghasilkan histogram dari kolom Age. Sebagai input, fungsi ini menggunakan vektor usia, dan menampilkan distribusi frekuensi usia pekerja dalam bentuk batang. Sumbu-x menunjukkan rentang usia, sementara sumbu-y menunjukkan jumlah pekerja di tiap rentang usia tersebut. Warna histogram diatur menjadi ungu `(col="purple")` . Histogram ini memberikan gambaran apakah distribusi usia bersifat simetris, condong ke kanan/kiri, atau memiliki beberapa puncak (multimodal).

Barplot: Fungsi `barplot(table(A$Position), las=3)` digunakan untuk membuat grafik batang dari posisi jabatan (Position) dalam dataset. Fungsi table position menghitung jumlah pekerja di setiap jenis posisi, yang kemudian divisualisasikan dalam bentuk batang vertikal. Parameter `las=3` membuat label kategori posisi ditampilkan secara vertikal (atau dimiringkan 90 derajat), sehingga mempermudah pembacaan jika labelnya panjang atau jumlah kategorinya banyak. Output dari visualisasi ini menunjukkan jumlah pekerja berdasarkan posisi atau jabatan.

Boxplot: Baris `boxplot(A$Salary ~ A$Position)` menghasilkan boxplot (diagram kotak) yang memperlihatkan distribusi gaji untuk setiap posisi. Ini adalah bentuk visual dari analisis perbandingan distribusi, dengan input berupa data gaji sebagai respon dan posisi sebagai grup. Output-nya adalah grafik yang menunjukkan median gaji, kuartil bawah dan atas, serta outlier (jika ada) untuk setiap jabatan. Boxplot ini membantu melihat variasi gaji antar posisi dan apakah ada posisi yang memiliki distribusi gaji lebih tinggi atau lebih menyebar dibandingkan yang lain.

---

```r
#4
#QUARTILES
quantile(A$Salary)
quantile(A$Salary, 0.25)
quantile(A$Salary, 0.50)
quantile(A$Salary, 0.75)
#OUTLIERS
IQR(A$Salary)
batas_bawah<- quantile(A$Salary, 0.25) - 1.5*IQR(A$Salary)
batas_atas<- quantile(A$Salary, 0.75) + 1.5*IQR(A$Salary)
print(IQR(A$Salary))
print(batas_bawah)
print(batas_atas)
#CETAK OUTLIERS
outliers <-A$Salary[A$Salary<batas_bawah | A$Salary>batas_atas]
print(outliers)
```

---
Kode ini digunakan untuk menganalisis kuartil dan outlier pada kolom Salary. Fungsi quantile(A$Salary) menghasilkan lima nilai penting: minimum, kuartil 1 (Q1), median (Q2), kuartil 3 (Q3), dan maksimum. Baris-baris berikutnya `(quantile(A$Salary, 0.25), 0.50, 0.75)` menghitung masing-masing kuartil secara terpisah.
Untuk mendeteksi outlier, digunakan fungsi IQR(A$Salary) untuk menghitung rentang interkuartil (Q3 - Q1). Kemudian ditentukan batas bawah dan batas atas sebagai:

Batas bawah = Q1 - 1.5 × IQR

Batas atas = Q3 + 1.5 × IQR

Nilai Salary yang berada di luar rentang tersebut dianggap outlier dan diambil menggunakan filter logika A$Salary < batas_bawah | A$Salary > batas_atas. Nilai-nilai tersebut kemudian dicetak dengan print(outliers).

---

```r
#5.
#COMPARISON
#RATA-RATA GAJI PEKERJA YANG MEMILIKI STATUS FULL TIME
mean(A$Salary[A$Full.Time == "Yes"])
mean(A$Salary[A$Full.Time == "No"])
class(A$Salary)
class(A$Full.Time)
```

---
Kode ini digunakan untuk membandingkan rata-rata gaji berdasarkan status kerja (Full Time atau bukan). Baris `mean(A$Salary[A$Full.Time == "Yes"])` menghitung rata-rata gaji pekerja full-time, sementara `mean(A$Salary[A$Full.Time == "No"])` menghitung rata-rata gaji pekerja non-full-time.

Dua baris terakhir `(class(A$Salary) dan class(A$Full.Time))` digunakan untuk mengecek tipe data dari kolom Salary dan Full.Time. Biasanya Salary bertipe numerik (numeric) dan Full.Time bertipe karakter (character) atau faktor (factor), tergantung struktur dataset.
