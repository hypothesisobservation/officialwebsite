# qcl (qcl)

QCL Website

## Install the dependencies
```bash
nvm use v16.19.1
npm install pm2@latest -g //optional
npm install
```

### Instlal qflashcard
```bash
quasar ext add @quasar/qflashcard //optional
```

### Start the app in development mode (hot-code reloading, error reporting, etc.)
```bash
npx quasar dev
http://localhost:8080/
```

local build testing:
```bash
src-ssr/index.js
const options = {
//  key: fs.readFileSync("/ssl/Nginx/2_qcldigital.com.key"),
//  cert: fs.readFileSync("/ssl/Nginx/1_qcldigital.com_bundle.crt")
};
//app.get('/', function (req, res, next) {
//  if (req.secure) {
//          // request was via https, so do no special handling
//          next();
//  } else {
//          // request was via http, so redirect to https
//          res.redirect('https://' + req.headers.host + req.url);
//  }
//})
// https.createServer(options, app).listen(443);

npx quasar build --mode ssr
cd dist/ssr
npm run start
http://localhost:3000/
```


### Build the app for production
```bash
(SPA)
quasar build
\cp -rf /var/lib/jenkins/workspace/QCLSSR/dist/spa/* /var/www/html
(SSR)
cd /var/lib/jenkins/workspace/QCLSSR
quasar build --mode ssr
cd dist/ssr && npm install && PORT=80 npm run start
cd dist/ssr && npm install && pm2 stop index && PORT=80 pm2 start index.js
```

### Customize the configuration
See [Configuring quasar.conf.js](https://quasar.dev/quasar-cli/quasar-conf-js).

### 不使用默认的MainLayout.vue
```bash
src/router/routes.js
```
 
