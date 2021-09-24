# Laporan Praktikum Modul 1

### Anggota  Kelompok D15 :

### Richard Asmarakandi (05111940000017)

### Nurul Izzatil Ulum (05111940000058)



## SOAL

#### 1. Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!

Ketika kita membuka website "ichimarumaru.tech", kita akan disuguhkan dengan halaman yang menunjukkan bahwa website menggunakan webserver nginx.

![ichimarumaru.tech](/pictures/1-A.png)

Untuk memastikan, dapat dilakukan pada wireshark, lalu menggunakan display filter `http contains nginx`. dan terlihat, server menggunakan nginx.

![ichimarumaru.tech](/pictures/1-B.png)

#### 2. Temukan paket dari web-web yang menggunakan basic authentication method!

Karena yang dicari adalah paket maka isi display filter adalah `http.authbasic`

![Screenshot (475)](https://user-images.githubusercontent.com/76694068/134185295-02284804-a8c8-4f57-a8e4-0808a4822d1a.png)


#### 3. Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkandari file .pcapng!

Pertama, isi display filter dengan `http.host contains basic.ichimarumaru.tech` > klik paket paling atas.
![Screenshot (461)](https://user-images.githubusercontent.com/76694068/134185981-b4914c75-d362-4740-acfc-8a3432a88ee9.png)

Kedua, cari `Hyper Text Protocol` > `Authorization` maka di Credentials ada username dan password yang dipakai
![Screenshot (462)](https://user-images.githubusercontent.com/76694068/134185997-4d96d446-b5cf-4238-9b85-8916d0eeb1b2.png)

Ketiga, untuk mencopy password dan username tersebut, `klik kiri` > `Copy` > `Value` lalu Pastekan pada suatu media 
![Screenshot (476)](https://user-images.githubusercontent.com/76694068/134186808-a653d696-4dc0-4628-aca5-6fdf1af602c8.png)

Terakhir, jika username dan password tadi dimasukkan, maka website `basic.ichimarumaru.tech` akan terbuka
![Screenshot (465)](https://user-images.githubusercontent.com/76694068/134186001-eee6f033-8d05-44cc-baea-e16a7cb4d784.png)

#### 4. Temukan paket mysql yang mengandung perintah query select!

Mengisi display filter dengan `mysql contains select or mysql contains SELECT` karena ada select yang menggunakan kapital dan tidak.
![Screenshot (464)](https://user-images.githubusercontent.com/76694068/134187633-05e65f2d-4981-4f8d-bc3a-b1f0c5e1fd8c.png)


#### 5. Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!

Karena diketahui username dan password dapat diperoleh melalui query insert, maka kita mencari paket mysql yang mengandung query dengan perintah insert melalui display picture. Expresionnya adalah `mysql.query contains INSERT or mysql.query contains insert`. Maka akan didapatkan hasil sebagai berikut :
![5-A](pictures/5-A.png)

Dari hasil tersebut, dapat disimpulkan bahwa usernamenya "akakanomi" dan passwordnya "pemisah4lautan". Setelah mendapatkan username dan password, kita loginkan pada http://portal.ichimarumaru.tech. Maka akan tampil halaman web seperti berikut :
![5-B](pictures/5-B.png)

Terdapat pertanyaan pada halaman tersebut dan kita diharuskan menjawab pertanyaannya, maka kita hanya perlu mengisi kolom jawaban dengan jawaban yang benar
![5-C](pictures/5-C.png)

#### 6. Cari username dan password ketika melakukan login ke FTP Server!

Mengisi display filter dengan `ftp.request.command == "USER" || ftp.request.command == "PASS"`
![Screenshot (467)](https://user-images.githubusercontent.com/76694068/134188079-24747c98-55b8-47b6-8286-2b45bbbe8cc5.png)


#### 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

Pertama tulis di display filter `ftp-data contains "Real.pdf"`
![Screenshot (469)](https://user-images.githubusercontent.com/76694068/134457220-43cb3300-1ca1-4606-ae16-0003e8d947b2.png)

Setelah itu, `klik kiri` pada paket yang paling atas > `follow` > `TCP Stream`
![Screenshot (470)](https://user-images.githubusercontent.com/76694068/134457223-fcdd61f5-a8b6-493a-b2bc-508e60418165.png)

Setelah keluar, ganti `Show as` dengan `Raw` lalu simpan data dalam bentuk `.zip`
![Screenshot (471)](https://user-images.githubusercontent.com/76694068/134457225-23dbe95a-d2a5-4fb3-8906-8a32024866f4.png)

Setelah tersimpan, ekstrak file dan buka pdf, maka akan muncul gambar seperti ini
![Screenshot (468)](https://user-images.githubusercontent.com/76694068/134457216-46ce016b-7f99-4524-808c-79bf450f1b24.png)


#### 8. Cari paket yang menunjukan pengambilan file dari FTP tersebut!

Isi pada Display Filter `ftp contains RETR`. RETR sendiri digunakan untuk men-download suatu file dari FTP server, jadi untuk melihat adanya pengambilan file atau tidak maka bisa dengan mencari RETR-nya
![Screenshot (485)](https://user-images.githubusercontent.com/76694068/134457743-da970cce-2fa0-4e97-81bb-b5e1a278f195.png)


#### 9. Dari paket-paket yang menuju FTP terdapat indikasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

Untuk mencari file bernama secret.zip, maka kita coba mencari menggunakan display filter `ftp-data.command contains secret.zip`. Lebih jelasnya, karena kita akan menyimpan sebuah paket yang merupakan sebuah **file** yang bernama `secret.zip` dari ftp, kita gunakan ftp-data dan kita spesifikan pencarian pada `ftp-data.command` karena kita, dapat menemukan paket saat file secret.zip tersebut diunggah pada ftp (dengan command `STOR`). Maka akan muncul tampilan seperti berikut :

![9-A](pictures/9-A.png)

Selanjutnya, untuk mendapatkan paket, kita klik kanan pada paket yang akan disimpan/diunduh, lalu menggunakan perintah follow -> TCP Stream seperti pada gambar berikut :
![9-B](pictures/9-B.png)

Setelah itu akan muncul tampilan seperti berikut :
![9-C](pictures/9-C.png)

Kita ubah `Show data as` menjadi `Raw`, lalu klik save as, dan pilih direktori tempat kita menyimpan file/paket yang akan diunduh. Ketika dibuka file memuat password. Kita masukkan password yang kita temukan pada no 10, yaitu `d1b1langbukanapaapajugagapercaya` :
![9-D](pictures/9-D.png)

Maka akan terbuka file `Wanted.pdf`-nya :
![9-E](pictures/9-E.png)

#### 10.Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

Untuk mencari file history.txt, kita gunakan display filter `ftp-data.command contains history.txt`. Penjelasannya sama dengan no 9, mengapa kita menggunakan display filter dengan expression tersebut. Maka akan muncul tampilan seperti berikut :
![10-A](pictures/10-A.png)

Berikutnya seperti tadi, kita simpan/unduh file dari paket tersebut dengan menggunakan follow -> TCP Stream, sama persis caranya dengan no 9. Ketika dibuka, file akan terlihat seperti ini :
![10-B](pictures/10-B.png)

Jika kita lihat, text tersebut mirip dengan perintah pada terminal linux. Perintah tersebut digunakan untuk melakukan `zip` pada file Wanted.pdf dan `zip` tersebut diberi nama `secret.zip`. Disinilah kita dapat menemukan kunci untuk membuka `secret.zip`. Karena pada perintah tersebut dituliskan `zip -P $key secret.zip Wanted.pdf`, dan `key = "$(tail -1 bukanapaapa.txt)"`, maka pasti password dari file `secret.zip` berkaitan dengan file bernama `bukanapaapa.txt`. Maka kita cari lagi file bernama `bukanapaapa.txt` pada wireshark dengan display filter menggunakan expression `ftp-data.command contains bukanapaapa.txt`. Hasilnya akan tampil seperti berikut :
![10-C](pictures/10-C.png)

Maka ditemukan file `bukanapaapa.txt`. Seperti tadi, kita lakukan export/unduh file dari paket tersebut menggunakan follow->TCP Stream. Ketika di buka file akan terlihat seperti ini :
![10-D](pictures/10-D.png)

Kemungkinan itulah passwordnya, yaitu `d1b1langbukanapaapajugagapercaya`. dan setelah dimasukkan ternyata berhasil. Untuk buktinya, ditunjukkan pada no 9.

#### 11. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

Karena perintah yang diberikan adalah `mengambil` maka kita memakai capture filter. Lalu menangkap paket yang berasal dari port 80 sehingga dihasilkan expression `src port 80`. src menandakan bahwa wireshark hanya akan menangkap paket yang `berasal`, lalu `port 80` sehingga menangkap paket yang berasal dari port 80.
![11-A](pictures/11-A.png)

Hasilnya :
![11-B](pictures/11-B.png)

#### 12. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

Hampir sama dengan no 11, namun disini `mengandung` sehingga entah itu `berasal` ataupun `menuju`, keduanya harus dapat ditangkap oleh wireshark, sehingga kita hanya perlu menuliskan expression pada capture filter `port 21`
![12-A](pictures/12-A.png)

Hasilnya :
![12-B](pictures/12-B.png)

#### 13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

Untuk menampilkan, maka filter yang perlu diisi adalah Display Filter. Display filter bisa diisi dengan `tcp.port == 443`
![Screenshot (486)](https://user-images.githubusercontent.com/76694068/134457943-8a0b4d08-3918-4b8a-adc8-c796bf00d9b0.png)


#### 14. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

Karena perintah yang diberikan adalah `mengambil` maka yang diisi adalah Capture Filter. Capture Filter dapat diisi `dst host kemenag.go.id`.
![Screenshot (472)](https://user-images.githubusercontent.com/76694068/134458073-80c76992-5855-45cb-8040-7d8234dbc361.png)

Maka ketika dijalankan, saat kita tidak membuka website `kemenag.go.id` maka tidak akan ada paket yang masuk. paket baru masuk saat kita membuka website tersebut.
![Screenshot (473)](https://user-images.githubusercontent.com/76694068/134458075-607583da-dfab-4269-8b63-88e453329361.png)


#### 15. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

Sebelumnya kita harus mengetahui IP Address kita terlebih dahulu. Cara mengetahuinya adalah dengan mengetikkan `ipconfig` pada command prompt. Lalu kita cari sambungan yang mengarah ke internet yang kita gunakan, dan temukan IPv4 Addressnya.
![15-A](pictures/15-A.png)

Pada gambar tersebut, diketahui IP Address yang saya gunakan adalah `192.168.43.224`. Maka kita gunakan IP yang telah kita temukan tersebut pada capture filter, karena perintah pada soal adalah `mengambil`. Lalu karena paket yang ingin ditangkap adalah `berasal`, maka digunakan expression `src`. Sehingga terbentuklah expression `src 192.168.43.224`.
![15-B](pictures/15-B.png)

Hasilnya :
![15-C](pictures/15-C.png)


## Masalah saat mengerjakan

Ada :

1. Pada nomor 7, Awal waktu file akhir disimpan dalam bentuk `.pdf`, ketika pdf-nya dibuka, gambar tidak keluar. Setelah itu dicoba menyimpan file dalam bentuk `.zip` baru kemudian di ekstrak. dan setelah itu pdf terbuka tanpa ada masalah.

2. Pada saat export file, terutama dalam bentuk `.zip` seringkali terjadi  file. Ternyata, export harus dilakukan secara perlahan hingga file benar-benar tampil secara sempurna dan bisa di export menjadi `.zip` yang openable
