# Responsi Praktikum Teknologi Cloud Terapan

*Dockerfile dan Contoh Penggunaannya*

*Endah Sukma Kuncari*


Dockerfile merupakan skrip yang berisi perintah yang akan dieksekusi secara otomatisasi dan berurutan untuk
membangun sebuah image.Perintah ini biasanya beisi komponen-komponen yang akan dibutuhkan nantinya.
Dengan menjalankan perintah docker build secara otomatis docker akan menginstall seluruh komponen
yang dibutuhkan sesuai dengan intruksi di dockerfile.Setiap perintah yang memodifikasi sistem file membuat lapisan baru.


Perintah dasar dockerfile ;

FROM <image> [as <name>]

Perintah awal untuk menginisialisasikan projek baru dengan docker,Dockerfile akan valid jika terdapat FROM didalamnya.

WORKDIR /path/to/workdir

Untuk mendefinisikan direktori yang nantinya seluruh intruksi yang ada di dockerfile akan dijalankan di direktori yang disetup di WORKDIR.

COPY <src> <dest>

Digunakan untuk meng copy file baru atau direktori dari <src> dan ditambahkan di filesystem container path <dest>

RUN <command>

RUN adalah instruksi untuk menjalankan perintah

EXPOSE <port> [<port> ...]

EXPOSE adalah perintah untuk me listen nework port

CMD ["executable","param","param"]

Digunakan untuk mengeksekusi perintah yang lebih spesifik

Membuka file dokumen dockerfile

FROM node:6.11.2-alpine

WORKDIR /app

COPY package.json /app

RUN npm install

COPY . /app

EXPOSE 8080

CMD [ "npm", "start" ]


Membuat container image, masuk ke direktori aplikasi dimana kita menyimpan Dockerfile

docker build -t <your username>/start-nodejs-with-docker .

Perintah docker build akan mendownload nodejs dan berbagai keperluan lainnya yang kemudian akan di jadikan container image .
tunggu hingga selesai download. Lalu jalankan perintah docker images untuk melihat container yang telah tersedia.

Untuk Menjalankan
docker run -p 8080:8080 <username>

Image docker ini bisa dibangun mengunakan dockerfile yaitu dengan mengunakan format penulisan yaml yang digunakan docker engine untuk menciptakan suatu image berdasarkan baris perintah yang konfigurasi yang ada pada file.



