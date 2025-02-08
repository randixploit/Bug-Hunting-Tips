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

# Cara penggunaan 
# Single Scan
```
subfinder -d domain.com -all -o subdomains.txt
assetfinder domain.com | tee subdomains.txt
sublist3r -d domain.com -o subdomains.txt
```
