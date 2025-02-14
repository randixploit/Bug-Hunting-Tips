# Cross Site Tracing (XST)
Apa itu XST? Singkatnya XST (Cross-Site Tracing) adalah jenis serangan web yang memanfaatkan metode HTTP TRACE untuk mencuri informasi sensitif, seperti cookie atau header otentikasi. Serangan ini bekerja dengan menggabungkan XSS (Cross-Site Scripting) untuk membaca respons TRACE, yang biasanya berisi data yang dikirimkan oleh pengguna. XST dapat dieksploitasi jika server mengizinkan metode TRACE dan tidak memiliki perlindungan yang memadai.

# Cara melakukan serangan XST
Untuk melakukan serangan XST kalian hanya bisa menggunakan curl command dari terminal. sebenarnya bisa menggunakan cara lain seperti lewat burp suite atau semacamnya, tetapi itu ribet. lebih baik yang simpel aja.

# Perintah
```
curl -X TRACE http://example.com -b "sessionId=mallicious_value"

curl -X TRACE http://example.com -H "Test-XST: Just_R"
```

Nah seperti kalian lihat pada perintah diatas, Perintah ini menguji apakah server mendukung metode HTTP TRACE dan apakah cookie yang dikirim akan dipantulkan dalam respons. Jika ya, bisa dieksploitasi untuk mencuri informasi sensitif melalui serangan XST.

# Screenshots
