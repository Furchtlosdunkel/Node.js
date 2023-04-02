# Node.js nedir?

* Node.js açık kaynaklı bir sunucu ortamıdır

* Node.js çeşitli platformlarda çalışır (Windows, Linux, Unix, Mac OS X, vb.)

* Düğüm.js sunucuda JavaScript kullanır

# Node.js Ne Yapabilir?

* Düğüm.js dinamik sayfa içeriği oluşturabilir

* Düğüm.js sunucuda dosya oluşturabilir, açabilir, okuyabilir, yazabilir, silebilir ve kapatabilir

* Düğüm.js form verilerini toplayabilir

* Düğüm.js veritabanınıza veri ekleyebilir, silebilir, değiştirebilir

# Get Started
Çalıştır => C:\Kullanıcılar\Adınız>node myfirst.js (Dosyaya  girmeyi unutma!!!!)

# Node.js Modules

* Node.js modülleri, önceden yazılmış JavaScript kod bloklarının tekrar kullanılabilmesini sağlar.

* Modüller, bir Node.js uygulamasındaki farklı bölümleri ayırmak ve organize etmek için kullanılır.

* Node.js'de modüller <b style="text-decoration: underline;">"require()"</b> fonksiyonu kullanılarak yüklenir. Bu fonksiyon, bir modül dosyasının yolunu alır ve ilgili modülün içeriğini yükler.

### Örneğin:

```Javascript
// example.js dosyası
const hello = () => {
  console.log("Hello, World!");
};

module.exports = { hello };
```

```Javascript
// main.js dosyası
const example = require("./example");

example.hello(); // "Hello, World!" yazdırır
```
<hr>

## HTML Dosyasını Ekleme:
Bu kod, Node.js HTTP modülünü kullanarak bir HTTP sunucusu oluşturur ve <b>"index.html"</b> adlı html dosyasının içeriğini istemcilere sunar.

```Javascript

const http = require('http');
const fs = require('fs');

http.createServer(function (req, res) {
    fs.readFile('index.html', function(err, data) {
      if (err) throw err;
      res.writeHead(200, {'Content-Type': 'text/html'});
      res.write(data);
      res.end();
    });
  }).listen(8080);

```
* Bu kod, <b>http.createServer()</b> fonksiyonu, bir callback fonksiyonu içerir. Bu fonksiyon, bir istek alındığında çalıştırılır.
* İstek alındığında, <b>http.createServer()</b> yöntemi ile "index.html" dosyası okunur ve yanıt olarak gönderilir. 
* <b>listen()</b> yöntemi, HTTP sunucusunun belirtilen bağlantı noktasında çalıştırılmasını sağlar.

# Node.js HTTP Module

* Node.js'in HTTP modülü, web sunucularının oluşturulmasına ve yönetilmesine olanak tanıyan bir modüldür.

* HTTP modülü, Node.js uygulamasının gelen istekleri dinlemesine, yanıt vermesine ve HTTP protokolüne uygun yanıtlar göndermesine olanak tanır

### Örneğin:

HTTP modülü kullanarak bir web sunucusu oluşturmak için şu adımları izleyebilirsiniz:

```Javascript
const http = require('http');

const server = http.createServer((req, res) => {
  // HTTP isteği geldiğinde çalışacak kodlar
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello, World!\n');
});

server.listen(3000, () => {
  console.log('Sunucu dinleniyor...');
});

```
#### Bu kod örneğinde

* <b> "http" </b> modülü <b>"require()"</b> fonksiyonu kullanılarak yüklenir ve "createServer()" metodu kullanarak bir HTTP sunucusu oluşturulur.( <b>"createServer()" </b> metodu, HTTP isteklerini dinleyen ve yanıt veren bir işlev alır. )

*  Bu örnekte, bir HTTP isteği alındığında, isteği karşılamak için yanıt verilir.

* <b>"statusCode"</b>ve <b>"setHeader()</b> "metodları kullanılarak yanıtın başlığı ayarlanır ve <b>"end()" </b>metodu kullanılarak yanıtın içeriği belirlenir.

* Son olarak, <b>listen()</b> metodu kullanılarak sunucunun dinlemesi gereken bağlantı noktası belirlenir. Bu örnekte, sunucu 3000 numaralı bağlantı noktasında dinlenir. <b>listen()</b> metodu ayrıca sunucunun dinlemeye başlamasından sonra çalışacak bir geri çağrı işlevi alır.

