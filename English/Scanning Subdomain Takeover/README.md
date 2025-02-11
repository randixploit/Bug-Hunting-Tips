# 🚀 Perform Subdomain Takeover Vulnerability Scanning
Hello guys, this time I will tell you how to do a Subdomain Takeover vulnerability scan, the first thing you need to prepare is definitely a list of subdomains, you can check how to do a subdomain scanning <a href='https://github.com/randixploit/Bug-Hunting-Tips/tree/main/Indonesia/Subdomain%20Recon'>here</a>.

# ⚡ Recommended Subdomain Takeover tools (checker)
1. <a href='https://github.com/PentestPad/subzy'>Subzy</a>
2. <a href='https://github.com/xcapri/subdosec'>Subdosec</a>

# Installation
```
go install -v github.com/PentestPad/subzy@latest

python3 -m pip install git+https://github.com/xcapri/subdosec.git
or 
python3 -m pip install --upgrade git+https://github.com/xcapri/subdosec.git
```

# Terminal configuration
# Code
```shell
export PATH=$PATH:/usr/local/go/bin 
export GOPATH=$HOME/go 
export PATH=$PATH:$GOPATH/bin 
export PATH=$PATH:~/.local/bin
```

If so, just <code>source ~/.zshrc</code> or <code>source ~/.bashrc</code>

# How to use
# 👨‍💻 Single scan
```bash
$ subzy r --target subdomain.domain.com

$ echo http://subdomain.domain.com | sudosec
```

# 👨‍💻 Mass scan
```bash
$ subzy r --targets subdomains.txt

$ cat subdomains.txt | subdosec
```

# 🖼️ Screenshots
# SUbzy
<img src='https://raw.githubusercontent.com/randixploit/Bug-Hunting-Tips/refs/heads/main/Indonesia/Scanning%20Subdomain%20Takeover/Screenshot_20250211_103656.png'>

# Subdosec
<img src='https://raw.githubusercontent.com/randixploit/Bug-Hunting-Tips/refs/heads/main/Indonesia/Scanning%20Subdomain%20Takeover/Screenshot_20250211_103922.png'>

If you find a subdomain that is vulnerable, immediately report it to the IT team or website manager, unless you have additional permission to carry out a takeover on the subdomain to strengthen evidence of vulnerability.

Hope it is useful.
