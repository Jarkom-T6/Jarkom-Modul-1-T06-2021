# Kelompok T6
  Syakhisk Al-Azmi (05311940000003)<br>
  Rizki Wijaya (05311940000014)<br>
  Shafira Firdausi (05311940000040)<br>

# Soal
#### 1. Sebutkan web server yang digunakan pada "ichimarumaru.tech"!
Masukkan command display filter `http.host contains ichimarumaru.tech`, lalu follow salah satu TCP stream yang ada.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/1_1.png)<br>
sehingga ditemukan web server yang digunakan pada “ichimarumaru.tech”, yakni **nginx/1.18.0 (Ubuntu)**.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/1_2.png)<br>

#### 2. Temukan paket dari web-web yang menggunakan basic authentication method!
Pertama tuliskan command `http.auth basic`, sehingga berikut hasil paket dari web-web yang menggunakan *Basic Authentication Method*.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/2.png)<br>

#### 3. Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!
Pertama ditemukan username dan password dari file .pcap yakni _**kuncimenujulautan:tQKEJFbgNGC1NCZIWAOjhym603xEbPkJhTciZN**_. Lalu dilakukan login ke basic.ichimarumaru.tech dan disebutkan urutan konfigurasi pengkabelan T568A.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/3.png)<br>

#### 4. Temukan paket mysql yang mengandung perintah query select!
Dituliskan command `mysql.command==3` untuk memfilter paket mysql yang mengandung perintah query select, lalu follow salah satu TCP stream, sehingga ditemukan username dan password _**("akakanomi",md5("pemisah4lautan"))**_.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/4.png)<br>

#### 5. Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!
Dari username dan password yang didapat pada nomor 4 sebelumnya, dilakukan login ke portal.ichimarumaru.tech dan disebutkan urutan konfigurasi pengkabelan T568B.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/5.png)<br>

#### 6. Cari username dan password ketika melakukan login ke FTP Server!
Dituliskan command `ftp` pada display capture, sehingga berikut username dan password yang ditemukan _**(USER secretuser, PASS aku.pengen.pw.aja)**_.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/6.png)<br>

#### 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")
Untuk menyelesaikan soal tersebut maka lakukan display filter dengan menggunakan `frame contains "Real.pdf"` maka akan didapatkan hasil sebagai berikut.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/7_1.png)<br>
Selanjutnya download file tersebut dengan melakukan follow TCP Stream, dengan klik kanan follow kemudian TCP Stream. Kemudian di TCP Stream rubah ke Raw sehingga menghasilkan hasil sebagai berikut.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/7_2.png)<br>
Selanjutnya save as file tersebut ke zip, dan lakukan extrak file maka akan didapatkan file pdf yang berisi sebagai berikut.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/7_3.png)<br>
(semua file pdf berisi **not this** kecuali pdf tersebut 😠)<br>

#### 8. Cari paket yang menunjukan pengambilan file dari FTP tersebut!
Jika menggunakan file **8-10.pcap** tidak ditemukan paket apapun, kami mencari menggunakan filter `ftp.command contains RETR`.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/8_1.png)<br>
Jika kita menggunakan `filter ftp.command contains STOR`, maka ditemukan data sebagai berikut.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/8_2.png)<br>

#### 9. Dari paket-paket yang menuju FTP terdapat indikasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!
Langkah pertama untuk menemukan file secret.zip, lakukan display filtering dengan menggunakan `ftp-data.command contains secret.zip`.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/9_1.png)<br>
Lakukan follow TCP stream dengan klik kanan follow kemudian pilih follow selanjutnya TCP stream, maka akan menampilkan data berupa ASCII sebagai berikut.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/9_2.png)<br>
Kemudian lakukan show data ke Raw, dengan pilih Show data as sehingga menjadi sebagai berikut.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/9_3.png)<br>
Selanjutnya Save as dan simpan dalam bentuk .zip, maka akan didapatkan file secret.zip. Dimana di dalam file tersebut terdapat file berupa Wanted.pdf yang tidak dapat di extract karena di password.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/9_4.png)<br>

#### 10. Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!
Untuk menyelesaikan soal nomor 10, lakukan display filter pada wireshark menggunakan `ftp-data.command contains history.txt` sehingga mendapatkan hasil sebagai berikut.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/10_1.png)<br>
Lakukan follow TCP stream dengan klik kanan follow kemudian pilih follow selanjutnya TCP stream, maka akan menampilkan data berupa ASCII sebagai berikut.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/10_2.png)<br>
Terlihat dari isi file history.txt terdapat history command yang pernah diketikkan oleh user, dimana terlihat bahwa password dari file secret.zip merupakan hasil dari tail -1 bukanapaapa.txt. Sehingga selanjutnya kita cari file bukanapaapa.txt dengan menggunakan `ftp-data.command contains bukanapaapa.txt`.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/10_3.png)<br>
Lakukan follow TCP stream dengan klik kanan follow kemudian pilih follow selanjutnya TCP stream, maka akan menampilkan data berupa ASCII sebagai berikut.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/10_4.png)<br>
Terlihat pada file bukanapaapa.txt, berisi _**d1b1langbukanapaapajugagapercaya**_ Kemudian gunakan untuk megekstrak file secret.zip. Maka file berhasil di extract dan terdapat file pdf yang apabila dibuka akan menampilkan sebagai berikut.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/10_5.png)<br>

#### 11. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!
Masukkan command `src port 80`.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/11_1.png)<br>
sehingga berikut hasil capture paket yang berasal dari port 80.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/11_2.png)<br>

#### 12. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!
Lakukan capture filter `port 21` di interface **loopback**.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/12_1.png)<br>
Port 21 adalah port FTP, jadi kami coba nyalakan server ftp local menggunakan `systemctl start vsftpd` <br>
Lalu coba connect ke server localhost menggunakan `ftp localhost`<br>
Maka setelah itu akan muncul paket yang diterima pada port 21 sebagai berikut.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/12_2.png)<br>

#### 13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!
Masukkan command `dst port 443`.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/13_1.png)<br>
sehingga berikut hasil capture paket yang menuju port 443.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/13_2.png)<br>

#### 14. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!
Masukkan command `host kemenag.go.id`.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/14_1.png)<br>
sehingga berikut hasil capture paket yang tujuannya ke kemenag.go.id.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/14_2.png)<br>

#### 15. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
Masukkan command `src host 10.10.8.26`.<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/15_1.png)<br>
sehingga berikut hasil capture paket yang berasal dari ip salah satu anggota kami (10.10.8.26).<br>
![image](https://github.com/Jarkom-T6/Jarkom-Modul-1-T06-2021/blob/main/Picture/15_2.png)<br>
