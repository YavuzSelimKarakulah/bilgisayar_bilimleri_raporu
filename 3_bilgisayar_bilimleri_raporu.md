# 3. RAPOR

## Ağ Temelleri (Networking)

Bu raporda temel ağ kavramları olan IP, Port, DNS, TCP, UDP; paket yapısı; ayrıca ping, traceroute ve nslookup araçlarının kullanım amacı açıklanmaktadır.

---

## 1. IP – Port – DNS – TCP – UDP Nedir?

### **IP (Internet Protocol)**
- İnternetteki her cihazın kimlik numarasıdır.
- Veri gönderilirken kaynak ve hedef adreslerini belirtir.
- Türleri:
  - **IPv4:** 192.168.1.5 gibi
  - **IPv6:** Çok daha uzun adresler (ör. fe80::1c2f)

---

### **Port**
- Bir cihazdaki uygulamaları ayırmaya yarar.
- IP ev adresiyse, port kapı numarasıdır.
- Önemli portlar:
  - 80 → HTTP
  - 443 → HTTPS
  - 53 → DNS

---

### **DNS (Domain Name System)**
- Domain isimlerini IP adreslerine çevirir.
- Örneğin:  
  `google.com → 142.250.xxx.xxx`
- İnsanların okuduğu isimleri bilgisayarın anlayacağı IP’ye dönüştürür.

---

### **TCP (Transmission Control Protocol)**
- Güvenilir veri aktarımı sağlar.
- Paket kaybolursa tekrar gönderilir.
- Sıralama kontrolü vardır.
- Kullanım alanları:
  - Web (HTTP/HTTPS)
  - E-posta
  - Dosya transferi

**Avantaj:** Güvenilir  
**Dezavantaj:** Yavaş

---

### **UDP (User Datagram Protocol)**
- Bağlantısız, çok hızlı bir protokoldür.
- Paket kaybını önemsemez.
- Kullanım alanları:
  - Oyunlar
  - Canlı yayınlar
  - Sesli aramalar (VoIP)

**Avantaj:** Çok hızlı  
**Dezavantaj:** Güvenilir değildir

---

## 2. Paket Yapısı Nasıl Çalışır?

Ağ üzerinde veriler **paketlere bölünerek** gönderilir.

Bir paket 3 ana bölümden oluşur:

### **1. Header (Başlık)**
- Kaynak IP
- Hedef IP
- Kaynak Port
- Hedef Port
- Protokol (TCP/UDP)
- Paket sıra numarası

### **2. Payload (Veri Bölümü)**
- Gönderilmek istenen gerçek veri.

### **3. Checksum**
- Hata kontrol bilgisi.

Veriler gönderilirken paketlere ayrılır, hedefte tekrar birleştirilir.

---

## 3. Ping, Traceroute, Nslookup Ne İşe Yarar?

### **Ping**
- Bir hedefe ulaşılıp ulaşılamadığını test eder.
- ICMP protokolünü kullanır.
- Gecikme süresini (ms) ölçer.

**Örnek:**
```bash
ping google.com
