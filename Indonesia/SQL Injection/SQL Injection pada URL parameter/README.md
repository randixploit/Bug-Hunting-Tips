# 🚀 Cara Mencari Kerentanan SQL Injection pada URl parameter

Apa itu Injeksi SQL? SQL Injection adalah kerentanan keamanan yang terjadi ketika penyerang memasukkan perintah SQL berbahaya ke dalam input aplikasi, seperti parameter atau formulir URL, untuk mengakses, mengubah, atau menghapus data dalam database. Kerentanan ini biasanya muncul karena aplikasi tidak memvalidasi input dengan benar, sehingga memungkinkan eksekusi perintah SQL yang tidak diinginkan. Akibatnya, penyerang dapat mencuri informasi sensitif, mengubah data, atau bahkan mengambil kendali sistem. 


# ⚠️ Perhatian

Konten ini sepenuhnya bertujuan untuk edukasi saja, guna meningkatkan kesadaran akan pentingnya keamanan dalam suatu sistem dan mendorong seluruh hacker untuk lebih bijak dalam menggunakan ilmu yang didapat, bukan menggunakan ilmu yang diperoleh untuk tujuan merugikan orang lain.


# ⚡ Refrensi

1. https://portswigger.net/web-security/sql-injection
2. https://vt.tiktok.com/ZSM2LKvq2/


Oke, hal pertama yang perlu dilakukan adalah mencari parameter sebanyak-banyaknya untuk menguji apakah memiliki kerentanan atau tidak, disini saya menggunakan beberapa tools yaitu: 

1. <a href="https://github.com/tomnomnom/waybackurls">Waybackurls</a>
2. <a href="https://github.com/projectdiscovery/katana">Katana</a> 
3. <a href="https://github.com/projectdiscovery/urlfinder">Urlfinder</a>


# 👨‍💻 Perintah

```shell
# waybackurls
cat subomain_aktif.txt | waybackurls | tee waybackurls.txt 

#katana 
katana -list subdomain_aktif.txt -o katana.txt 

# urlfinder 
cat subdomain_aktif.txt | sed 's|http://||g' | sed 's|https://||g' | sed 's|/||g' | urlfinder -all | uro | tee urlfinder.txt 

# menggabungkan semua daftar url menjadi satu file, sekaligus menghapus domain duplikat dan serupa
cat waybackurls.txt katana.txt urlfinder.txt | uro | tee allurl.txt
```

Setelah memiliki daftar URL, kamu harus mengumpulkan URL yang memiliki parameter, disini saya menggunakan perintah yang memiliki filter seperti jpg, css dan ekstensi file yang tidak bisa diinjeksi sama sekali.

# 👨‍💻 Perintah

```shell
cat allurl.txt | grep -vE '\.(css|jpg|jpeg|JPG|JPEG|png|PNG|ico|ttf|woff|woff2|svg|swf|js|mp4|mp3|mkv|eot|pdf|7z|tar|gz|zip)' | grep -vE "wp-content|wp-login|wp-includes|wp-json|wp-admin|wp-sitemap|suspendedpage.cgi|wordfence|fbclid|wc-ajax|xmlrpc.php" | grep -vE "=(rss|atom|comments-rss2|xml)" | uro | grep = | httpx -mc 200 -timeout 60 -o sqli.txt
```

Jika kamu sudah memiliki daftar url yang siap dipindai, kamu memerlukan alat lain. Tool yang saya maksud disini adalah tool sqli scanner. Seperti sqlmap, ghauri, loxs dan alat pemindai lainnya. disini saya menggunakan alat sqlmap. Sebenarnya lebih disarankan menggunakan alat yang dikhususkan untuk scanner atau checker seperti Loxs agar tidak memakan waktu lama. Tapi saya terlalu malas untuk mengkonfigurasi toolnya jadi saya pakai sqlmap saja wkwk 😂. 

# 👨‍💻 Perintah

```shell
sqlmap -m sqli.txt --random-agent --batch -v3 --tamper space2comment,between,randomcase --flush-session --time-sec 10
```


# 🖼️ Screenshot 

<img src="https://github.com/randixploit/Bug-Hunting-Tips/blob/main/Indonesia/SQL%20Injection/SQL%20Injection%20pada%20URL%20parameter/IMG_20250216_175246_878.jpg?raw=true">


Disini saya tidak membuang databasenya karena bagi saya itu melanggar hukum, karena kami sebagai pentester tidak mempunyai izin lebih lanjut untuk itu. Namun, hal ini juga diperlukan jika kamu melaporkan kerentanan seperti injeksi SQL yang mengharuskan kamu membuang database untuk mendapatkan bukti kuat. Semoga bermanfaat dan bisa digunakan untuk hal yang baik, bukan untuk kegiatan yang jahat ya 👌.