* <b>req (request) </b> ve <b>res (response)</b> kavramları, Node.js HTTP sunucusunda bir istek ve yanıt nesnesini temsil eder.<br>
<b>req </b> nesnesi, istek yaparken gönderilen tüm bilgileri içerirken, 
<br>
<b>res </b>  nesnesi, isteğe yanıt olarak gönderilen tüm bilgileri içerir. <br>
Bu nesneler, HTTP modülü kullanılarak bir web sunucusu oluşturulurken, isteği yönetmek ve yanıt vermek için kullanılır.
<hr>

## Add an HTTP Header

HTTP başlıkları, istek ve yanıt mesajlarında bilgi iletmek için kullanılır. Node.js'in http modülü, başlıkları eklemek ve okumak için bir dizi yöntem sağlar

```Javascript
const http = require('http');
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.write('Hello World!');
  res.end();
}).listen(8080);
```
* Bu örnekte, <b>res.writeHead()</b> yöntemi <b>"Content-Type"</b> başlığını <b>"text/html"</b> olarak ayarlar ve yanıtın durum kodunu <b>"200"</b> olarak ayarlar (başarılı bir yanıtı temsil eder).
* <b>res.write()</b> yöntemi, yanıtın gövdesine HTML kodu ekler.
* <b>res.end()</b> yöntemi, yanıtı sonlandırır ve istemciye gönderir.
<hr>

## Read the Query String
Node.js'de, bir URL'de belirtilen sorgu dizesini okumak için url modülü kullanılabilir. Sorgu dizesi, bir URL'nin sonundaki ? işaretinden sonra gelen parametrelerdir ve key=value çiftleri şeklinde yazılırlar. Bu çiftler, & işareti ile ayrılır. Örneğin, http://localhost:8080/?name=John&age=30 URL'sindeki sorgu dizesi, name=John&age=30 şeklindedir.

### Örneğin
Aşağıdaki örnek, bir URL'deki sorgu dizesini okur ve bunu res.write() yöntemiyle yanıt olarak gönderir:

```Javascript
const http = require('http');
const url = require('url');

http.createServer(function (req, res) {
  const q = url.parse(req.url, true).query;
  const name = q.name;
  const age = q.age;
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.write(`Hello ${name}, you are ${age} years old!`);
  res.end();
}).listen(8080);

```
* Yukarıdaki örnekte, <b>url.parse()</b> yöntemi kullanılarak istek URL'si ayrıştırılır ve query özelliği kullanılarak sorgu dizesi alınır. 
* Bu sorgu dizesi daha sonra <b>name</b> ve <b>age </b>değişkenlerine atanır ve <b>res.write()</b> yöntemiyle yanıt olarak gönderilir.

# Node.js File System Module

Node.js'de fs (file system) modülü, dosya işlemleri yapmak için kullanılır. Bu modül, dosyaları okumak, yazmak, güncellemek, silmek, oluşturmak, taşımak ve kopyalamak gibi birçok işlemi gerçekleştirmek için fonksiyonlar sağlar.

### Örneğin:

```Javascript
// Yazma örneği
const fs = require('fs');

fs.writeFile('ornek.txt', 'Merhaba, Dünya!', function (err) {
  if (err) throw err;
  console.log('Dosya oluşturuldu ve yazıldı!');
});

```
Bu örnek kodda,
*  fs modülü require() fonksiyonu kullanılarak yüklenir ve writeFile() metodunu kullanarak yeni bir dosya oluşturulur ve yazılır.
*  İlk argüman, oluşturulacak dosyanın adı ve yolu,<br>
   ikinci argüman ise dosyaya yazılacak içeriği temsil eder.<br>
   Üçüncü argüman ise bir geri çağırma işlevi (callback function) alır ve işlem tamamlandığında çalışır.
   
<hr>
Benzer şekilde, File System modülü ile bir dosyayı okuyabilir veya silinebilir veya klasörlerle ilgili işlemler yapılabilir.

