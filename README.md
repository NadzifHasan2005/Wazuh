# Wazuh
Alat yang digunakan adalah Ubuntu, Docker, dan Wazuh



## 1. Ubuntu
Ubuntu adalah sistem operasi open-source berbasis Linux yang populer yang dikembang kan oleh Canonical Ltd. Keunggulan dan kelebihan ubuntuk adalah
1. User friendly
Ubuntu mudah dalam menginstalan dan juga memiliki tampulan pnegguna atau user interface (UI) yang mudah dipahami sehingga bisa digunakan siapapun.
2. Performanya ringan
sistem operasi ini juga mampu mengoptimalkan penggunaan resources sehingga dapat tetap beroperasi dengan lancar di perangkat yang biasa saja atau kelas bawah.
3. Gratis
Ubuntu dapat di download, digunakan, dan dibagikan oleh siapapun melalui laman web resminya tanpa harus membayar lisensi. Hal ini sesuai dengan misi Ubuntu yang ingin menghadirkan OS gratis yang dapat digunakan oleh seluruh orang di dunia.
4. Aman dan bebas dari virus
Ubuntu juga sulit diretas dan jarang menjadi sasaran empuk hacking dibandingkan kompetitornya. Ubuntu sudah memenuhi berbagai standar keamanan internasional. Bahkan, studi kasus dari Pemerintah Inggris menunjukkan bahwa Ubuntu menduduki peringkat satu dalam tes keamanan.
5. Mendukung berbagai aplikasi 
Ubuntu memiliki aplikasi “Software Center” yang dapat digunakan untuk men-download berbagai aplikasi dengan mudah.

Untuk download .iso yang digunakan (recomended):
- 20.04 (https://releases.ubuntu.com/focal/)
- 22.04 (https://releases.ubuntu.com/jammy/)

## 2. Docker
Docker platform open-source untuk mengembangkan, mengirimkan, dan menjelaskan aplikasi dalam lingkungan terisolasi yang disebut **kontainer**. Kontainer ini mengemas semua yang dibutuhkan aplikasi untuk berjalan, termasuk kode aplikasi, depedansi, runtime, dankonfigurasi sistem. 
Fungsi dari Docker adalah
1. Pebuatan dan pengemasan aplikasi
untuk memastikan bahwa aplikasi berjalan konsisten di berbagai lingkungan, mengurangi masalah yang disebabkan oleh perbedaan konfigurasi antara lingkungan pengembangan, pengujian, dan produksi.
2. Distribusi dan penyebaran aplikasi
Aplikasi dapat dengan mudah didistribusikan dan di-deploy ke berbagai lingkungan.
3. Isolasi Lingkungan
memungkinkan aplikasi untuk diskalakan dengan mudah dengan menambah atau mengurangi jumlah kontainer yang menjalankan aplikasi.

## 3. Wazuh
Wazuh adalah sebuah platform kemanan siber berbasis open-source yang digunakan untuk membantu dan melindungi sistem komputer dari ancaman. Dengan Wzuh, kita mendeteksi aktivitas mencurgakan, memantau perubahan file penting di sistem, dan memeriksa log (catatan aktivitas), dan memastikan sistem mengikuti standar aturan yang telah dibuat oleh admin server.
Fungsi wazuh:
1. Deteksi ancaman
2. Memantau Integrasi File
3. Log data analysis
4. Manjemen kerentanan
5. Compliance monitoring

Kelebihan wazuh:
1. Skalabilitas tinggi
2. Integrasi yang fleksibilitas
3. Open-source

## 4. Virtual Machine yang digunakan
a. Menggunakan 2 VM (Menggunakan Ubuntu versi 22.04)
- VM Ubuntu Original (Belum diinstall apa-apa)
- VM wazuh manager
- VM Wazuh Agent

b. Proses membuat 3 VM
- VM Ubuntu Original (Belum diinstall apa-apa)
Proses instalasi VM bisa klik link ini: https://youtu.be/rJ9ysibH768?si=vYbTyYqoQe3_Hybu
- VM wazuh manager</br>
  <img width="617" height="367" alt="image" src="https://github.com/user-attachments/assets/d816fa09-910b-434d-b901-099a2e8fcced" /></br>
  Langkahnya:
  - Klik VM Ubuntu original
  - lalu klik clone
  - Tunggu hingga selesai 
- VM Wazuh Agent</br>
  <img width="617" height="367" alt="image" src="https://github.com/user-attachments/assets/d816fa09-910b-434d-b901-099a2e8fcced" /></br>
  Langkahnya:
  - Klik VM Ubuntu original
  - Lalu klik clone
  - Tunggu hingga selesai 


## 5. Proses Instalasi Tools yang dipakai yang akan di Pakai di VM Wazuh Manager 
https://github.com/NadzifHasan2005/Wazuh/blob/main/Instalasi%20Wazuh%20dan%20Docker_VM%20Wazuh%20Manager.md

