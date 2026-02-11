# Dokumentasi Wazuh
---
## 1.  Ensure /tmp is a separate partition</br>
<img width="1798" height="682" alt="Screenshot 2026-02-10 095352" src="https://github.com/user-attachments/assets/79b41d53-d168-4089-8680-978939ec779d" />

**ID**&emsp;&emsp;&emsp;: 28500</br>
**Target**&emsp; : Command: findmnt --kernel /tmp</br>
**Level**&emsp;         : 1<br>
**Tujuan**              : Membuat `/tmp` sebagai sistem berkas tersendiri memungkinkan administrator untuk menetapkan opsi mount tambahan, seperti opsi noexec pada mount, sehingga /tmp tidak dapat digunakan oleh penyerang untuk menginstal kode eksekusi.</br>
**Langkah-langkahnya**  :</br>
1. Gunakan command `sudo systemctl unmask tmp.mount`, fungsinya untuk persyaratan konfigurasi khusus mount /tmp pada lingkungan VM.
2. Modifiksasi file /etc/fstab, dengan command `sudo nano /etc/fstab`.
3. Ketika sudah masuk, masukkan command
   ```
   tmpfs /tmp tmpfs defaults,rw,nosuid,nodev,noexec,relatime,size=2G 0 0
   ```
   seperti ini </br>
   <img width="879" height="412" alt="image" src="https://github.com/user-attachments/assets/2c7f4a1f-b584-4586-b60d-30578af5f11c" />
4. Lalu, `ctrl+x`, lanjut `y`. restart wazuh agent, masukkan command
   ```
   sudo systemctl restart wazuh-agent
   ```
5. Hasilnya seperti dibawah ini</br>
   <img width="817" height="32" alt="image" src="https://github.com/user-attachments/assets/6e45e86c-7126-45f8-9624-909407135df4" />

---

## 2. Ensure noexec option set on /var/tmp partition<br>
<img width="826" height="472" alt="ID 28508_Ensure noexec option set on var tmp partition" src="https://github.com/user-attachments/assets/26ad7807-435e-488a-af9f-f370735def08" />

**ID**: 28508</br>
**Target**: Command: findmnt --kernel /var/tmp</br>
**Level**         : 1<br>
**Tujuan**              : Tujuannya untuk memastikan bahwa pengguna tidak dapat menjalankan berkas biner yang dapat dieksekusi dari /var/tmp.</br>
**Langkah-langkahnya**  :</br>
1. Modifiksasi file /etc/fstab, dengan command `sudo nano /etc/fstab`.
2. Masukan command
   ```
   /tmp /var/tmp none bind 0 0
   ```
   <img width="861" height="320" alt="image" src="https://github.com/user-attachments/assets/21285ae3-ee53-4a34-89f0-62cdf5166c7f" />
3. Lalu, `ctrl+x`, lanjut `y`. masukkan command dibawah untuk melakukan verifikasi
   ```
   findmnt --kernel /var/tmp
   ```
   <br><img width="707" height="52" alt="image" src="https://github.com/user-attachments/assets/9aa6f003-21b3-40b1-b21e-19fe68d366fb" />
   Jika seperti digambar, sudah berjalan dengan baik.
4. Jika sudah, masukkan untuk merestart agent
   ```
   sudo systemctl restart wazuh-agent
   ```
5. Hasilnya seperti dibawah ini</br>
   <img width="823" height="36" alt="image" src="https://github.com/user-attachments/assets/c1eb86f5-da1a-48e1-bcca-565c1b37774b" />

---

## 3. Ensure AIDE is installed
<img width="833" height="502" alt="ID 28526_Ensure AIDE is Installed" src="https://github.com/user-attachments/assets/f99437df-eb56-493f-aa57-ca7a8809dc0b" />

**ID**: 28526</br>
**Target**: Command: dpkg-query -s aide</br>
**Level**         : 1<br>
**Tujuan**        : Tujuannya  untuk mencegah atau membatasi paparan konfigurasi yang salah secara tidak sengaja atau disengaja, atau berkas biner yang dimodifikasi.</br>
**Langkah-langkahnya**  :</br>
1. Verifikasi terlebih dahulu, apakah sudah terinstall atau belum
   ```
   sudo dpkg-query -s aide &>/dev/null && echo "aide is installed"
   ```
   ```
   sudo dpkg-query -s aide-common &>/dev/null && echo "aide-common is installed"
   ```
   Jika belum lanjut langkah ke 2
2. Instalasi AIDE
   ```
   sudo apt install aide aide-common

   ```
3. Menginisialisasi AIDE:
   ```
   aideinit
   ```
   Fungsi `aidetinit` untuk membuat database awal (baseline) untuk AIDE.
   ```
    mv /var/lib/aide/aide.db.new /var/lib/aide/aide.db
   ```
   Fungsi `mv /var/lib/aide/aide.db.new /var/lib/aide/aide.db` untuk mengganti database lama dengan database baru.
4. Jika sudah, masukkan untuk merestart agent
   ```
   sudo systemctl restart wazuh-agent
   ```
5. Hasilnya adalah
   <img width="833" height="31" alt="image" src="https://github.com/user-attachments/assets/6e0919e4-8472-456e-b8e7-f0c4e591cdec" />

