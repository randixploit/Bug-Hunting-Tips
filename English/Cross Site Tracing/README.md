# 🚀 Cross Site Tracing (XST)

What is XST? In short, XST (Cross-Site Tracing) is a type of web attack that exploits the HTTP TRACE method to steal sensitive information, such as cookies or authentication headers. This attack works by combining XSS (Cross-Site Scripting) to read the TRACE response, which typically contains user-submitted data. XST can be exploited if the server allows the TRACE method and lacks proper protections.

# 💻 How to Perform an XST Attack

To perform an XST attack, you can only use the curl command from the terminal. While other methods, such as using Burp Suite, are possible, they can be complicated. It's better to keep it simple.

# 👨‍💻 Command
```shell
curl -X TRACE http://example.com -b "sessionId=mallicious_value"

curl -X TRACE http://example.com -H "Test-XST: Just_R"
```

As you can see from the command above, it tests whether the server supports the HTTP TRACE method and whether the sent cookie is reflected in the response. If so, it can be exploited to steal sensitive information through an XST attack.

# 🖼️ Screenshots
<img src="https://raw.githubusercontent.com/randixploit/Bug-Hunting-Tips/refs/heads/main/Indonesia/Cross%20Site%20Tracing/20250215_032432.jpg">

That's all from me. I hope the material I provided is easy to understand, even though the explanation may still be lacking. Regards.
