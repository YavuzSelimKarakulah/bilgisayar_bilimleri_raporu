#  Concurrency ve Parallel Programming: Derinlemesine Teknik Bakış

Bu rapor, eşzamanlı ve paralel programlamanın mimari detaylarını, risklerini ve modern çözüm yöntemlerini kapsamlı bir şekilde ele alır.

---

## 1. Concurrency vs. Parallelism: Mimari Farklar

Birçok kişi bu ikisini aynı sanır ama aradaki fark **"yönetim"** ile **"icra"** arasındadır.

* **Concurrency (Eşzamanlılık):** Bir yapıdır. Yazılımın aynı anda birden fazla işi ilerletebilecek şekilde tasarlanmasıdır. Tek çekirdekli bir makinede bile concurrency olabilir; CPU, her işe milisaniyelik zaman dilimleri (time-slicing) ayırarak aralarında geçiş yapar.
* **Parallelism (Paralellik):** Bir uygulamadır. Donanım seviyesinde aynı anda birden fazla işlemin gerçekten yürümesidir. 
    * **Data Parallelism:** Aynı verinin farklı parçalarını farklı çekirdeklerde işlemek (Örn: Bir dizinin yarısını Core 1, diğer yarısını Core 2'nin toplaması).
    * **Task Parallelism:** Tamamen farklı görevlerin farklı çekirdeklerde çalışması (Örn: Bir thread log yazarken, diğerinin veritabanı sorgusu yapması).

---

## 2. Race Condition: Neden "Yarış"?

İsmi, iki thread'in paylaşılan kaynağa ulaşmak için adeta "yarışmasından" gelir. İşlemci seviyesinde bir değişkeni artırmak (`x++`) aslında 3 adımdır:
1.  Değeri bellekten oku (Read).
2.  Değeri 1 artır (Modify).
3.  Yeni değeri belleğe yaz (Write).

**Kritik Senaryo:** Thread A 1. adımı yapar (değer 5). Tam o sırada CPU, Thread B'ye geçer. Thread B de okur (değer hala 5) ve yazma işlemini bitirir (değer 6 olur). Tekrar Thread A'ya dönüldüğünde, A kendi elindeki 5 değerini 6 yapar ve yazar. 
*Sonuç:* İki kez artırma yapılmasına rağmen değer sadece 1 artmış olur. İşte bu **Race Condition**'dır.

---

## 3. Senkronizasyonun "Kutsal Üçlüsü" ve Ekstra Detaylar

###  Mutex vs. Binary Semaphore
* **Mutex:** "Ownership" (Sahiplik) kavramı vardır. Kilidi kim vurduysa sadece o açabilir. Genellikle kritik kod bölgelerini korumak için kullanılır.
* **Binary Semaphore:** Sahiplik yoktur. Bir thread kilitleyebilir, bambaşka bir thread o kilidi açabilir. Bu yüzden "sinyalleşme" (signaling) için daha uygundur.

###  Counting Semaphore
Birden fazla özdeş kaynağın (Örn: Havuzdaki 10 veritabanı bağlantısı) yönetilmesinde kullanılır. Sayı sıfıra ulaştığında gelen thread'ler bloklanır (uyutulur).

###  Spinlock (Hızlı ama Riskli)
Thread'in uyumak yerine, kilit açılana kadar sürekli bir `while` döngüsü içinde kilidi kontrol etmesidir. 
* **Avantajı:** Context switch (thread değiştirme) maliyeti yoktur.
* **Dezavantajı:** Kilit uzun süre açılmazsa CPU'yu %100 kullanıp boşa harcar.

---

## 4. Kritik Kavram: Deadlock (Ölümcül Kilitlenme)

Çok çekirdekli sistemlerde en büyük korku budur. 
* Thread 1, A kaynağını kilitler ve B'yi ister.
* Thread 2, B kaynağını kilitler ve A'yı ister.
* **Sonuç:** İkisi de sonsuza kadar birbirini bekler. Program donar.

---

## 5. Modern Yaklaşım: Lock-Free Programming ve Atomic Operations

Kilit kullanmak (Lock/Mutex) performans maliyeti getirir (CPU'yu durdurur). Modern dillerde (C#, Java, C++) **Atomic** işlemler vardır. İşlemci seviyesinde (CPU instruction) "oku-artır-yaz" işlemini tek bir bölünemez adımda yaparlar. Kilit kullanmadan "Race Condition"ı engellemenin en hızlı yoludur.

---

## 6. Sonuç ve Mühendislik Kazancı

* **Verimlilik:** CPU'nun bekleme sürelerini (I/O bekleme gibi) başka işlerle doldurursun.
* **Responsiveness:** Arayüzün donmasını engellersin (arka planda hesaplama yaparken kullanıcı tıklamaya devam edebilir).
* **Hız:** İşlem süresini çekirdek sayısına bölerek (ideal şartlarda) performansı katlarsın.

---
