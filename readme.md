### Node Express Https Api 
-  参考链接 (http://www.appinn.com/markdown/)
- express  如何使用 HTTPS服务器
```$xslt
   HTTP: 超文本传输协议 (Hypertext transfer protocol) 是一种详细规定了浏览器和万维网服务器之间互相通信的规则，
   通过因特网传送万维网文档的数据传送协议。 
```
```$xslt
  HTTPS:（Hypertext Transfer Protocol over Secure Socket Layer），是以安全为目标的HTTP通道，简单讲是HTTP的安全版。
  即HTTP下加入SSL层，HTTPS的安全基础是SSL，因此加密的详细内容就需要SSL。 它是一个URI scheme（抽象标识符体系），句法类同http:体系。
  用于安全的HTTP数据传输。https:URL表明它使用了HTTP，但HTTPS存在不同于HTTP的默认端口及一个加密/身份验证层（在HTTP与TCP之间）。
  这个系统的最初研发由网景公司进行，提供了身份验证与加密通讯方法，现在它被广泛用于万维网上安全敏感的通讯，例如交易支付方面。
```
-  区别
```$xslt
    * https协议需要到ca申请证书，一般免费证书很少，需要交费。
    * http是超文本传输协议，信息是明文传输，https 则是具有安全性的ssl加密传输协议。
    * http和https使用的是完全不同的连接方式，用的端口也不一样，前者是80，后者是443。
    * http的连接很简单，是无状态的；HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，比http协议安全。
```
### 在项目中使用
###### 使用 openssl 生产证书文件
- openssl genrsa 1024 > private.pem  //＃通过私钥文件生成CSR证书签名
- openssl req -new -key private.pem -out csr.pem //＃通过私钥文件生成CSR证书签名
- openssl x509 -req -days 365 -in csr.pem -signkey private.pem -out file.crt //＃通过私钥文件和CSR证书签名生成证书文件
######   生产三个文件
```$xslt
private.pem: 私钥
csr.pem: CSR证书签名
file.crt: 证书文件
```
### 详细使用方式
参考 app.js 