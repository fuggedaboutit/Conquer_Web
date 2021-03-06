# HTTP vs HTTPS

## ๐ค What is HTTP?

<br>

- **`Hypertext Transfer Protocol`** ์ ์ฝ์๋ก **server์ธก์์ client ๋ธ๋ผ์ฐ์ ๋ก ์นํ์ด์ง๋ฅผ ์ฒ๋ฆฌ, ๋ ๋๋ง ๋ฐ ์ ๋ฌ** ํ๋๋ฐ ์ฌ์ฉ๋๋ ํ๋กํ ์ฝ, ์ฆ ํต์  ๊ท์ฝ์ ์๋ฏธํฉ๋๋ค!. ๋ฐ๋ผ์ HTTP๋ ์น์ด ํ์๋๋ ์๋จ์ด๋ผ๊ณ ๋ ํ  ์ ์์ต๋๋ค.

  => ํต์  ๊ท์ฝ์ด๋ฏ๋ก client๊ฐ server์ ์์ฒญํ๊ฑฐ๋ server๊ฐ ์๋ต์ ์ค๋ ์ง์ผ์ผํ๋ ๊ท์น์ด๋ผ๊ณ  ์๊ฐํ๋ฉด ๋จ(๋ํ์ ๊ท์น!)

  > ๐ Hypertext : ์ฐธ์กฐ(ํ์ดํผ๋งํฌ)๋ฅผ ํตํด ๋์๊ฐ ํ ๋ฌธ์์์ ๋ค๋ฅธ ๋ฌธ์๋ก ์ฆ์ ์ ๊ทผํ  ์ ์๋ ํ์คํธ
  >
  > ๐ www. = world wide web

<br>

- `๋ธ๋ผ์ฐ์ ๋ client๊ฐ ๋ณด๋ ํ๋ฉด`์๋๋ค. ์ด ๋ธ๋ผ์ฐ์ ์์ client, ์ฆ ์ฌ์ฉ์๊ฐ ์น์ฌ์ดํธ์์ ์ํธ์์ฉ์ ์ํํ๋ ค๊ณ  ํ  ๋, (๊ฒ์, ์ ์ฅ, ์์ฑ ๋ฑ ๋ญ๋  ํ๋ ค๊ณ  ํ  ๋) ์๊ธฐ๋ ๊ฒ ๋ฐ๋ก ์์ฒญ, **`request`** ์๋๋ค. ์ด๋ฌํ ์์ฒญ์ด ์์ด์ผ ์๋ต, **`response`** ๋ ์๊ธธ ์ ์์ต๋๋ค!

  ex) ๊ฒ์์ฐฝ์ ๋ญ๊ฐ๋ฅผ ๊ฒ์ํ์ ๋, ์์ฒญ์ ๋ํ ์๋ต์ด SERP(search engine results page)์ ๋์ค๋ ๊ฒ

<br>

- ์์ฒญ๊ณผ ์๋ต ๋ชจ๋ data ์ด๋ฏ๋ก ํต์  ๊ท์ฝ์ธ HTTP๋ **`data๊ฐ ๋คํธ์ํฌ๋ฅผ ํตํด ์ ์ก๋๋ ๋ฐฉ๋ฒ`** ์ด๋ผ๊ณ ๋ ํ  ์ ์์ต๋๋ค!

<br>

- ์ ์  ๋ ๋คํธ์ํฌ์์ผ๋ก ์ฒ๋ฆฌ๋๋ ์ผ์ด ๋ง์์ง๋ฉด์ ๊ฐ์ธ ์ ๋ณด๋ ๊ฒฐ์  ์ ๋ณด ๊ฐ์ ๋ณด์์ด ํ์ํ data๋ฅผ ์ฃผ๊ณ  ๋ฐ๋ ๊ฒฝ์ฐ๊ฐ ๋ ๋ง์์ง๊ณ  ์์ต๋๋ค => HTTP์ ์น๋ช์ ์ธ ๋ฌธ์ ๊ฐ ๋ฐ๋ก โโ **HTTP๋ฅผ ํตํ data ์ก์์ ์ ์ 3์๋ ๋๋ฌด ์ฝ๊ฒ ๋ณผ ์ ์์ ๋งํผ ๋ธ์ถ์ด ๋์ด ์์ต๋๋ค** โโ

