# 🚀 Melakukan Scanning Kerentanan Subdomain Takeover
Halo guys, kali ini saya akan kasi tau cara melakukan scanning kerentanan Subdomain Takeover, hal pertama yang perlu di siapkan sudah pasti list subdomain ya, kamu bisa cek cara melakukan subdomain scanning <a href='https://github.com/randixploit/Bug-Hunting-Tips/tree/main/Indonesia/Subdomain%20Recon'>di sini</a>.

# ⚡ Rekomendasi tools Subdomain Takeover (checker)
1. <a href='https://github.com/PentestPad/subzy'>Subzy</a>
2. <a href='https://github.com/xcapri/subdosec'>Subdosec</a>

# Instalasi
```
go install -v github.com/PentestPad/subzy@latest

python3 -m pip install git+https://github.com/xcapri/subdosec.git
or 
python3 -m pip install --upgrade git+https://github.com/xcapri/subdosec.git
```

# Konfigurasi terminal
Pada terminal (linux) kalian cek dulu, pake bash atau zsh. Ketik perintah echo $SHELL kalau outputnya zsh maka edit pada file ~/.zshrc, kalo bash maka edit pada file ~/.bashrc. Kemudian kalian tambahkan kode di paling bawah.

# Code
```shell
export PATH=$PATH:/usr/local/go/bin 
export GOPATH=$HOME/go 
export PATH=$PATH:$GOPATH/bin 
export PATH=$PATH:~/.local/bin
```

Kalau sudah tinggal <code>source ~/.zshrc</code> atau <code>source ~/.bashrc</code>

# Cara penggunaan
# Single scan
```bash
$ subzy r --target subdomain.domain.com

$ echo http://subdomain.domain.com | sudosec
```

# Mass scan
```bash
$ subzy r --targets subdomains.txt

$ cat subdomains.txt | subdosec
```

# Screenshots
# SUbzy
