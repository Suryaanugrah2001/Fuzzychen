# Fuzzychen
Algorithm Fuzzy Time Series Chen (R programing)

install.packages("fuzzy")
library(fuzzy)

# Membaca data deret waktu
data <- read.csv('nama_file.csv')  # Gantilah "nama_file.csv" dengan nama file Anda

#Konversi Data Menjadi Fuzzy Sets
nilai_fuzzy <- linguistic(var = data$nilai, type = "trapmf", params = c(0, 0, 20, 40))

# membangun model
model <- fts.chen(data = nilai_fuzzy, lag = 2, steps = 3, method = "HW", n.ahead = 1)

# lag adalah jumlah lag (periode sebelumnya) yang akan digunakan dalam model.steps adalah jumlah langkah ke depan yang akan diprediksi.method adalah metode peramalan yang dapat digunakan (misalnya, "HW" untuk Holt-Winters).n.ahead adalah jumlah periode ke depan yang akan diprediksi.

# Peramalan
forecast <- forecast(model, n.ahead = 1)
plot(forecast)

