# How-To-Install-CWP-in-centOS
CWP (centOS Web Panel) merupakan control panel gratis yang dibuat khusus untuk VM/Server yang menggunakan OS centOS pada semua generasi centOS yang masih didukung oleh pengembang untuk detail OS centOS yang masih didukung dapat dilihat pada tautan berikut: https://wiki.centos.org/About/Product

## Persiapan
- Menggunakan layanan VM XXS CPU (1 core) RAM (1GB)
- Menggunakan OS CentOS yang masih disupport yaitu centOS 7 dan centOS 8 Stream
- Menyiapkan root domain baik nasional ataupun internasional (domain.tld)

## Langkah Instalasinya
#### Step 1: Melakukan Perubahan Port SSH
Pada langkah pertama ini kami akan menggunakan OS centOS 7 namun nantinya kami juga akan menampilkan langkah untuk installasi yang menggunakan centOS 8 Stream dan berikut langkahnya:

Langkah pertama ialah kita coba login langsung ke user root VM dengan perintah sebagai berikut:

> ```$ ssh root@ipaddress```

Selanjutnya setelah kita berhasil login kita ubah dulu port ssh sebagai antisipasi serangan keamanan dengan perintah sebagai berikut:

> ```$ vim /etc/ssh/sshd_config```

Setelah muncul text editor, maka kita cari informasi port, hapus pagar dan ubah menjadi port yang diinginkan disini kami menggunakan port 2211, simpan dan restart service ssh, berikut perintah yang kami jalankan.

> ```$ systemctl restart sshd_config```

Jika terjadi error silakan mencoba melihatnya dengan perintah:

> ```$ systemctl status sshd_config```

Setelah service SSH berjalan normal kita coba log out dan mencoba login lagi dengan perintah:

> ```$ ssh root@ipaddress -p2211```


#### Step 2: Melakukan Perubahan Hostname dan Update OS
Setelah kita melakukan perubahan port SSH, selanjutnya kita ubah dulu hostname VM kita dengan perintah:

> ```$ hostname srv1.example.com```

Apabila sudah selesai langkah selanjutnya ialah melakukan update OS pada VM dengan perintah:

> ```$ yum update -y ```

Tunggu hingga proses update selesai.

#### Step 3: Melakukan Instalasi CWP pada OS CentOS 7  (recommended)
Setelah update selesai kita coba untuk melakukan installasi CWP dan berikut langkahnya:
Langkah pertama kita masuk ke folder src dan berikut perintahnya:

> ```$ cd /usr/local/src```

Langkah kedua kita download file CWP yang dibutuhkan dengan perintah wget berikut:

> ```$ wget http://centos-webpanel.com/cwp-el7-latest```
> ```$ yum -y install wget (jika wget belum terinstall)```

Langkah terakhir kita tinggal jalankan perintah bash untuk melakukan deploy/installasi CWP dan berikut detail perintahnya:

> ```$ sh cwp-el7-latest```

Tunggu hingga proses intallasi selesai, jika berhasil akan terdapat informasi url login ke portal CWP.

```#############################
#      CWP Installed        #
#############################

Go to CentOS WebPanel Admin GUI at http://SERVER_IP:2030/

http://Ip_Address:2030
SSL: https://Ip_Address:2031
---------------------
Username: root
Password: ssh server root password
MySQL root Password: Qw24Q7ZZDWZn

#########################################################
          CentOS Web Panel MailServer Installer          
#########################################################
SSL Cert name (hostname): nol1-els2.localhost
SSL Cert file location /etc/pki/tls/ private|certs
#########################################################

Visit for help: www.centos-webpanel.com
Write down login details and press ENTER for server reboot!
Loaded plugins: fastestmirror
Cleaning repos: base cwp epel extras mariadb updates
Cleaning up list of fastest mirrors
Please reboot the server!
Reboot command: shutdown -r now
```

Terakhir coba akses url yang diberikan, kemudian coba akses dengan credentian user dan password sama dengan VM

![Tampilan](https://user-images.githubusercontent.com/38468795/205562850-0515c785-5d6f-476b-94f5-57e353c0c891.png)

#### Step 4: Melakukan Instalasi CWP pada OS CentOS 8, Alma Linux & Rocky Linux
Untuk installasi pada OS CentOS 8, Alma Linux & Rocky linux hampir sama dengan proses installasi pada OS CentOS7, namun hanya berbeda pada file yang didownload dan dijalankan saja, berikut detailnya:

Langkah pertama kita masuk ke folder src dan berikut perintahnya:

> ```$ cd /usr/local/src```

Langkah kedua kita download file CWP yang dibutuhkan dengan perintah wget berikut:

> ```$ wget http://centos-webpanel.com/cwp-el8-latest```
> ```$ yum -y install wget (jika wget belum terinstall)```

Langkah terakhir kita tinggal jalankan perintah bash untuk melakukan deploy/installasi CWP dan berikut detail perintahnya:

> ```$ sh cwp-el8-latest```

Tunggu hingga proses intallasi selesai, jika berhasil akan terdapat informasi url login ke portal CWP.

```#############################
#      CWP Installed        #
#############################

Go to CentOS WebPanel Admin GUI at http://SERVER_IP:2030/

http://Ip_Address:2030
SSL: https://Ip_Address:2031
---------------------
Username: root
Password: ssh server root password
MySQL root Password: Qw24Q7ZZDWZn

#########################################################
          CentOS Web Panel MailServer Installer          
#########################################################
SSL Cert name (hostname): nol1-els2.localhost
SSL Cert file location /etc/pki/tls/ private|certs
#########################################################

Visit for help: www.centos-webpanel.com
Write down login details and press ENTER for server reboot!
Loaded plugins: fastestmirror
Cleaning repos: base cwp epel extras mariadb updates
Cleaning up list of fastest mirrors
Please reboot the server!
Reboot command: shutdown -r now
```

Terakhir coba akses url yang diberikan, kemudian coba akses dengan credentian user dan password sama dengan VM

![Tampilan](https://user-images.githubusercontent.com/38468795/205562850-0515c785-5d6f-476b-94f5-57e353c0c891.png)



**Sumber Referensi installasi CWP**: https://control-webpanel.com/installation-instructions#step4 

