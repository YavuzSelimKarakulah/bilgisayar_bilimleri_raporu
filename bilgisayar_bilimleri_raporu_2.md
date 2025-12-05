
## 1. Kernel Nedir?

Kernel (çekirdek), işletim sisteminin en temel ve en kritik bileşenidir. Donanım ile uygulamalar arasında bir arayüz görevi görür ve sistem kaynaklarının güvenli biçimde yönetilmesini sağlar.

### Kernel’in Başlıca Görevleri
- **Bellek Yönetimi:** RAM’in süreçler arasında dağıtılması ve korunması.
- **Süreç Yönetimi:** Process oluşturma, sonlandırma ve CPU paylaşımı.  
- **Cihaz Yönetimi:** Donanım aygıtlarına sürücüler aracılığıyla erişim.
- **Dosya Sistemi Yönetimi:** Verilerin depolanması, okunması, yazılması.
- **Güvenlik:** Yetkilendirme, izolasyon ve erişim kontrol mekanizmaları.

### Kernel Türleri
- **Monolitik Kernel:** Tüm servisler tek bir büyük yapıdadır (Ör: Linux).
- **Microkernel:** Sadece temel işlevler çekirdekte, diğerleri kullanıcı modunda (Ör: Minix).
- **Hybrid Kernel:** Her iki yapının özelliklerini birleştirir (Ör: Windows, macOS).

---

## 2. Süreç (Process) ve İş Parçacığı (Thread) Farkı

Bir uygulama çalıştırıldığında işletim sistemi o uygulama için bir **process** oluşturur. Process yapısı, programın çalışması için gerekli bellek alanı ve kaynakları içerir.

### Process (Süreç) Nedir?
- İşletim sistemi tarafından izole edilen bağımsız bir çalışma birimidir.
- Her process’in **kendine ait bellek alanı** vardır.
- Process çökmesi diğer süreçleri doğrudan etkilemez.

### Thread (İş Parçacığı) Nedir?
- Process içinde çalışan daha küçük yürütme birimleridir.
- Aynı process içindeki tüm thread’ler **aynı bellek alanını paylaşır**.
- Oluşturma maliyeti düşüktür ve paralel çalışmayı kolaylaştırır.


## 3. Bellek Yönetimi Nasıl Yapılır?

Bellek yönetimi, RAM’in verimli kullanılması ve süreçlerin birbirini etkilemeden çalışması için kullanılan mekanizmaları kapsar.

### 1. Sayfalama (Paging)
Bellek sabit boyutlu parçalara ayrılır:
- Program tarafında: **Sayfa (page)**  
- RAM tarafında: **Çerçeve (frame)**  

Sayfalama sayesinde programlar fiziksel belleğin boyutundan bağımsız çalışabilir. Kullanılmayan sayfalar diske taşınarak sanal bellek oluşturulur.

### 2. Segmentasyon
Bellek, programın mantıksal bölümlerine göre ayrılır (kod, veri, yığın). Daha esnek fakat günümüzde paging kadar yaygın değildir.

### 3. Sanal Bellek (Virtual Memory)
RAM yetmediğinde işletim sistemi diski geçici bellek gibi kullanır. Bu, programların çalışmaya devam etmesini sağlar ancak performansı düşürür.

### 4. Bellek Koruma
İşletim sistemi, bir sürecin başka bir sürecin belleğine izinsiz erişmesini engeller. Bu, güvenlik ve sistem stabilitesi için zorunludur.

---

## 4. CPU Zamanlayıcıları (CPU Scheduling)

CPU zamanlayıcısı, birden fazla sürecin CPU'yu nasıl paylaşacağını belirleyen algoritmalardır. CPU aynı anda tek bir süreç çalıştırabilir, bu nedenle süreçler sırayla çalıştırılır.

### Yaygın Zamanlama Algoritmaları

#### 1. FCFS (First Come, First Served)
- İlk gelen sürecin önce çalıştırıldığı basit bir yöntemdir.

#### 2. SJF (Shortest Job First)
- Tahmin edilen çalışma süresi en kısa olan süreç öncelikli çalıştırılır.

#### 3. Round Robin
- Her sürece belirli bir zaman dilimi (quantum) verilir.
- Çoklu kullanıcı sistemlerinde yaygın olarak kullanılır.

#### 4. Priority Scheduling
- Her süreç belirli bir öncelik değerine sahiptir.
- Yüksek öncelikli süreçler daha önce çalıştırılır.

#### 5. Multilevel Feedback Queue
- Süreçler farklı kuyruklara ayrılır.
- Sistem gerçek zamanlı olarak süreci daha uygun bir kuyruğa taşıyabilir.

---

## Kazanç

Bu konuları öğrenmek, yazılım geliştiricilerin programlarının bilgisayar üzerinde **nerede, nasıl ve hangi mekanizmalarla** çalıştığını anlamasını sağlar.  
Performans analizi, sorun giderme ve verimli kod yazma açısından bu bilgiler kritik öneme sahiptir.

