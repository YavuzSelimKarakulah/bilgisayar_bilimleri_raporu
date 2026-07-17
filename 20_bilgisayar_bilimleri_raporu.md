# Bölüm 19: CI/CD (Continuous Integration / Continuous Deployment) Mantığı ve Süreçleri - Kapsamlı Rapor

Modern yazılım mühendisliğinde ve DevOps kültüründe, kodun yerel geliştirme ortamından çıkıp güvenli, test edilmiş ve hatasız bir şekilde son kullanıcıya ulaşmasını sağlayan en kritik altyapı **CI/CD (Continuous Integration / Continuous Deployment)** sistemleridir.

Özellikle birden fazla geliştiricinin, örneğin 3 kişilik bir ekibin ortaklaşa yürüttüğü web uygulaması (örneğin bir öğrenci yoklama sistemi otomasyonu) projelerinde, farklı bilgisayarlarda yazılan kodların aynı GitHub deposu (repository) üzerinde çakışmadan (overwrite olmadan) birleştirilmesi ve yönetilmesi CI/CD süreçleri ile güvence altına alınır. Bu rapor, Build - Test - Deploy boru hattının (pipeline) çalışma mantığını ve sağladığı mühendislik avantajlarını detaylandırmaktadır.

---

## 1. Continuous Integration (Sürekli Entegrasyon - CI)

Sürekli Entegrasyon, bir projede çalışan geliştiricilerin kod değişikliklerini merkezi bir sunucudaki ortak bir dal (branch) üzerine düzenli ve sık olarak entegre etme pratiğidir. Geleneksel yöntemlerde kod birleştirme işlemi haftalar sürebilen ve "Integration Hell" (Entegrasyon Cehennemi) adı verilen kaoslara yol açarken, CI bu süreci günlük hatta saatlik rutinlere böler.

**Süreç ve Çalışma Mantığı:**
* **Tetiklenme (Trigger):** Ekip üyesi, kendi branch'inde çalışmasını tamamlayıp kodu depoya `push` ettiğinde veya bir Pull Request (PR) açtığında CI süreci otomatik olarak tetiklenir.
* **Bağımlılıkların Çözülmesi (Dependency Resolution):** Uygulamanın çalışması için gereken ortam hazırlanır. Örneğin; Node.js ve Express.js tabanlı bir arka uç (backend) projesinde `npm install` ile paketler indirilir veya C, C++, Java gibi dillerle yazılmış projelerde ilgili derleyici araçları ve kütüphaneler ayağa kaldırılır.
* **Statik Kod Analizi (Linting):** Yazılan kodun, takımın belirlediği standartlara (isimlendirme kuralları, mimari kısıtlamalar) uyup uymadığı statik analiz araçlarıyla kontrol edilir.
* **Otomatik Testler (Automated Testing):** CI sisteminin kalbidir. Yazılan veri tabanı modellerinin, API yönlendirmelerinin (route) veya algoritmaların bozulup bozulmadığı Unit (Birim) ve Integration (Entegrasyon) testleri ile otomatik sınanır.
* **Koruma Mekanizması:** Eğer bu aşamalardan biri bile başarısız olursa, süreç anında durdurulur ve geliştiriciye detaylı bir hata logu (log) gönderilir. Böylece hatalı kod ana (main/master) branch'e sızmamış olur.

---

## 2. Continuous Deployment ve Continuous Delivery (Sürekli Dağıtım / Teslimat - CD)

Sürekli Dağıtım ve Teslimat, CI aşamasından (Build ve Test) başarıyla geçen, yani hatasız olduğu kanıtlanmış kodun hedef sunuculara (canlı ortama veya test ortamına) aktarılması otomasyonudur.

* **Continuous Delivery (Sürekli Teslimat):** Kod, canlı ortama çıkmaya her an hazırdır ve genellikle bir test (staging) veya UAT (Kullanıcı Kabul Testi) sunucusuna otomatik olarak yüklenir. Ancak uygulamanın son kullanıcının göreceği canlı ortama (production) geçişi için takım lideri veya müşteri tarafından manuel bir onay (bir butona basılması) gerekir.
* **Continuous Deployment (Sürekli Dağıtım):** Süreçte insan müdahalesi tamamen ortadan kaldırılmıştır. Tüm testleri başarıyla geçen yeni özellikler veya hata düzeltmeleri (bug fix), herhangi bir manuel onaya ihtiyaç duymadan otomatik olarak canlı sunucuya yüklenir ve saniyeler içinde kullanıcılara sunulur.

