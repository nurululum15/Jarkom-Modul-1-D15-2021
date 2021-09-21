# Laporan Praktikum Modul 1

## SOAL

### 1. Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!

### 2. Temukan paket dari web-web yang menggunakan basic authentication method!

Karena yang dicari adalah paket maka isi display filter adalah `http.authbasic`

![Screenshot (475)](https://user-images.githubusercontent.com/76694068/134185295-02284804-a8c8-4f57-a8e4-0808a4822d1a.png)


### 3. Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkandari file .pcapng!

Pertama, isi display filter dengan `http.host contains basic.ichimarumaru.tech` > klik paket paling atas.
![Screenshot (461)](https://user-images.githubusercontent.com/76694068/134185981-b4914c75-d362-4740-acfc-8a3432a88ee9.png)

Kedua, cari `Hyper Text Protocol` > `Authorization` maka di Credentials ada username dan password yang dipakai
![Screenshot (462)](https://user-images.githubusercontent.com/76694068/134185997-4d96d446-b5cf-4238-9b85-8916d0eeb1b2.png)

Ketiga, untuk mencopy password dan username tersebut, `klik kiri` > `Copy` > `Value` lalu Pastekan pada suatu media 
![Screenshot (476)](https://user-images.githubusercontent.com/76694068/134186808-a653d696-4dc0-4628-aca5-6fdf1af602c8.png)

Terakhir, jika username dan password tadi dimasukkan, maka website `basic.ichimarumaru.tech` akan terbuka
![Screenshot (465)](https://user-images.githubusercontent.com/76694068/134186001-eee6f033-8d05-44cc-baea-e16a7cb4d784.png)

### 4. Temukan paket mysql yang mengandung perintah query select!

Mengisi display filter dengan `mysql contains select or mysql contains SELECT` karena ada select yang menggunakan kapital dan tidak.

![Screenshot (464)](https://user-images.githubusercontent.com/76694068/134187633-05e65f2d-4981-4f8d-bc3a-b1f0c5e1fd8c.png)


### 5. Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username danpassword bisa didapat dari query insert pada table users dari file .pcap!

### 6. Cari username dan password ketika melakukan login ke FTP Server!

Mengisi display filter dengan `ftp.request.command == "USER" || ftp.request.command == "PASS"`

![Screenshot (467)](https://user-images.githubusercontent.com/76694068/134188079-24747c98-55b8-47b6-8286-2b45bbbe8cc5.png)


### 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

### 8. Cari paket yang menunjukan pengambilan file dari FTP tersebut!

### 9. Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

### 10.Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

### 11. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

### 12. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

### 13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

### 14. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

### 15. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
