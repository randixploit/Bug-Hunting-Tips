# 🚀 How to Look for SQL Injection Vulnerabilities in URL parameters

What is SQL Injection? SQL Injection is a security vulnerability that occurs when an attacker injects malicious SQL commands into application input, such as URL parameters or forms, to access, modify, or delete data in a database. These vulnerabilities typically arise because the application does not properly validate input, allowing execution of undesired SQL commands. As a result, attackers can steal sensitive information, modify data, or even take control of the system.


# ⚠️ Attention 

This content is intended entirely for educational purposes only, to increase awareness of the importance of security in a system and encourage all hackers to be wiser in using the knowledge they have gained, not to use the knowledge they have gained for the purpose of harming other people.

# ⚡ References

1. https://portswigger.net/web-security/sql-injection
2. https://vt.tiktok.com/ZSM2LKvq2/


OK, the first thing you need to do is look for as many parameters as possible to test whether there is a vulnerability or not, here I use several tools, namely: 

1. <a href="https://github.com/tomnomnom/waybackurls">Waybackurls</a>
2. <a href="https://github.com/projectdiscovery/katana">Katana</a>
3. <a href="https://github.com/projectdiscovery/urlfinder">Urlfinder</a>


# 👨‍💻Command

```shell
# waybackurls
cat subdomains_alive.txt | waybackurls | tee waybackurls.txt

# katana
katana -list subdomains_alive.txt -o katana.txt

# urlfinder
cat subdomains_alive.txt | sed 's|http://||g' | sed 's|https://||g' | sed 's|/||g' | urlfinder -all | uro | tee urlfinder.txt

# merge all url lists into one file, while removing duplicate and similar domains
cat waybackurls.txt katana.txt urlfinder.txt | uro | tee allurl.txt
```

After having a list of URLs, you have to collect URLs that have parameters, here I use a command that has filters such as jpg, css and file extensions that cannot be injected at all.

# 👨‍💻 Command

```shell
cat allurl.txt | grep -vE '\.(css|jpg|jpeg|JPG|JPEG|png|PNG|ico|ttf|woff|woff2|svg|swf|js|mp4|mp3|mkv|eot|pdf|7z|tar|gz|zip)' | grep -vE "wp-content|wp-login|wp-includes|wp-json|wp-admin|wp-sitemap|suspendedpage.cgi|wordfence|fbclid|wc-ajax|xmlrpc.php" | grep -vE "=(rss|atom|comments-rss2|xml)" | uro | grep = | httpx  -mc 200 -timeout 60 -o sqli.txt
```

If you already have a list of URLs ready to be scanned, you'll need another tool. The tool I mean here is the SQLI Scanner tool. Such as sqlmap, ghauri, loxs and other scanning tools. here I use the sqlmap tool. In fact, it is more advisable to use a tool specifically for scanners or checkers such as Loxs so that it doesn't take a long time. But I'm too lazy to configure the tool so I just use sqlmap hahaha 😂.

# 👨‍💻 Command

```shell
sqlmap -m sqli.txt --random-agent --batch -v3 --tamper space2comment,between,randomcase --flush-session --time-sec 10
```

# 🖼️ Screenshots 

<img src="https://github.com/randixploit/Bug-Hunting-Tips/blob/main/Indonesia/SQL%20Injection/SQL%20Injection%20pada%20URL%20parameter/IMG_20250216_175246_878.jpg?raw=true"> 


Here I do not throw away the database because for me it is against the law, because we as pentesters do not have further permission for that. However, this is also necessary if you are reporting a vulnerability such as SQL injection that requires you to dump the database to obtain hard evidence. Hopefully it's useful and can be used for good things, not for evil activities, OK 👌