---

## 3. Build – Test – Deploy Pipeline (Boru Hattı) Mimarisi

Bu üç aşama birbirini takip eden zincirleme bir reaksiyon oluşturur. GitHub Actions, Jenkins, Travis CI veya GitLab CI gibi araçlar üzerinden genellikle yapılandırma dosyaları (örneğin YAML - `.yml`) ile kodlanarak yönetilir.

### A. Build Aşaması (Derleme ve İnşa)
* Uygulamanın insan tarafından okunabilen ham kaynak kodunun (source code), bilgisayar veya sunucu tarafından doğrudan çalıştırılabilir formata getirilmesidir. 
* Projenin kullandığı teknolojiye göre kaynak kod yorumlanabilir yapıya hazırlanır veya makine koduna / byte-code'a dönüştürülür.
* Tüm ortam değişkenleri (environment variables) ayarlanır.
* Süreç sonunda uygulamanın sunucuya gönderilecek "paketlenmiş" ve taşınabilir hali (Artifact veya Docker Container imajı) oluşturulur.

### B. Test Aşaması (Kalite ve Güvenlik Kapısı)
* **İzolasyonlu Denetim:** Pipeline, yeni kodu diğer sistemlerden bağımsız, izole bir konteyner ortamında çalıştırır.
* **Regresyon Kontrolü:** Eklenen yeni bir özelliğin, uygulamanın önceden sorunsuz çalışan kısımlarını bozup bozmadığı denetlenir. 
* Performans ve güvenlik açıklarına dair taramalar da bu adımda yapılabilir. Testleri %100 başarıyla geçen kod "dağıtıma uygun" damgası alır.

### C. Deploy Aşaması (Yayınlama ve Dağıtım)
* Hazırlanan ve test edilen güvenilir kod paketinin bulut sunucuya, VPS'e veya ilgili hosting ortamına iletilmesidir.
* **Zero-Downtime (Kesintisiz Geçiş):** Modern CD süreçlerinde, Blue-Green Deployment gibi stratejiler sayesinde sistem duraklamadan yeni versiyona geçer. Kullanıcılar sistemi kullanırken herhangi bir kesinti veya bakım ekranı görmezler.

---

## 4. CI/CD Otomasyonunun Sağladığı Kritik Kazançlar

1. **Kodun Otomatik Test Edilmesi ve Erken Hata Tespiti:** 
   * Hatalar yerel bilgisayardan çıkıp ortak depoya ulaştığı an yakalanır. "Benim bilgisayarımda sorunsuz çalışıyordu" argümanı geçerliliğini yitirir, çünkü kod herkes için standart ve bağımsız bir pipeline sunucusunda test edilir.
2. **Kodun Otomatik ve Güvenilir Bir Şekilde Yayınlanması:**
   * Geleneksel yöntemlerdeki gibi FTP üzerinden manuel dosya kopyalamak, sunucu ayarlarını elle yapılandırmak gibi eski, yorucu ve insan hatasına açık yöntemler tarih olur. Sistem kendi kendini hatasız bir şekilde dakikalar içinde günceller.
3. **Anında Geri Dönüş (Rollback) ve Versiyon Güvenliği:**
   * Eğer canlı ortama alınan yeni versiyonda beklenmedik, testlerden kaçmış kritik bir sorun çıkarsa, CI/CD sistemleri sayesinde tek bir komutla eski, stabil çalışan versiyona anında geri dönülebilir (rollback). Bu, kriz yönetimini inanılmaz derecede kolaylaştırır.
4. **Takım İçi Verimlilik ve Odak Artışı:**
   * Geliştiriciler tekrarlayan sunucu ayarlamaları, manuel test koşmaları ve derleme işlemleriyle değerli vakitlerini kaybetmezler. Bunun yerine sadece temiz kod yazmaya, algoritmaları optimize etmeye ve yeni özellikler geliştirmeye odaklanırlar.
5. **Daha Hızlı Ürün Teslimatı (Time-to-Market):**
   * Yeni bir fikir veya müşteri talebi, geliştirildiği gün hatta geliştirildiği saat içerisinde güvenle canlıya alınabilir. Bu hız, yazılım projelerine büyük bir rekabet avantajı sağlar