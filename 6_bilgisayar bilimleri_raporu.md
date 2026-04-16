## 1. API NEDİR VE NEDEN VARDIR?
API (Application Programming Interface), iki farklı yazılımın birbiriyle güvenli ve standart bir şekilde konuşmasını sağlayan bir arayüzdür.

### 1.1. API'nin Temel Amacı
Veri Paylaşımı: Veritabanındaki veriyi doğrudan açmak yerine, kontrollü bir şekilde dış dünyaya sunar.

Soyutlama: Arka plandaki binlerce satırlık kodu gizleyerek, kullanıcıya sadece "istek yap ve cevap al" kolaylığı sağlar.

Platform Bağımsızlığı: Yazılan tek bir backend, hem Android hem iOS hem de Web uygulamalarına aynı veriyi gönderebilir.

### 1.2. Neden İhtiyaç Duyarız?
Modern yazılımlar artık "Monolitik" (tek parça) yapıdan "Microservice" (küçük parçalar) yapısına geçmiştir. API'ler bu parçaların birbiriyle uyum içinde çalışmasını sağlayan tek standarttır.

## 2. REST MİMARİSİ VE HTTP METOTLARI
REST (Representational State Transfer), web üzerinden veri alışverişi yaparken kullanılan en yaygın mimari stildir.

### 2.1. Temel HTTP Metotları (CRUD İşlemleri)
Bir API üzerinden işlem yaparken kullanılan standart fiiller şunlardır:

GET (Read): Sunucudan veri çekmek için kullanılır. Sadece okuma yapar, veriyi değiştirmez.

POST (Create): Sunucuya yeni bir veri kaydetmek için kullanılır. (Örn: Yeni bir kullanıcı oluşturma).

PUT (Update): Mevcut bir veriyi tamamen güncellemek için kullanılır. Verinin tüm alanlarını kapsar.

PATCH (Partial Update): Verinin tamamını değil, sadece belirli bir kısmını değiştirmek için kullanılır.

DELETE (Delete): Belirli bir kaynağı sunucudan kalıcı olarak silmek için kullanılır.

### 2.2. HTTP Durum Kodlarının Anlamı
Sunucu, yapılan her isteğe bir sayısal kodla cevap verir:

2xx (Başarı): 200 (OK) veya 201 (Created) işlemlerin sorunsuz bittiğini gösterir.

4xx (İstemci Hatası): 404 (Bulunamadı) veya 401 (Yetkisiz Giriş) hatalarını temsil eder.

5xx (Sunucu Hatası): 500 (İç Sunucu Hatası) sunucu tarafında bir çökme olduğunu belirtir.

## 3. JSON (JAVASCRIPT OBJECT NOTATION) YAPISI
JSON, makinelerin kolayca okuduğu ve insanların kolayca yazdığı hafif bir veri değişim formatıdır.

### 3.1. JSON Veri Tipleri ve Hiyerarşi
JSON verisi her zaman bir "Key-Value" (Anahtar-Değer) çiftinden oluşur ve şu kurallara uyar:

Nesneler (Objects): Süslü parantez { } içinde tanımlanır.

Diziler (Arrays): Köşeli parantez [ ] içinde liste şeklinde tutulur.

Veri Tipleri: String (metin), Number (sayı), Boolean (true/false) ve Null tiplerini destekler.

### 3.2. Örnek Veri Yapısı
{
  "id": 232511043,
  "ad": "Yavuz Selim",
  "soyad": "Karakülah",
  "ogrenci_mi": true,
  "yetenekler": ["Java", "JavaScript", "Linux", "API"],
  "egitim": {
    "bolum": "Bilgisayar Programcılığı",
    "durum": "Aktif"
  }
}

## 4. BASİT BİR ENDPOINT TASARIMI
Bir API tasarımı yapılırken URL'lerin (endpoint) temiz, anlaşılır ve hiyerarşik olması gerekir.

### 4.1. Endpoint Standartları
İyi bir endpoint tasarımı eylem (fiil) yerine nesne (isim) kullanır:

Yanlış: /kitaplariGetir

Doğru: GET /kitaplar
Metot,Endpoint,İşlem
GET,/kitaplar,Tüm kitap listesini döndürür.
GET,/kitaplar/12,12 ID numaralı kitabın detayını verir.
POST,/kitaplar,Sisteme yeni bir kitap verisi ekler.
DELETE,/kitaplar/12,İlgili kitabı kütüphaneden siler.

Gemini şunu dedi:
Anladım Yavuz, raporun sadece metin içeriğini hazırlıyorum. Aşağıdaki içeriği kopyalayıp bir .md dosyasına yapıştırdığında yaklaşık 70-80 satırlık, zengin içerikli bir teknik rapor elde edeceksin.

🏛️ Teknik Rapor: API Mantığı (REST & JSON Temelleri)
Hazırlayan: Yavuz Selim Karakülah

Öğrenci No: 232511043

Konu: API Mimarisi, HTTP Metotları ve JSON Veri Yapısı

Kategori: Backend Geliştirme Temelleri / Sistemler Arası İletişim

