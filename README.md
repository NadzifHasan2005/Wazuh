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

## 4. Langkah-Langkah install Docker dan wazuh, dan penggunaan wazuh di docker
**a.  Intall Docker**
- Buat file bernama `docker.sh`, dengan menggunakan command
  ```
  nano docker.sh
  ```
- Lalu masukkan sintaks seperti ini di file `docker.sh`
  ```
  # Add Docker's official GPG key:
  sudo apt update
  sudo apt install ca-certificates curl
  sudo install -m 0755 -d /etc/apt/keyrings
  sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
  sudo chmod a+r /etc/apt/keyrings/docker.asc
  
  # Add the repository to Apt sources:
  sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
  Types: deb
  URIs: https://download.docker.com/linux/ubuntu
  Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
  Components: stable
  Signed-By: /etc/apt/keyrings/docker.asc
  EOF
  
  sudo apt update
  ```
- Masukkan command
  ```
  sudo chmod +x docker.sh
  ```  
- lalu install docker dengan command
  ```
  ./docker.sh
  ```
- Jika sudah selesai, masukkan command dbawah untuk install docker packages
  ```
  sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  ```
- Setelah masukin command diatas dan sudah selesai, masukkan command dibawah untuk memastikan docker sudah berjalan
  ```
  sudo systemctl status docker
  ```
  nanti hasilnya,</br>
  <img width="721" height="407" alt="image" src="https://github.com/user-attachments/assets/29eae0f6-91d3-4a5a-acec-c83328f7bd71" />
- Sudah statusnya active lalu ketik command
  ```
  sudo docker run hello-world
  ```
  Jika gambar seperti dibawah, akhirnya berhasil🎉🎉🥳
  <img width="778" height="403" alt="image" src="https://github.com/user-attachments/assets/c96ff14b-84bc-4d7e-accf-8e4beefaa00a" />





b. Install wazuh di dalam docker
- Sebelum menginstall, wazuh install terlebih dahulu `git`. Dengan command
  ```
  sudo apt install git -y
  ```
  Jika sudah selesai, masukkan command dibawah untuk memastikan sudah terinstall atau belum
  ```
  git --version
  ```
- Setelah selesai intall `git`, lalu masukkan command dibawah ini untuk proses perinstallah.
  ```
  git clone https://github.com/wazuh/wazuh-docker.git -b v4.7.2
  ```
- Lalu masuk ke diktionari, dengan memasukkan command dibawah
  ```
  cd wazuh-docker/single-node
  ```
- Lalu masukkan command dibawah untuk menjalankan sebuah kontainer sementara yang tugas utamanya adalah membuat sertifikat SSL/TLS
  ```
  sudo docker compose -f generate-indexer-certs.yml run --rm generator
  ```
- lalu masukkan command dibawah ini. Gunanya unutk menjalankan seluruh layanan container
  ```
  sudo docker compose up -d
  ```
- Jika sudah pulling semua, _copy_ ip vm ubuntu anda.
- Jika sudah paste di chrome windows. tampilan akan seperti ini</br>
  <img width="1918" height="952" alt="image" src="https://github.com/user-attachments/assets/fd67c225-6a54-402f-817a-c4eff50fc290" />
- Masukkan user name dan password </br>
  User        = `admin`</br>
  Password    = `SecretPassword`
- Jika tampilan sudah seperti dibawah ini, berarti anda sudah berhasil🥳🥳🎉🎉
  <img width="1918" height="905" alt="image" src="https://github.com/user-attachments/assets/31bb8e37-e2f5-4f19-b201-44ba3a845f29" />
 
