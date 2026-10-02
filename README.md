# Safe Shop Redirect Page

এটি GitHub Pages-এ চলা একটি static redirect page। এটি third-party URL shortener bypass করে না; শুধু আগে থেকে configure করা নিজের shop domain-এ redirect করে।

## Setup

`index.html`-এ এই line বদলাও:

```js
const ALLOWED_HOSTS = ["your-shop.example"];
```

উদাহরণ:

```js
const ALLOWED_HOSTS = ["shop.example.com", "www.shop.example.com"];
```

তারপর GitHub repository settings থেকে **Pages → Deploy from branch → main → /(root)** নির্বাচন করো।

## ব্যবহার

```text
https://USERNAME.github.io/Bypass1/?link=https%3A%2F%2Fshop.example.com%2Fproduct%2F123
```

`link` অবশ্যই URL-encoded হতে হবে। Page-টি শুধু `ALLOWED_HOSTS`-এ থাকা HTTPS domain গ্রহণ করবে। `vplink.in` বা অন্য third-party shortener যোগ করবে না।

## গুরুত্বপূর্ণ

GitHub Pages static hosting হওয়ায় এখানে server-side validation নেই। Secret, API key বা private redirect data এই ফাইলে রাখবে না। Private/complex logic দরকার হলে নিজের backend, Cloudflare Worker অথবা Flask API ব্যবহার করো।
