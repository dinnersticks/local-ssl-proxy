local-ssl-proxy
===============

Simple SSL HTTP proxy using a self-signed certificate. Intended for local development only.

Install
-------
```sh
npm install -g local-ssl-proxy
```

Run
---
To start a proxy from port `9001` to `9000` run:
```sh
local-ssl-proxy --source 9001 --target 9000
```

Start your web server on the target port (`9000` in the example) and navigate to `https://localhost:<target-port>` ([https://localhost:9001](https://localhost:9001) in the example). You'll get a warning because the certificate is self-signed, this is safe to ignore during development.

Test
---
Run in parallel as responder to test valid proxy connectivity. 
 ```js
var http = require('http');

http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Testing Local SSL Proxy\n');
}).listen(9000, "127.0.0.1");

console.log('Server running at http://127.0.0.1:9000/');
 ```
