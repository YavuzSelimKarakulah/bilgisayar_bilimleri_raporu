#  Software Design Patterns (Tasarım Desenleri) Raporu

Bu rapor, yazılım geliştirmede sürdürülebilirliği ve yeniden kullanılabilirliği artıran temel tasarım desenlerini ve bunların sağladığı avantajları incelemektedir.

---

## 1. Neden Tasarım Desenleri (Pattern) Kullanılır?

Tasarım desenleri "tekerleği yeniden icat etmeni" engeller.
* **Ortak Dil:** Ekip arkadaşına "Burada bir Singleton kullandım" dediğinde, kodun ne yaptığını uzun uzun anlatmana gerek kalmaz.
* **Bakım Kolaylığı:** Kodun bir yerini değiştirdiğinde her yerin patlamasını (spagetti kod) önler.
* **Genişletilebilirlik:** Yeni bir özellik eklerken mevcut kodu bozmadan üzerine inşa etmeni sağlar.

---

## 2. Creational Patterns (Kurucu Desenler)

Nesnelerin nasıl oluşturulacağıyla ilgilenirler.

###  Singleton
Bir sınıftan uygulama ömrü boyunca **sadece bir adet** nesne (instance) oluşturulmasını garanti eder.
* **Kullanım Yeri:** Veritabanı bağlantıları, Log yönetimi veya Konfigürasyon dosyaları.
* **Mantık:** Constructor'ı `private` yap, içeride statik bir örnek tut.

###  Factory Method
Nesne oluşturma mantığını istemciden gizler. Hangi nesnenin oluşturulacağına bir "fabrika" karar verir.
* **Kullanım Yeri:** Bir oyun projesinde "Düşman" sınıfından; seviyeye göre "Zombi" mi "Robot" mu üretileceğine karar veren yapı.

---

## 3. Structural Patterns (Yapısal Desenler)

Sınıfların ve nesnelerin nasıl bir araya gelip daha büyük yapılar oluşturacağıyla ilgilenirler.

###  Adapter (Adaptör)
Birbirleriyle uyumsuz arayüzlere (interface) sahip iki yapının birlikte çalışmasını sağlar.
* **Örnek:** Mevcut sistemin `JSON` bekliyor ama dışarıdan bir kütüphane `XML` gönderiyor. Araya bir "Adaptör" koyarak veriyi dönüştürürsün.

###  Decorator
Bir nesneye, mevcut yapısını değiştirmeden dinamik olarak yeni özellikler eklemeni sağlar.
* **Örnek:** Düz bir "Kahve" nesnesine; "Süt", "Şeker" veya "Krema" dekoratörleri ekleyerek farklı kahve türleri oluşturmak.

---

## 4. Behavioral Patterns (Davranışsal Desenler)

Nesneler arasındaki iletişim ve sorumlulukların dağıtımıyla ilgilenirler.

###  Strategy
Bir işin yapılabileceği farklı algoritmaları (yöntemleri) birbirinden ayırır ve çalışma anında (runtime) hangisinin kullanılacağını seçmeni sağlar.
* **Kullanım Yeri:** Bir e-ticaret sitesinde ödeme yöntemleri (Kredi Kartı, PayPal, Kripto). Hepsi "Öde" işlemini yapar ama mantıkları farklıdır.

###  Observer (Gözlemci)
Bir nesnede değişiklik olduğunda, ona bağlı olan diğer tüm nesnelerin otomatik olarak haberdar edilmesini sağlar.
* **Kullanım Yeri:** YouTube'da bir kanala abone olduğunda bildirim gelmesi. Kanal (Subject), aboneler (Observers).

---

## 5. Elde Edilecek Kazanç (The Payoff)

* **Junior vs. Senior Farkı:** Junior kod yazar (işi bitirir), Senior ise "mimari" kurar (değişime açık bırakır).
* **Loose Coupling (Gevşek Bağlılık):** Sınıfların birbirine göbekten bağlı olmamasını sağlayarak test edilebilirliği artırırsın.
* **Kodun Ömrü:** Pattern kullanılan projeler yıllar sonra bile kolayca güncellenebilir.

---
> **Unutma:** Her yere pattern sıkıştırmaya çalışmak (Over-engineering) bir hastalıktır. İhtiyaç olduğunda doğru deseni seçmek asıl yetenektir.