```Javascript
// Dosya okuma örneği
const fs = require('fs');

// Dosyayı oku
fs.readFile('dosya.txt', (err, data) => {
  if (err) throw err;
  console.log(data);
});

// Dosyaya yaz
fs.writeFile('dosya.txt', 'Merhaba Dünya!', (err) => {
  if (err) throw err;
  console.log('Dosya yazıldı!');
});

// Dosyaya ekle
fs.appendFile('dosya.txt', 'Bu son ekleme!', (err) => {
  if (err) throw err;
  console.log('Dosyaya eklendi!');
});

// Dosyayı sil
fs.unlink('dosya.txt', (err) => {
  if (err) throw err;
  console.log('Dosya silindi!');
});

// Dosyayı yeniden adlandır veya taşı
fs.rename('dosya.txt', 'yenidosya.txt', (err) => {
  if (err) throw err;
  console.log('Dosya yeniden adlandırıldı veya taşındı!');
});

// Dosyanın bilgilerini al
fs.stat('yenidosya.txt', (err, stats) => {
  if (err) throw err;
  console.log(`Dosya boyutu: ${stats.size} bytes`);
});

// Yeni bir dizin oluştur
fs.mkdir('yeni_dizin', (err) => {
  if (err) throw err;
  console.log('Yeni bir dizin oluşturuldu!');
});

// Dizindeki dosyaları listele
fs.readdir('.', (err, files) => {
  if (err) throw err;
  console.log(files);
});
```

# Node.js URL Module

Node.js URL modülü, URL'leri (Uniform Resource Locator) ayrıştırmak, işlemek ve oluşturmak için kullanılır. Bu modül, bir URL'nin farklı parçalarına erişmek için birçok yöntem sağlar.

### Örneğin:
Aşağıda, Node.js URL modülü kullanarak bir URL'yi ayrıştırmak ve parçalarına erişmek için kullanabileceğiniz örnek bir kod parçası verilmiştir:

```Javascript
const url = require('url');

const myUrl = 'https://www.example.com:8080/path?query=string#hash';

// URL'yi ayrıştırma
const parsedUrl = url.parse(myUrl, true);

// URL parçalarına erişim
console.log(parsedUrl.href);     // 'https://www.example.com:8080/path?query=string#hash'
console.log(parsedUrl.protocol); // 'https:'
console.log(parsedUrl.host);     // 'www.example.com:8080'
console.log(parsedUrl.hostname); // 'www.example.com'
console.log(parsedUrl.port);     // '8080'
console.log(parsedUrl.path);     // '/path?query=string'
console.log(parsedUrl.pathname); // '/path'
console.log(parsedUrl.search);   // '?query=string'
console.log(parsedUrl.query);    // { query: 'string' }
console.log(parsedUrl.hash);     // '#hash'

```
* Bu örnekte, <b>url.parse()</b> metodu kullanılarak bir URL ayrıştırılır ve parçalarına erişilir. Metodun ilk parametresi, ayrıştırılacak URL'yi, ikinci parametresi ise URL sorgularını ayrıştırmak için kullanılan bir nesne olabilir. <b>url.parse()</b> metodu, URL'nin ayrıştırılmış halini bir nesne olarak döndürür ve bu nesnenin özellikleri aracılığıyla URL parçalarına erişilir.

  * protocol: URL'nin protokolü (http, https, ftp vb.).
  * slashes: // işaretlerinin varlığı.
  * auth: URL'nin kimlik doğrulama bilgileri (kullanıcı adı ve şifre).
  * host: URL'nin ana bilgisayarı ve bağlantı noktası.
  * port: URL'nin bağlantı noktası.
  * hostname: URL'nin ana bilgisayarı.
  * hash: URL'nin sayfadaki konumu.
  * search: URL'nin sorgu dizisi.
  * query: URL'nin sorgu dizisi (sorgu dizesi anahtar-değer çiftleri olarak ayrıştırılmış hali).
  * pathname: URL'nin yolu.
  * path: URL'nin yolu ve sorgu dizisi.
  * href: Tam URL.
<hr>
Node.js URL modülü, URL'leri oluşturmak için de kullanılabilir. url.format() metodu, bir URL nesnesini bir URL'ye dönüştürür. Aşağıda örnek bir kod parçası verilmiştir:

```Javascript
const url = require('url');
const myUrl = url.format({
  protocol: 'https',
  hostname: 'www.example.com',
  pathname: '/path',
  query: { id: '123', name: 'example' }
});

console.log(myUrl); // 'https://www.example.com/path?id=123&name=example'

```
Bu örnekte, url.format() metodu, bir URL nesnesi alır ve bu nesneyi bir URL'ye dönüştürür. Nesne özellikleri, URL parçalarına karşılık gelir.

