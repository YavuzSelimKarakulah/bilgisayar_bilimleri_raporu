l# 📑 Kapsamlı Teknik Rapor: Bellek Mimarisi ve Yazılım Optimizasyonu

**Hazırlayan:** Yavuz Selim Karakülah  
**Öğrenci No:** 232511043  
**Konu:** Bellek Yönetimi (Stack/Heap), Garbage Collection Dinamikleri ve Performans Analizi  
**Versiyon:** 2.0 (Genişletilmiş Teorik Metin)

---

## 1. BELLEK YÖNETİMİNİN TEMELLERİ
Bilgisayar bilimlerinde bellek yönetimi, sınırlı bir kaynak olan RAM'in (Random Access Memory) uygulamalar arasında adil, güvenli ve hızlı bir şekilde paylaştırılması sürecidir. Bellek yönetimi hataları, modern yazılımların %70'inden fazlasının performans kaybı yaşamasının temel sebebidir.

---

## 2. STACK VE HEAP: DERİNLEMESİNE BAKIŞ

Yazılım çalışma zamanında belleği iki ana mantıksal segmente ayırırız. Bu ayrım, verinin **yaşam ömrü (lifetime)** ve **erişilebilirliği (accessibility)** üzerine kuruludur.

### 2.1. Stack (Yığın) Mimarisi
Stack, işletim sistemi tarafından yönetilen ve "Sıralı Erişim" prensibine dayanan bir bellek bölgesidir.
* **Hiyerarşik Yapı:** Metotlar çağrıldığında bellekte bir "Stack Frame" açılır. Metot sonlandığında bu frame tamamen bellekten düşer.
* **Performans:** İşlemci (CPU), Stack adresine doğrudan erişebilir. Pointer takibi gerektirmediği için erişim hızı nanosaniyeler mertebesindedir.
* **Statik Tahsis:** Derleme zamanında boyutu bilinen veriler burada saklanır.

### 2.2. Heap (Öbek) Mimarisi
Heap, uygulamanın tüm parçaları tarafından paylaşılan, daha karmaşık ve büyük verilerin saklandığı "Serbest Alan"dır.
* **Dinamik Tahsis:** Verinin boyutu çalışma zamanında (runtime) belirleniyorsa Heap kullanılır.
* **Esneklik:** Veriler Stack'teki gibi sıralı değil, dağınık bir şekilde yerleşir. Bu durum, veriye erişmek için "Pointer" (işaretçi) kullanımını zorunlu kılar.
* **Yönetim Zorluğu:** Belleğin neresinin boş, neresinin dolu olduğunun takibi ek bir yönetim maliyeti (Overhead) getirir.



---

## 3. GARBAGE COLLECTION (GC) OPERASYONEL SÜREÇLERİ

Garbage Collector, yazılımcıyı bellek boşaltma yükünden kurtaran ancak arka planda ciddi bir algoritma çalıştıran bir servistir.

### 3.1. Nesilsel (Generational) Hipotez
GC, "Yeni oluşturulan nesneler, eski nesnelere göre daha çabuk ölür" prensibiyle çalışır. Bu yüzden belleği nesillere ayırır:
1.  **Generation 0 (Gen 0):** En yeni nesnelerin toplandığı alandır. Temizleme işlemi milisaniyeler sürer ve çok sık gerçekleşir.
2.  **Generation 1 (Gen 1):** Gen 0 temizliğinden sağ çıkan nesnelerin "terfi" ettirildiği tampon bölgedir.
3.  **Generation 2 (Gen 2):** Statik veriler ve uzun ömürlü nesneler burada birikir. Buranın temizlenmesi (Full GC), uygulamanın anlık olarak donmasına ("Stop the World") neden olabilir.



### 3.2. Mark-Sweep-Compact Algoritması
GC devreye girdiğinde şu üç aşamayı izler:
* **İşaretleme (Mark):** Tüm nesne ağacı taranır. Aktif olarak kullanılanlara "canlı" damgası vurulur.
* **Süpürme (Sweep):** Damgası olmayan nesnelerin bellek adresleri boşa çıkarılır.
* **Sıkıştırma (Compact):** Silinen nesnelerin yarattığı boşluklar, canlı nesnelerin kaydırılmasıyla kapatılır. Böylece bellek parçalanması (fragmentation) önlenir.

---

## 4. MEMORY LEAK (BELLEK SIZINTISI) VE SİSTEMİK ETKİLERİ

Bellek sızıntısı, teknik olarak bir nesnenin kullanım dışı kalmasına rağmen, bir referans bağından dolayı GC tarafından "canlı" sanılmasıdır.

### 4.2. Sızıntının Yaygın Nedenleri
* **Statik Referanslar:** Uygulama ömrü boyunca yaşayan statik listelere eklenen nesneler asla temizlenmez.
* **Olay Dinleyiciler (Events):** Bir nesne, başka bir nesnenin olayına abone olduğunda, aralarında koparılamaz bir bağ oluşur. Abonelik sonlandırılmazsa her iki nesne de bellekte hapsolur.
* **Döngüsel Referanslar:** İki nesnenin birbirine işaret etmesi sonucu oluşan karmaşık yapılar, eski GC algoritmalarını yanıltabilir.

### 4.3. Performans Kayıpları
Sızıntı arttıkça;
1.  İşletim sistemi sürekli sayfalama (paging) yapar, bu da disk hızına düşmenize neden olur.
2.  GC, belleği boşaltabilmek için daha sık çalışmaya başlar ve CPU'yu meşgul eder.
3.  Uygulama yanıt vermeyi keser ve sonunda işletim sistemi tarafından sonlandırılır.

---

## 5. OPTİMİZASYON STRATEJİLERİ VE SONUÇ

Yüksek performanslı bir kod yazmak için bellek farkındalığı şarttır:

* **Nesne Yaşam Döngüsü:** Nesneleri sadece ihtiyaç duyulan en dar kapsamda (scope) oluşturun.
* **Kapasite Yönetimi:** Dinamik koleksiyonların (List, Map vb.) başlangıç kapasitelerini belirleyerek bellekte sürekli yeniden boyutlandırma yapılmasının önüne geçin.
* **Büyük Nesne Yönetimi (LOH):** Çok büyük nesnelerin (85KB üzeri) Heap'te özel bir alana (Large Object Heap) alındığını ve buranın çok zor temizlendiğini unutmayın.
* **Tanılama:** Geliştirme sürecinde düzenli olarak "Memory Profiler" araçlarıyla bellek dökümü (Snapshot) alarak artışları gözlemleyin.

---
*Bu teknik döküman, bellek yönetimi prensiplerinin teorik çerçevesini oluşturmak üzere hazırlanmıştır.*