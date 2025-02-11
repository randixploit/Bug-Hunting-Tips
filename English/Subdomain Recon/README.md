# 🚀 Perform Subdomain Scanning
Hello guys, for me, the first thing you need to do when you want to perform penetration testing is to scan the target’s subdomains. So, how do you do that? Okay. Here, I already have some resources that you can use to scan subdomains.\

# ⚡ Recommended Subdomain Scanner Tools
1. <a href="https://github.com/projectdiscovery/subfinder">Subfinder</a>
2. <a href="https://github.com/tomnomnom/assetfinder">Assetfinder</a>
3. <a href="https://github.com/aboul3la/Sublist3r">Sublist3r</a>
4. <a href="https://github.com/owasp-amass/amass">Amass</a>
5. <a href="https://github.com/guelfoweb/knock">Knockpy</a>

# Installation
```bash
$ go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest

$ go install github.com/tomnomnom/assetfinder@latest

$ pip install sublist3r amass knock-subdomains
```

# Terminal configuration
In the terminal (Linux) you check first, use bash or zsh. Type the command <code>echo $SHELL</code> if the output is zsh then edit the ~/.zshrc file, if it is bash then edit the ~/.bashrc file. Then you add the code at the bottom.

# Code
```shell
export PATH=$PATH:/usr/local/go/bin 
export GOPATH=$HOME/go 
export PATH=$PATH:$GOPATH/bin 
export PATH=$PATH:~/.local/bin
```

# 💻 How to use
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

# Knockpy (long)
<img src="https://raw.githubusercontent.com/randixploit/Bug-Hunting-Tips/refs/heads/main/Indonesia/Subdomain%20Recon/Screenshot_20250208-201716.jpg">

For those who want it to be simple without needing to install the tools above, you can use <a href="https://dash.pugrecon.celes.in/">PugRecon</a>

Hope this helps you, thank you.
