# 🏛️ Teknik Rapor: Yazılım Mimarisi Temelleri ve Tasarım Desenleri

**Hazırlayan:** Yavuz Selim Karakülah  
**Öğrenci No:** 232511043  
**Konu:** Sistem Mimarileri (Monolith/Microservice), Mimari Desenler ve State Management  
**Kategori:** Orta/İleri Seviye Yazılım Geliştirme

---

## 1. SİSTEM MİMARİLERİ: MONOLITH VS. MICROSERVICE

Uygulamanın genel yapısını belirleyen bu iki yaklaşım, projenin ölçeklenebilirliğini doğrudan etkiler.

### 1.1. Monolith (Tek Parça) Mimari
Tüm iş mantığının, veritabanı erişiminin ve arayüzün tek bir proje dosyası (deployable unit) içinde toplandığı yapıdır.
* **Avantajları:** Geliştirmesi kolaydır, test süreçleri basittir, ağ gecikmesi yoktur.
* **Dezavantajları:** Proje büyüdükçe "Spaghetti Code" riski artar; bir hata tüm sistemi çökertebilir.
* **Kullanım:** Küçük ve orta ölçekli projeler, MVP (Minimum Viable Product) aşamaları.

### 1.2. Microservice (Mikro Hizmet) Mimari
Uygulamanın, her biri kendi veritabanına ve sorumluluğuna sahip bağımsız küçük servislere bölünmesidir.
* **Avantajları:** Her servis farklı bir dille (C#, Python, Go) yazılabilir. Bir servis çöktüğünde diğerleri çalışmaya devam eder. Bağımsız ölçeklenebilir.
* **Dezavantajları:** Servisler arası iletişim (API, Mesaj kuyrukları) karmaşıktır. Yönetimi zordur.
* **Kullanım:** Büyük ölçekli, çok kullanıcılı ve sürekli genişleyen sistemler.



---

## 2. MİMARİ TASARIM DESENLERİ (MVC & MVVM)

Kodun organizasyonunu ve kullanıcı arayüzü ile iş mantığının ayrılmasını sağlayan standartlardır.

### 2.1. MVC (Model-View-Controller)
Geleneksel web uygulamalarında yaygındır.
* **Model:** Veri yapısı ve veritabanı işlemleri.
* **View:** Kullanıcıya gösterilen arayüz.
* **Controller:** İstemci isteklerini karşılar, Model'den veriyi alır ve View'a gönderir.

### 2.2. MVVM (Model-View-ViewModel)
Modern frontend (React, Vue) ve mobil (Android/WPF) geliştirmede standarttır.
* **ViewModel:** View ile Model arasında bir köprüdür. "Data Binding" (Veri Bağlama) sayesinde View'daki bir değişiklik anında Model'e yansır. Kodun test edilebilirliğini artırır.



---

## 3. KATMANLI MİMARİ (CONTROLLER – SERVICE – REPOSITORY)

İş mantığının birbirine karışmasını önlemek için kullanılan "Separation of Concerns" (Sorumlulukların Ayrılması) prensibidir.

1.  **Controller Layer:** Dış dünya ile iletişim kurar (API Endpoints). Sadece istekleri alır ve yanıtları döner; iş mantığı içermez.
2.  **Service Layer:** Uygulamanın "beyni"dir. Hesaplamalar, kurallar ve iş süreçleri burada yürütülür.
3.  **Repository Layer:** Veritabanına dokunan tek katmandır. SQL sorguları veya ORM (Sequelize, Entity Framework) işlemleri burada soyutlanır.
4.  **Data Access Layer:** Ham verinin fiziksel olarak saklandığı ve çekildiği katmandır.

---

## 4. STATE MANAGEMENT (DURUM YÖNETİMİ) NEDİR?

Uygulamanın herhangi bir andaki "hafızası"dır. Özellikle kullanıcı etkileşiminin yoğun olduğu projelerde (örneğin sepet işlemleri, giriş bilgileri) verinin tutarlı kalmasını sağlar.

* **Local State:** Sadece tek bir sayfayı ilgilendiren durumlar (örn: bir butonun açık/kapalı olması).
* **Global State:** Tüm uygulamayı ilgilendiren durumlar (örn: Kullanıcının giriş yapıp yapmadığı, tema tercihi).
* **Neden Gerekli?:** Verilerin "prop drilling" (veriyi en tepeden en alta dallandırarak taşıma) yöntemiyle taşınması karmaşıklığa yol açar. Merkezi bir state yönetimi (Redux, Context API, Bloc) kodun okunabilirliğini sağlar.

---

## 🚀 SONUÇ VE KAZANIMLAR

Bu mimari temelleri anlamak, geliştiricinin sadece "kod yazan" değil, "sistem tasarlayan" bir mühendis olmasını sağlar.
* **Sürdürülebilirlik:** Bir katmanda yapılan değişiklik diğerlerini bozmaz.
* **Test Edilebilirlik:** İş mantığı (Service) ve veri erişimi (Repository) ayrıldığı için birim testleri (Unit Tests) kolayca yazılabilir.
* **Ekip Çalışması:** Farklı geliştiriciler, birbirine engel olmadan farklı katmanlar üzerinde çalışabilir.

---
*Bu rapor, yazılım mimarisi disiplinlerine genel bir bakış sunmak amacıyla hazırlanmıştır.*