## 1. API NEDİR VE NEDEN VARDIR?
API (Application Programming Interface), iki farklı yazılımın birbiriyle güvenli ve standart bir şekilde konuşmasını sağlayan bir arayüzdür.

### 1.1. API'nin Temel Amacı
Veri Paylaşımı: Veritabanındaki veriyi doğrudan açmak yerine, kontrollü bir şekilde dış dünyaya sunar.

Soyutlama: Arka plandaki binlerce satırlık kodu gizleyerek, kullanıcıya sadece "istek yap ve cevap al" kolaylığı sağlar.

Platform Bağımsızlığı: Yazılan tek bir backend, hem Android hem iOS hem de Web uygulamalarına aynı veriyi gönderebilir.

### 1.2. Neden İhtiyaç Duyarız?
Modern yazılımlar artık "Monolitik" (tek parça) yapıdan "Microservice" (küçük parçalar) yapısına geçmiştir. API'ler bu parçaların birbiriyle uyum içinde çalışmasını sağlayan tek standarttır.

## 2. REST MİMARİSİ VE HTTP METOTLARI
REST (Representational State Transfer), web üzerinden veri alışverişi yaparken kullanılan en yaygın mimari stildir.

### 2.1. Temel HTTP Metotları (CRUD İşlemleri)
Bir API üzerinden işlem yaparken kullanılan standart fiiller şunlardır:

GET (Read): Sunucudan veri çekmek için kullanılır. Sadece okuma yapar, veriyi değiştirmez.

POST (Create): Sunucuya yeni bir veri kaydetmek için kullanılır. (Örn: Yeni bir kullanıcı oluşturma).

PUT (Update): Mevcut bir veriyi tamamen güncellemek için kullanılır. Verinin tüm alanlarını kapsar.

PATCH (Partial Update): Verinin tamamını değil, sadece belirli bir kısmını değiştirmek için kullanılır.

DELETE (Delete): Belirli bir kaynağı sunucudan kalıcı olarak silmek için kullanılır.

### 2.2. HTTP Durum Kodlarının Anlamı
Sunucu, yapılan her isteğe bir sayısal kodla cevap verir:

2xx (Başarı): 200 (OK) veya 201 (Created) işlemlerin sorunsuz bittiğini gösterir.

4xx (İstemci Hatası): 404 (Bulunamadı) veya 401 (Yetkisiz Giriş) hatalarını temsil eder.

5xx (Sunucu Hatası): 500 (İç Sunucu Hatası) sunucu tarafında bir çökme olduğunu belirtir.

## 3. JSON (JAVASCRIPT OBJECT NOTATION) YAPISI
JSON, makinelerin kolayca okuduğu ve insanların kolayca yazdığı hafif bir veri değişim formatıdır.

### 3.1. JSON Veri Tipleri ve Hiyerarşi
JSON verisi her zaman bir "Key-Value" (Anahtar-Değer) çiftinden oluşur ve şu kurallara uyar:

Nesneler (Objects): Süslü parantez { } içinde tanımlanır.

Diziler (Arrays): Köşeli parantez [ ] içinde liste şeklinde tutulur.

Veri Tipleri: String (metin), Number (sayı), Boolean (true/false) ve Null tiplerini destekler.

### 3.2. Örnek Veri Yapısı
JSON
{
  "id": 232511043,
  "ad": "Yavuz Selim",
  "soyad": "Karakülah",
  "ogrenci_mi": true,
  "yetenekler": ["Java", "JavaScript", "Linux", "API"],
  "egitim": {
    "bolum": "Bilgisayar Programcılığı",
    "durum": "Aktif"
  }
}
## 4. BASİT BİR ENDPOINT TASARIMI
Bir API tasarımı yapılırken URL'lerin (endpoint) temiz, anlaşılır ve hiyerarşik olması gerekir.

### 4.1. Endpoint Standartları
İyi bir endpoint tasarımı eylem (fiil) yerine nesne (isim) kullanır:

Yanlış: /kitaplariGetir

Doğru: GET /kitaplar
### 4.2. Kütüphane Sistemi Örneği
Metot	Endpoint	İşlem
GET	/kitaplar	Tüm kitap listesini döndürür.
GET	/kitaplar/12	12 ID numaralı kitabın detayını verir.
POST	/kitaplar	Sisteme yeni bir kitap verisi ekler.
DELETE	/kitaplar/12	İlgili kitabı kütüphaneden siler.
## 5. API GÜVENLİĞİ VE YETKİLENDİRME
API'ler her zaman dışarıya tamamen açık olmaz; veri güvenliğini sağlamak için şu yöntemler kullanılır:

API Key: Uygulamaya özel verilen bir anahtar kodudur.

OAuth2 / JWT: Kullanıcı giriş yaptıktan sonra verilen geçici dijital jetonlardır (Token).

💡 Kazanç: Backend Dünyasına Giriş
API mantığını kavramak, sizi sadece bir "kod yazarı" olmaktan çıkarıp, sistemlerin nasıl entegre edileceğini bilen bir "yazılım mimarı" yoluna sokar. Frontend ile Backend arasındaki veri trafiğini yönetmek, profesyonel yazılım dünyasının en kritik becerisidir.