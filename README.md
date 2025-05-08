#   R PROGRAMMING - EDA (Exp
This repository contains a collection of R scripts and notebooks used to explore fundamental and intermediate data wrangling techniques. It covers essential topics such as handling missing values, removing duplicates, filtering and grouping data, reshaping datasets (pivoting and unpivoting), merging datasets, and data visualization.

===============================================================================================================================================================================================================

#TAKE DATA
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

Kode R ini digunakan untuk menghitung rata-rata, median, dan modus dari data gaji (`Salary`). Data disimpan dalam variabel `A`, dan fungsi `mean()` serta `median()` digunakan langsung. Karena R tidak punya fungsi bawaan untuk modus, dibuatlah fungsi `Mode()` yang mencari nilai paling sering muncul. Jika semua nilai muncul sama banyak, maka hasilnya `NA`. Intinya, kode ini membantu memahami sebaran nilai gaji dalam data.

