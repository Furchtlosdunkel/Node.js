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
Aşağıdaki örnek, bir URL'deki sorgu dizesini okur ve bunu <b>res.write()</b> yöntemiyle yanıt olarak gönderir:

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
*  fs modülü <b>require()</b> fonksiyonu kullanılarak yüklenir ve <b>writeFile()</b> metodunu kullanarak yeni bir dosya oluşturulur ve yazılır.
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
Node.js URL modülü, URL'leri oluşturmak için de kullanılabilir. <b>url.format()</b> metodu, bir URL nesnesini bir URL'ye dönüştürür. Aşağıda örnek bir kod parçası verilmiştir:

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
Bu örnekte, <b>url.format()</b> metodu, bir URL nesnesi alır ve bu nesneyi bir URL'ye dönüştürür. Nesne özellikleri, URL parçalarına karşılık gelir.

# Node.js NPM
## NPM Nedir?
* NPM, Node.js paketleri veya isterseniz modüller için bir paket yöneticisidir.
* <a>www.npmjs.com</a> indirip kullanabileceğiniz binlerce ücretsiz paket barındırır.
* Node.js'yi yüklediğinizde NPM programı bilgisayarınıza yüklenir.
## Paket Nedir?
* Node.js'deki bir paket, bir modül için ihtiyacınız olan tüm dosyaları içerir.
* Modüller, projenize dahil edebileceğiniz JavaScript kütüphaneleridir.

## Bir Paket İndirin
* Bir paketi indirmek çok kolaydır.

* Komut satırı arayüzünü açın ve NPM'ye istediğiniz paketi indirmesini söyleyin.

  * "büyük harf" adlı bir paket indirmek istiyorum

```cmd
C:\Users\Your Name>npm install upper-case
```
* NPM, paketin yerleştirileceği <b>"node_modules"</b> adlı bir klasör oluşturur. Gelecekte kuracağınız tüm paketler bu klasöre yerleştirilir.

Projemin artık şöyle bir klasör yapısı var:

```cmd
C:\Users\My Name\node_modules\upper-case
```
## Paket Kullanma

* Paket yüklendikten sonra kullanıma hazırdır.

"Büyük harfli" paketi, diğerlerini dahil ettiğiniz şekilde ekleyin modül:
```Javascript
const uc = require('upper-case');
```


<b>"Hello World!"</b> çıktısını büyük harflere dönüştürecek bir Node.js dosyası oluşturun:

```Javascript
const http = require('http');
const uc = require('upper-case');
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.write(uc.upperCase("Hello World!"));
  res.end();
}).listen(8080);

```

# Node.js Events
Node.js, olay tabanlı bir mimariye sahip olduğu için olayları işleyebilir. Node.js, <b>'events'</b> adlı bir modül sunar, bu modül sayesinde, özel olaylar tanımlayabilir ve bu olaylar tetiklendiğinde özel işlevler çağırabilirsiniz.

Bu modül, EventEmitter sınıfını tanıtır. EventEmitter sınıfı, özel olaylar oluşturmak için kullanılan ana sınıftır. Bu sınıf, olayları yayınlayan nesneleri temsil eder ve olayları dinleyen işlevler eklemenizi sağlar.

Olaylar, EventEmitter sınıfında tanımlandığı gibi, bir kez tanımlandığında tetiklenebilir. Bu olaylar, onlarca özel fonksiyonu tetikleyebilir ve bunlar özel işlevlerinizi çağırabilir.

### Örneğin:
```Javascript
const EventEmitter = require('events');

class MyEmitter extends EventEmitter {}

const myEmitter = new MyEmitter();

myEmitter.on('event', () => {
  console.log('Bir olay tetiklendi!');
});

myEmitter.emit('event');

```
* Bu örnekte, EventEmitter sınıfı kullanarak özel bir olay tanımlıyoruz. Bu olayı tetiklemek için <b>emit()</b>fonksiyonunu kullanıyoruz ve bir sonraki satırda, <b>on()</b> fonksiyonuyla olayın tetiklenmesi durumunda çalışacak bir fonksiyon tanımlıyoruz. <b>emit()</b>fonksiyonuyla, 'event' olayını tetikliyoruz ve sonuç olarak, "Bir olay tetiklendi!" mesajını görüntüleyecektir.

# Node.js Upload Files
* Formidable modülü NPM kullanılarak indirilebilir ve kurulabilir:
```cmd
C:\Users\Your Name>npm install formidable
```
* Formidable modülünü indirdikten sonra, modülü herhangi bir uygulamaya dahil edebilirsiniz:

```Javascript
var formidable = require('formidable');
```
## Dosya Yükleme
* Artık Node.js'de kullanıcının bilgisayarınıza dosya yüklemesini sağlayan bir web sayfası yapmaya hazırsınız:

### Adım 1: Bir Yükleme Formu Oluşturun
* Yükleme alanı olan bir HTML formu yazan bir Node.js dosyası oluşturun:
```Javascript
// Bu kod bir HTML formu üretecektir:
var http = require('http');

http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.write('<form action="fileupload" method="post" enctype="multipart/form-data">');
  res.write('<input type="file" name="filetoupload"><br>');
  res.write('<input type="submit">');
  res.write('</form>');
  return res.end();
}).listen(8080);
```
### Adım 2: Yüklenen Dosyayı Ayrıştırın
* Sunucuya ulaştığında yüklenen dosyayı ayrıştırabilmek için Formidable modülünü ekleyin.

