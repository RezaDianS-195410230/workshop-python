Mempelajari Tutorial

BAB 6 MODUL
Modul adalah yang berisi definisi dan pernyataan Python. 
Nama file adalah nama modul dengan akhiran .py ditambahkan. 
Dalam sebuah modul, nama modul (sebagai string) tersedia sebagai nilai dari variabel global name
ditor teks favorit Anda untuk membuat file bernama fibo.py di direktori saat ini dengan konten berikut:

# Fibonacci numbers module

def fib(n):    # write Fibonacci series up to n
    a, b = 0, 1
    while a < n:
        print(a, end=' ')
        a, b = b, a+b
    print()

def fib2(n):   # return Fibonacci series up to n
    result = []
    a, b = 0, 1
    while a < n:
        result.append(a)
        a, b = b, a+b
    return result

Sekarang masukkan interpreter Python dan impor modul ini dengan perintah berikut:

>>> import fibo

Ini tidak memasukkan nama fungsi yang didefinisikan dalam fibo secara langsung di tabel simbol saat ini; 
itu hanya memasukkan nama modul fibo di sana. Menggunakan nama modul Anda dapat mengakses fungsi:

>>> fibo.fib(1000)
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987
>>> fibo.fib2(100)
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
>>> fibo.__name__
'fibo'

Jika Anda ingin sering menggunakan suatu fungsi, Anda dapat menetapkannya ke nama lokal:

>>> fib = fibo.fib
>>> fib(500)
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377

6.1. Lebih lanjut tentang Module

Setiap modul memiliki tabel simbol pribadinya sendiri, yang digunakan sebagai tabel simbol global oleh semua fungsi yang didefinisikan dalam modul. 
Dengan demikian, pembuat modul dapat menggunakan variabel global dalam modul tanpa mengkhawatirkan bentrokan yang tidak disengaja dengan variabel global pengguna. 
Di sisi lain, jika kita tahu apa yang kita lakukan, kita dapat menyentuh variabel global modul dengan notasi yang sama yang digunakan untuk merujuk ke fungsinya, modname.itemname.

6.1.2. Jalur Pencarian Modul
Saat modul bernama spam diimpor, penerjemah pertama-tama mencari modul bawaan dengan nama itu. Jika tidak ditemukan, maka akan mencari file bernama spam.
py dalam daftar direktori yang diberikan oleh variabel sys.path. sys.path diinisialisasi dari lokasi ini:
Direktori yang berisi skrip input (atau direktori saat ini ketika tidak ada file yang ditentukan).
PYTHONPATH (daftar nama direktori, dengan sintaks yang sama dengan variabel shell PATH).
Default yang bergantung pada penginstalan (menurut konvensi termasuk direktori site-packages, ditangani oleh modul situs).

6.1.3. File Python "Dikompilasi"
Untuk mempercepat pemuatan modul, Python menyimpan versi kompilasi dari setiap modul di direktori pycache di bawah nama module.version.pyc, di mana versi mengkodekan format file yang dikompilasi; biasanya berisi nomor versi Python. 
Misalnya, di CPython rilis 3.3 versi kompilasi dari spam.py akan di-cache sebagai pycache/spam.cpython-33.pyc. 
Konvensi penamaan ini memungkinkan modul yang dikompilasi dari rilis yang berbeda dan versi Python yang berbeda untuk hidup berdampingan.

6.2. Modul Standar
Kumpulan modul tersebut adalah opsi konfigurasi yang juga bergantung pada platform yang mendasarinya. Misalnya, modul winreg hanya tersedia di sistem Windows. 
Satu modul tertentu patut mendapat perhatian: sys, yang dibangun ke dalam setiap juru bahasa Python. 
Variabel sys.ps1 dan sys.ps2 mendefinisikan string yang digunakan sebagai prompt primer dan sekunder
Variabel sys.path adalah daftar string yang menentukan jalur pencarian interpreter untuk modul. 
Ini diinisialisasi ke jalur default yang diambil dari variabel lingkungan PYTHONPATH, atau 
dari default bawaan jika PYTHONPATH tidak disetel. Anda dapat memodifikasinya menggunakan operasi daftar standar

6.3. Fungsi dir()
Fungsi bawaan dir() digunakan untuk mengetahui nama yang didefinisikan oleh modul. Ini mengembalikan daftar string yang diurutkan
dir() tidak mencantumkan nama fungsi dan variabel bawaan. Jika Anda ingin daftarnya, mereka didefinisikan dalam modul standar bawaan builtins

6.4. Paket
Paket adalah cara menyusun namespace modul Python dengan menggunakan "nama modul bertitik". 
Misalnya, nama modul A.B menunjuk submodule bernama B dalam paket bernama A. Sama seperti penggunaan modul menyelamatkan penulis modul yang berbeda dari harus khawatir tentang 
nama variabel global masing-masing, penggunaan nama modul bertitik menyelamatkan penulis paket multi-modul seperti NumPy atau Bantal karena harus khawatir tentang nama modul masing-masing.
Misalkan Anda ingin merancang kumpulan modul (a "package") untuk penanganan file suara dan data suara yang seragam. Ada banyak format file suara yang berbeda (biasanya dikenali dari ekstensinya, misalnya: .wav, .aiff, .au), 
jadi Anda mungkin perlu membuat dan memelihara koleksi modul yang terus bertambah untuk konversi antara berbagai format file. Saat mengimpor paket, Python mencari melalui direktori di sys.path mencari subdirektori paket. 
File init.py diperlukan untuk membuat Python memperlakukan direktori yang berisi file sebagai paket. Ini mencegah direktori dengan nama umum, seperti string, secara tidak sengaja menyembunyikan modul valid yang muncul kemudian di jalur pencarian modul.

6.4.1. Mengimpor Dari Paket
ernyataan impor menggunakan konvensi berikut: jika kode init.py paket mendefinisikan daftar bernama all, itu dianggap sebagai daftar nama modul yang harus diimpor ketika dari paket import * ditemukan. 
Terserah pembuat paket untuk tetap memperbarui daftar ini ketika versi baru dari paket dirilis. Pembuat paket juga dapat memutuskan untuk tidak mendukungnya, jika mereka tidak melihat gunanya mengimpor * dari paket mereka. 
Misalnya, file sound/effects/init.py dapat berisi kode berikut:

__all__ = ["echo", "surround", "reverse"]

6.4.2. Referensi Intra-paket
nda dapat menggunakan impor absolut untuk merujuk ke submodul paket saudara kandung. Sebagai contoh, jika modul sound.filters.
vocoder perlu menggunakan modul echo dalam paket sound.effects, modul tersebut dapat menggunakan dari sound.effect import echo.
Dari modul surround misalnya, Anda dapat menggunakan:

from . import echo
from .. import formats
from ..filters import equalizer

6.4.3. Paket di Beberapa Direktori
Paket mendukung satu atribut khusus lagi, path. Ini diinisialisasi menjadi daftar yang berisi nama direktori yang menyimpan init.py paket sebelum kode dalam file itu dieksekusi. 
Variabel ini dapat dimodifikasi; hal itu akan memengaruhi pencarian modul dan subpaket di masa mendatang yang terdapat dalam paket.