# 🚀 Melakukan Scanning Subdomain
Halo guys, bagi saya hal pertama yang perlu lakukan saat ingin melakukan penetration testing adalah melakukan scanning pada subdomain target, lalu bagaimana caranya? Oke. Disini saya sudah punya beberapa sumber yang bisa kalian gunakan untuk melakukan scanning subdomain.

# ⚡ Rekomendasi Tools Subdomain Scanner
1. <a href="https://github.com/projectdiscovery/subfinder">Subfinder</a>
2. <a href="https://github.com/tomnomnom/assetfinder">Assetfinder</a>
3. <a href="https://github.com/aboul3la/Sublist3r">Sublist3r</a>
4. <a href="https://github.com/owasp-amass/amass">Amass</a>
5. <a href="https://github.com/guelfoweb/knock">Knockpy</a>

# Instalasi
```
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
```
$ subfinder -d domain.com -all -recursive

$ assetfinder domain.com

$ sublist3r -d domain.com

$ amass enum -d domain.com

$ knockpy -d domain.com --recon
```

# 👨‍💻 Mass scan
```
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

Untuk yang pengen simpel tanpa perlu install tools2 di atas kalian bisa pakai <a href="https://dash.pugrecon.celes.in/">PugRecon</a>

Semoga ini bisa membantu kalian, terima kasih.
