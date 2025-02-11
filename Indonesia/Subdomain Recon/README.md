# 🚀 Melakukan Scanning Subdomain
Halo guys, bagi saya hal pertama yang perlu lakukan saat ingin melakukan penetration testing adalah melakukan scanning pada subdomain target, lalu bagaimana caranya? Oke. Disini saya sudah punya beberapa sumber yang bisa kalian gunakan untuk melakukan scanning subdomain.

# ⚡ Rekomendasi Tools Subdomain Scanner
1. <a href="https://github.com/projectdiscovery/subfinder">Subfinder</a>
2. <a href="https://github.com/tomnomnom/assetfinder">Assetfinder</a>
3. <a href="https://github.com/aboul3la/Sublist3r">Sublist3r</a>
4. <a href="https://github.com/owasp-amass/amass">Amass</a>
5. <a href="https://github.com/guelfoweb/knock">Knockpy</a>

# Instalasi
```bash
$ go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest

$ go install github.com/tomnomnom/assetfinder@latest

$ pip install sublist3r amass knock-subdomains
```

# Konfigurasi terminal
Pada terminal (linux) kalian cek dulu, pake bash atau zsh. Ketik perintah <code>echo $SHELL</code> kalau outputnya zsh maka edit pada file ~/.zshrc, kalo bash maka edit pada file ~/.bashrc. Kemudian kalian tambahkan kode di paling bawah.

# Code
```shell
export PATH=$PATH:/usr/local/go/bin 
export GOPATH=$HOME/go 
export PATH=$PATH:$GOPATH/bin 
export PATH=$PATH:~/.local/bin
```

# 💻 Cara penggunaan 
# 👨‍💻 Single Scan
```bash
$ subfinder -d domain.com -all -recursive

$ assetfinder domain.com

$ sublist3r -d domain.com

$ amass enum -d domain.com

$ knockpy -d domain.com --recon
```

# 👨‍💻 Mass scan
```bash
$ subfinder -dL list.txt -all -recursive

$ cat list.txt | assetfinder

$ cat list.txt | while read domain; do sublist3r -d $domain; done

$ cat list.txt | while read domain; do amass enum -d $domain; done
```

# 🖼️ Screenshot 
# Subfinder
<img src="https://raw.githubusercontent.com/randixploit/Bug-Hunting-Tips/refs/heads/main/Indonesia/Subdomain%20Recon/Screenshot_20250208-195951.jpg">

# Assetfinder
<img src="https://raw.githubusercontent.com/randixploit/Bug-Hunting-Tips/refs/heads/main/Indonesia/Subdomain%20Recon/Screenshot_20250208-195543.jpg">

# Sublist3r
<img src="https://raw.githubusercontent.com/randixploit/Bug-Hunting-Tips/refs/heads/main/Indonesia/Subdomain%20Recon/Screenshot_20250208-200254.jpg">

# Amass
<img src="https://github.com/randixploit/Bug-Hunting-Tips/blob/main/Indonesia/Subdomain%20Recon/Screenshot_20250208-200855.jpg">

# Knockpy (lama)
<img src="https://raw.githubusercontent.com/randixploit/Bug-Hunting-Tips/refs/heads/main/Indonesia/Subdomain%20Recon/Screenshot_20250208-201716.jpg">

Sekarang bagaimana cara mengetahui subdomain mana saja kah yang masih aktif untuk sekarang? saya punya cara untuk mengecek hal tersebut, kalian tinggal pakai tools <a href='https://github.com/projectdiscovery/httpx'>Httpx</a> atau <a href='https://github.com/tomnomnom/httprobe'>Httprobe</a>, kalian bisa pakai salah satunya untuk memfilter subdomain, untuk cara penginstalannya sudah ada di halaman github nya, baiklah untuk memfilter subdomain yang masih aktf kalian tinggal pakai command seperti ini:

# Code
```bash
# menggunakan httpx
httpx -l subdomains -o alive.txt

# menggunakan httprobe
cat subdomains.txt | httprobe | tee alive.txt
```


Semoga ini bisa membantu kalian, terima kasih.
