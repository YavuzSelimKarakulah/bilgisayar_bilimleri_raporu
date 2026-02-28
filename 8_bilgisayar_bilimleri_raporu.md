## 1. Relational Database (İlişkisel Veritabanı) Nedir?
İlişkisel veritabanı, verilerin birbirleriyle bağlantılı tablolar (table) halinde tutulduğu bir sistemdir. Her tablo satırlardan (records) ve sütunlardan (columns) oluşur.

Mantık
Veriyi tek bir büyük yığın yerine, mantıksal parçalara bölerek (Normalizasyon) saklar.

Örnek: "Siparişler" tablosu ile "Müşteriler" tablosu birbirinden ayrıdır ama birbiriyle ilişkilidir.

Popüler Örnekler
PostgreSQL

MySQL

MS SQL Server

Oracle

## 2. Temel Anahtarlar: Primary Key ve Foreign Key
Veritabanında karmaşayı önleyen en önemli kurallar "Key" yani anahtar mekanizmalarıdır.

Primary Key (Birincil Anahtar)
Bir tablodaki her satırı benzersiz (unique) kılan kimlik numarasıdır.

Asla boş olamaz ve tekrar edemez.

Örnek: T.C. Kimlik numaranız sizin kişisel Primary Key’inizdir.

Foreign Key (Yabancı Anahtar)
Bir tablodaki veriyi başka bir tabloyla ilişkilendirmek için kullanılır.

Bir tablonun Primary Key'i, başka bir tabloda Foreign Key olarak yer alır.

Örnek: "Siparişler" tablosundaki Musteri_ID sütunu, "Müşteriler" tablosundaki anahtara işaret eder.

## 3. Temel SQL Komutları (SELECT, JOIN, GROUP BY)
Veritabanıyla konuşmak için kullandığımız dilin en kritik kelimeleri şunlardır:

SELECT
Veritabanından veri çekmek (okumak) için kullanılır.

"Bana şu sütunları getir" demektir.

JOIN
Farklı tablolardaki verileri, aralarındaki ilişkiyi kullanarak tek bir sonuç setinde birleştirir.

Örnek: Müşteri adı ile o müşterinin verdiği sipariş tarihini yan yana görmek için iki tabloyu Join yaparsınız.

GROUP BY
Verileri belirli bir kritere göre gruplandırır.

Genellikle matematiksel işlemlerle (SUM, AVG, COUNT) birlikte kullanılır.

## 4. Index Ne İşe Yarar?
Index (İndeks), veritabanı performansını artırmak için kullanılan bir yapıdır.

Kütüphane Benzetmesi
Bir kitabın en arkasındaki "İçindekiler" veya "Dizin" kısmı gibidir.

Aradığınız bir kelimeyi tüm kitabı sayfa sayfa okumadan (Full Table Scan) hızlıca bulmanızı sağlar.

Performans Etkisi
Avantajı: Okuma (SELECT) işlemlerini inanılmaz hızlandırır.

Dezavantajı: Veri ekleme (INSERT) veya güncelleme (UPDATE) sırasında indeksin de güncellenmesi gerektiği için bu işlemleri biraz yavaşlatabilir.

## 4. BASİT BİR ENDPOINT TASARIMI
Bir API tasarımı yapılırken URL'lerin (endpoint) temiz, anlaşılır ve hiyerarşik olması gerekir.

### 4.1. Endpoint Standartları
İyi bir endpoint tasarımı eylem (fiil) yerine nesne (isim) kullanır:

Yanlış: /kitaplariGetir

Doğru: GET /kitaplar

### 4.2. Kütüphane Sistemi Örneği
Metot,Endpoint,İşlem
GET,/kitaplar,Tüm kitap listesini döndürür.
GET,/kitaplar/12,12 ID numaralı kitabın detayını verir.
POST,/kitaplar,Sisteme yeni bir kitap verisi ekler.
DELETE,/kitaplar/12,İlgili kitabı kütüphaneden siler.

## 5. API GÜVENLİĞİ VE YETKİLENDİRME
API'ler her zaman dışarıya tamamen açık olmaz; veri güvenliğini sağlamak için şu yöntemler kullanılır:

API Key: Uygulamaya özel verilen bir anahtar kodudur.

OAuth2 / JWT: Kullanıcı giriş yaptıktan sonra verilen geçici dijital jetonlardır (Token).

💡 Kazanç: Backend Dünyasına Giriş
API mantığını kavramak, sizi sadece bir "kod yazarı" olmaktan çıkarıp, sistemlerin nasıl entegre edileceğini bilen bir "yazılım mimarı" yoluna sokar. Frontend ile Backend arasındaki veri trafiğini yönetmek, profesyonel yazılım dünyasının en kritik becerisidir.