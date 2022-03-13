BAB 7 - Input dan Output
Bab ini membahas beberapa cara untuk menampilkan output dari suatu program, data dapat dicetak dalam bentuk yang dapat dibaca, 
atau ditulis ke file untuk digunakan kedepannya.

7.1. Pemformatan output yang lebih menarik
Dua cara untuk menulis nilai: pernyataan ekspresi dan print() fungsi.
Ada beberapa cara untuk memformat output.
- Di dalam string ini, dapat menulis ekspresi Python antara {end} karakter yang dapat merujuk ke variabel atau nilai literal. 
Mulailah string dengan f atau F sebelum tanda kutip pembuka atau tanda kutip tiga.
- Metode str.format() string membutuhkan lebih banyak upaya manual.
- Tipe string memiliki beberapa metode yang melakukan operasi yang berguna untuk mengisi string ke lebar kolom tertentu.
Fungsi str() ini dimaksudkan untuk mengembalikan representasi nilai yang cukup dapat dibaca manusia,
sedangkan repr()dimaksudkan untuk menghasilkan representasi yang dapat dibaca oleh penerjemah. 
7.1.1. Literal string
- Literal string yang diformat (disingkat juga disebut f-string) memungkinkan untuk memasukkan nilai ekspresi Python 
di dalam string dengan mengawali string dengan f or F dan menulis ekspresi sebagai {expression}.
7.1.2. Format string()
Penggunaan dasar str.format() 
7.1.3. Pemformatan string
Metode str.rjust() objek string membenarkan string di bidang dengan lebar tertentu dengan mengisinya dengan spasi di sebelah kiri. 
Ada metode lain, str.zfill()
7.2. File
open() mengembalikan objek file , dan paling sering digunakan dengan dua argumen: .open(filename, mode)
7.2.1. Metode dari file objek
objek file yang dipanggil f.
Untuk membaca konten file, panggil f.read(size).  
f.read() akan mengembalikan string kosong ('').
f.readline() membaca satu baris dari file.
f.write(string) menulis isi string ke file
f.tell()mengembalikan bilangan bulat yang memberikan posisi objek file saat ini dalam file 
yang direpresentasikan sebagai jumlah byte dari awal file saat dalam mode biner dan angka buram saat dalam mode teks
7.2.2. Menyimpan data terstruktur dengan json
Catatan Format JSON biasanya digunakan oleh aplikasi modern untuk memungkinkan pertukaran data. Banyak programmer sudah mengetahuinya, 
yang menjadikannya pilihan yang baik untuk interoperabilitas.