* Dosya yüklendiğinde ve ayrıştırıldığında, bilgisayarınızdaki geçici bir klasöre yerleştirilir.

```Javascript
// Dosya yüklenecek ve geçici bir klasöre yerleştirilecektir:
var http = require('http');
var formidable = require('formidable');

http.createServer(function (req, res) {
  if (req.url == '/fileupload') {
    var form = new formidable.IncomingForm();
    form.parse(req, function (err, fields, files) {
      res.write('File uploaded');
      res.end();
    });
//   } else {
//     res.writeHead(200, {'Content-Type': 'text/html'});
//     res.write('<form action="fileupload" method="post" enctype="multipart/form-data">');
//     res.write('<input type="file" name="filetoupload"><br>');
//     res.write('<input type="submit">');
//     res.write('</form>');
//     return res.end();
//   }
// }).listen(8080);
```
### Adım 3: Dosyayı Kaydedin
* Bir dosya sunucuya başarıyla yüklendiğinde, geçici bir klasöre yerleştirilir.

* Bu dizinin yolu, yöntemin geri arama işlevinde üçüncü bağımsız değişken olarak aktarılan "files" nesnesinde bulunabilir.<b>parse()</b>

* Dosyayı istediğiniz klasöre taşımak için Dosya Sistemi modülünü kullanın ve dosyayı yeniden adlandırın:

```Javascript
// var http = require('http');
// var formidable = require('formidable');
var fs = require('fs');

// http.createServer(function (req, res) {
//   if (req.url == '/fileupload') {
//     var form = new formidable.IncomingForm();
//     form.parse(req, function (err, fields, files) {
      var oldpath = files.filetoupload.filepath;
      var newpath = 'C:/Users/Your Name/' + files.filetoupload.originalFilename;
      fs.rename(oldpath, newpath, function (err) {
        if (err) throw err;
        res.write('File uploaded and moved!');
        res.end();
      });
//  });
//   } else {
//     res.writeHead(200, {'Content-Type': 'text/html'});
//     res.write('<form action="fileupload" method="post" enctype="multipart/form-data">');
//     res.write('<input type="file" name="filetoupload"><br>');
//     res.write('<input type="submit">');
//     res.write('</form>');
//     return res.end();
//   }
// }).listen(8080);
```
### Dosya Yükleme ( "toplam kod")
```Javascript
var http = require('http');
var formidable = require('formidable');
var fs = require('fs');

http.createServer(function (req, res) {
  if (req.url == '/fileupload') {
    var form = new formidable.IncomingForm();
    form.parse(req, function (err, fields, files) {
      var oldpath = files.filetoupload.filepath;
      var newpath = 'C:/Users/Your Name/' + files.filetoupload.originalFilename;
      fs.rename(oldpath, newpath, function (err) {
        if (err) throw err;
        res.write('File uploaded and moved!');
        res.end();
      });
 });
  } else {
    res.writeHead(200, {'Content-Type': 'text/html'});
    res.write('<form action="fileupload" method="post" enctype="multipart/form-data">');
    res.write('<input type="file" name="filetoupload"><br>');
    res.write('<input type="submit">');
    res.write('</form>');
    return res.end();
  }
}).listen(8080);
```

# Node.js Send an Email
* Node.js kullanarak e-posta göndermek için, nodemailer adlı bir modül kullanabilirsiniz. Bu modül, SMTP veya sendmail protokollerini kullanarak e-posta göndermenizi sağlar.

* İlk olarak, nodemailer modülünü kurmanız gerekiyor. Bunun için terminal veya komut istemi penceresinde aşağıdaki komutu çalıştırabilirsiniz:
```cmd
npm install nodemailer
```

```Javascript
var nodemailer = require('nodemailer');

var transporter = nodemailer.createTransport({
  service: 'gmail',
  auth: {
    user: 'youremail@gmail.com',
    pass: 'yourpassword'
  }
});

var mailOptions = {
  from: 'youremail@gmail.com',
  to: 'myfriend@yahoo.com',
  subject: 'Sending Email using Node.js',
  text: 'That was easy!'
};

transporter.sendMail(mailOptions, function(error, info){
  if (error) {
    console.log(error);
  } else {
    console.log('Email sent: ' + info.response);
  }
});
```
Ve hepsi bu kadar! Artık sunucunuz e-posta gönderebilir.

## Çoklu Alıcılar
* Birden fazla alıcıya e-posta göndermek için, bunları mailOptions nesnesinin virgülle ayrılmış "to" özelliğine ekleyin:

```Javascript
// Birden fazla adrese e-posta gönderme:
var mailOptions = {
  from: 'youremail@gmail.com',
  to: 'myfriend@yahoo.com, myotherfriend@yahoo.com',
  subject: 'Sending Email using Node.js',
  text: 'That was easy!'
}
```
## HTML Gönder 
* E-postanızda HTML biçimli metin göndermek için "text" özelliği:
```Javascript
// HTML içeren e-posta gönderme:
var mailOptions = {
  from: 'youremail@gmail.com',
  to: 'myfriend@yahoo.com',
  subject: 'Sending Email using Node.js',
  html: '<h1>Welcome</h1><p>That was easy!</p>'
}
```



