
# Node.js nedir?

* Node.js açık kaynaklı bir sunucu ortamıdır
* Node.js çeşitli platformlarda çalışır (Windows, Linux, Unix, Mac OS X, vb.)
* Düğüm.js sunucuda JavaScript kullanır

# Node.js Ne Yapabilir?

* Düğüm.js dinamik sayfa içeriği oluşturabilir
* Düğüm.js sunucuda dosya oluşturabilir, açabilir, okuyabilir, yazabilir, silebilir ve kapatabilir
* Düğüm.js form verilerini toplayabilir
* Düğüm.js veritabanınıza veri ekleyebilir, silebilir, değiştirebilir
 

# Başlarken
Çalıştır => C:\Kullanıcılar\Adınız>node myfirst.js (Dosyaya  girmeyi unutma!!!)



## Sunucu Oluşturma

```javascript
// http modülünü require kullanarak içeri aktarıyoruz.
var http = require('http');

// myfirstmodule.js dosyasında tanımlanmış olan myDateTime fonksiyonunu içeri aktarıyoruz.
var dt = require('./myfirstmodule');

// Bir HTTP sunucusu oluşturuyoruz ve callback fonksiyonu kullanarak istekleri ele alıyoruz.
http.createServer(function (req, res) {
  // Sunucu yanıtı için başlık tanımlıyoruz ve 'text/html' türünde bir içerik belirtiyoruz.
  res.writeHead(200, {'Content-Type': 'text/html'});
  
  // Sunucu yanıtı olarak, "The date and time are currently: " ifadesini ve myDateTime fonksiyonunun döndürdüğü tarih/saat metnini gönderiyoruz.
  res.write("The date and time are currently: " + dt.myDateTime());
  
  // Yanıtın tamamlandığını belirtiyoruz.
  res.end();
}).listen(8080); // Sunucuyu belirtilen 8080 portunda dinlemeye başlatıyoruz.



## s