<br>

## ๐ค What is HTTPS?

<br>

- HTTPS๋ `Hyper Text Transfer Protocol` Secure์ ์ฝ์๋ก ๊ฐ๋จํ๊ฒ HTTP์ **๋ณด์์ด ์ถ๊ฐ** ๋์๋ค๊ณ  ์ดํด ํ  ์ ์์ต๋๋ค!

  ![HTTPS_example](https://user-images.githubusercontent.com/75834421/119218538-c6dfd100-bb1b-11eb-8f73-c3e50e5f23cf.png)

<br>

- HTTPS๋ ํ์ฌ์ **๋ณด์์ธ์ฆ์** ๋ฅผ ์ฌ์ฉํ์ฌ ์ฐ๊ฒฐ์ ๋ณดํธํ๊ณ  ์ฌ์ดํธ๊ฐ ํฉ๋ฒ์ ์ธ์ง ํ์ธํฉ๋๋ค. ์ด ์ธ์ฆ์๋ฅผ **`SSL ์ธ์ฆ์`**(๋๋ "cert")๋ผ๊ณ  ํฉ๋๋ค

  ![http_vs_https](https://user-images.githubusercontent.com/75834421/119217409-fa6b2d00-bb14-11eb-9f87-89b1ec424315.png)

<br>

## ๐ฎ What is SSL or TLS?

<br>

- SSL์ด๋ `Secure Socket layer`๋ก browser์ server์ฌ์ด์ ๊ต๋ฅ๋ฅผ ์ํธํ ํจ์ผ๋ก์จ data์ ๋ธ์ถ์ ๋ง์์ค๋๋ค

  > ๋ท์ค์ผ์ดํ ์ปค๋ฎค๋์ผ์ด์์ค์ฌ๊ฐ ๊ฐ๋ฐํ๊ณ  ํ์ฌ ํ์ค ์ ์ ๋ช์นญ์ **TLS**๋ผ๊ณ  ํฉ๋๋ค!

<br>

- TLS๋ `Transport Layer Security`์ ์ฝ์๋ก `์ ์ก ๊ณ์ธต ๋ณด์`์ ๋ปํ๋ฉฐ HTTPS๋ก ์ฃผ๊ณ  ๋ฐ๋ data๋ฅผ **์ํธํ**ํ๊ณ  ์ ์ ๋ฉ์ผ ๋ฐ ๊ธฐํ **ํ๋กํ ์ฝ์ ๋ณดํธ** ํ๋ ๋ฐ ์ฌ์ฉํ  ์ ์์ต๋๋ค.

  > TLS๋ ๋ค์ํ ์ข๋ฅ์ ๋ณด์ ํต์ ์ ์ํ ํ๋กํ ์ฝ์ด๊ณ  HTTPS๋ TLS์์ HTTP๋ฅผ ์น์ด์ ๋ณด์๋ HTTP ํต์ ์ ํ๋ ํ๋กํ ์ฝ์๋๋ค. ์ฆ, **๋ค์ํ ์ญํ ์ ํ๋ ํ๋กํ ์ฝ์ด ์๋๋ฐ ๊ทธ๊ฒ๋ค์ ๋ณด์(security)์ ๊ด์ฌํ๋ ํ๋กํ ์ฝ์ด TLS!**

<br>

- SSL์ ๊ธฐ๋ฐํ ๊ธฐ์ ๋ก ๋ฐ์ดํฐ๊ฐ ์ ์ก๋ ์ดํ ๋ณ์กฐ๋์ง ์๊ณ  ํต์ ์ด ์ค์  ๋ฐ์ ์์ ์ ์ด๋ฃจ์ด ์ง๋๋ก ํฉ๋๋ค. ์ฌ๊ธฐ์ SSL์ธ์ฆ์๋ก ์๋ฒ๊ฐ ์ ๋ขฐํ  ์ ์๋์ง ํ๋จํ๊ธฐ ์ํด ๊ณต๊ฐํค ์๋ช ๋ฐฉ์์ ์ฌ์ฉํ๋ ์ด๋ฅผ **`SSL/TLS Handshake`** ๋ผ๊ณ  ํฉ๋๋ค!!

  ![handshaking](https://user-images.githubusercontent.com/75834421/119219552-212f6080-bb21-11eb-967d-532570012884.png)

<br>

### ๐ฎ ์ ํํ ์ด๋ค ๋ฐฉ์์ผ๋ก ์ํธํ๋๋ ๊ฑธ๊น?

<br>

![์ํธํ๋ฐฉ์](https://user-images.githubusercontent.com/75834421/119218384-f3471d80-bb1a-11eb-9314-dbf7ee472cc2.png)

<br>

### ๐ฎ HTTPS์ ๋๋ค๋ฅธ ์ฅ์ !!

<br>

- **HTTPS๋ก ์ ํํ๊ฒ ๋๋ฉด `๊ฒ์์์ง ์ต์ ํ(SEO)`์ ์์ด์๋ ํฐ ํํ์ ๋ณผ ์ ์์ต๋๋ค!**
  => ์ง๋ 2014๋ ๊ตฌ๊ธ์์๋ HTTP๋ฅผ HTTPS๋ก ๋ฐ๊พธ๋ผ๊ณ  ๊ถ๊ณ ํ๊ณ , HTTPS๋ก์ ์ ํ์ ์ฅ๋ คํ๊ธฐ ์ํด์ HTTPS๋ฅผ ์ฌ์ฉํ๋ ์น์ฌ์ดํธ์ ๋ํด์ ๊ฒ์ ์์ ๊ฒฐ๊ณผ์ ์ฝ๊ฐ์ ๊ฐ์ฐ์ ์ ์ฃผ๊ฒ ๋ค๊ณ  ๋ฐํํ์ต๋๋ค!

<br>

- SEO๋ `Search Engine Optimization`์ ์ฝ์๋ก `๊ฒ์์์ง์ต์ ํ`๋ฅผ ๋ปํฉ๋๋ค. ๋ค์๋งํด, ๊ฒ์์ (๊ฒ์ ์ ์ )์ ์๋๋ฅผ ์ดํดํ๊ณ  ์ด์ ์ถฉ์คํ ๋ง์ถฐ ์น ํ์ด์ง์ ์ฝํ์ธ ๋ฅผ ์ ์ํ๊ณ , ์ด ํ์ด์ง๊ฐ ๊ฒ์ ๊ฒฐ๊ณผ ํ์ด์ง์์ ์ ๋ธ์ถ ๋๋๋ก ์นํ์ด์ง์ ํ๊ทธ์ ๋งํฌ ๊ตฌ์กฐ๋ฅผ ๊ฐ์ ํ์ฌ ์์ฐ ์ ์ ํธ๋ํฝ์ ๋๋ฆฌ๋ ์์ฑโ์ด๋ผ๊ณ  ํ  ์ ์์ต๋๋ค.

<br>

- **`๊ฐ์ํ๋ ๋ชจ๋ฐ์ผ ํ์ด์ง(AMP, Accelerated Mobile Pages)`๋ฅผ ๋ง๋ค๊ณ  ์ถ์ ๋๋ HTTPS ํ๋กํ ์ฝ์ ์ฌ์ฉ**ํด์ผ ํฉ๋๋ค! ์ฌ๊ธฐ์ `AMP`๋ ๋ชจ๋ฐ์ผ ๊ธฐ๊ธฐ์์ ํ์ด์ง๋ฅผ ๋ณผ ๋ ๋ถํ์ํ HTML์์๋ ๋นผ๊ณ  ๋ฑ ํ์ํ ๊ฒฐ๊ณผ๋ง ์ ๋ณด์ด๊ฒ๋ ์ฝํ์ธ ๋ฅผ ๋ก๋ฉํ๋ ๋ฐฉ๋ฒ์๋๋ค!

  > ์ด๊ฒ๋ ๊ตฌ๊ธ์ด ๋ง๋ ๊ฑฐ๋ผ๊ณ  ํฉ๋๋ค๐๐

<br>

### ๐ฎ ๊ทธ๋ฌ๋ฉด http ์์ https๋ก ์ ํํ๋ ๋ฐฉ๋ฒ์??

<br>

๐ http์์ https๋ก ์ ํํ  ๋ `๊ณ ๋ คํด์ผํ  ์ `๋ค์ด ์์ต๋๋ค.

<br>

1. **Inform Google About the Transition, and Mistakes to Avoid**
   => ์ฌ์ดํธ๊ฐ http์์ https๋ก ์ ํ๋๊ฑธ ๊ตฌ๊ธ์ ์๋ ค์ฃผ๊ธฐ!

2. **Choose the Right Security Certificate: SSL and Wildcard Certificates** => ๋ค์ํ SSL ์ธ์ฆ์ ์ค ์ ์ ํ ๊ฒ ์ ๊ณ ๋ฅด๊ธฐ!

3. **Make Sure All URLs Are Properly Updated Sitewide** => htmlํ์ผ tag์์์ ์ฌ์ฉํ๋ ๋ชจ๋  url๋ค๋ ์ ๋ณด๊ณ  https์ ๋ง๊ฒ ๋ณ๊ฒฝํ๊ธฐ!(relative Url ์ฌ์ฉ!)

4. **Don't Prevent Google From Crawling Your New HTTPS Site** => ๊ตฌ๊ธ์ด ํฌ๋กค๋ง ํ๋ ๊ฑธ ๋ง์ง ์๋๋ก ํด์ผ ํฉ๋๋ค! + ๊ฒ์์์ง์ด ์ฐ๋ฆฌ์ ์น์ฌ์ดํธ์ ์๋ ํ์ด์ง๋ค์ ์ธ๋ฑ์ฑํ๋ ๊ฒ์ ํ์ฉํด์ผ ํฉ๋๋ค!!

<br>

[์ฐธ๊ณ ]

- HTTP vs HTTPS

  : <http://blog.wishket.com/http-vs-https-%EC%B0%A8%EC%9D%B4-%EC%95%8C%EB%A9%B4-%EC%82%AC%EC%9D%B4%ED%8A%B8%EC%9D%98-%EB%A0%88%EB%B2%A8%EC%9D%B4-%EB%B3%B4%EC%9D%B8%EB%8B%A4/>

  : <https://www.semrush.com/blog/what-is-https/>

- ๋ค์ํ ํ๋กํ ์ฝ

  : <https://enter.tistory.com/141>

  : <https://m.blog.naver.com/xcripts/70122755291>

- TLS/SSL HandShake

  : <https://wangin9.tistory.com/entry/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%97%90-URL-%EC%9E%85%EB%A0%A5-%ED%9B%84-%EC%9D%BC%EC%96%B4%EB%82%98%EB%8A%94-%EC%9D%BC%EB%93%A4-5TLSSSL-Handshake#:~:text=%EC%9D%B8%EC%A6%9D%EC%84%9C%EB%A5%BC%20%ED%86%B5%ED%95%B4%20%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8%EA%B0%80,SSL%2FTLS%20Handshake%20%EB%9D%BC%EA%B3%A0%20%ED%95%A9%EB%8B%88%EB%8B%A4.>

- SSL์ ๋ฌด์์ด๊ณ  ์ธ์ฆ์๋ ๋ฌด์์ธ๊ฐ?

  : <https://wiki.kldp.org/HOWTO/html/SSL-Certificates-HOWTO/x70.html>
