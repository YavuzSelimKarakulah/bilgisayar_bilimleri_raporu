## 1. KATMANLI ADRESLER: IP, PORT VE DNS HİYERARŞİSİ
Bir verinin internet üzerindeki yolculuğu, doğru adresleme protokollerinin bir arada çalışmasına bağlıdır.

### 1.1. IP (Internet Protocol) ve Alt Yapısı
Tanım: Cihazların ağ üzerinde birbirini bulmasını sağlayan mantıksal adreslemedir.

IPv4 Detayı: 32 bitlik yapısıyla yaklaşık 4.3 milyar adres sunar; ancak günümüzde tükenme noktasına gelmiştir.

IPv6 Avantajı: 128 bitlik yapısı sayesinde neredeyse sonsuz adres alanı sunarak IoT (Nesnelerin İnterneti) cihazları için standart haline gelmiştir.

### 1.2. Portlar: Servislerin Giriş Kapıları
Standardizasyon: Portlar 0 ile 65535 arasındadır. İlk 1024 port "well-known" (bilinen) servisler için ayrılmıştır.

Uygulama Katmanı: Web trafiği için 80/443, güvenli veri aktarımı için 22 (SSH), veritabanı bağlantıları için ise özel portlar (Örn: 3306 - MySQL) kullanılır.

### 1.3. DNS: Çözümleme Mekanizması
Hiyerarşi: Kök sunuculardan başlayarak (Root -> TLD -> Authoritative) bir alan adını IP'ye çevirir.

Cache Mantığı: Tarayıcılar ve işletim sistemleri, hız kazanmak için daha önce ziyaret edilen sitelerin IP adreslerini yerel hafızada tutar.

## 2. TRANSPORT (TAŞIMA) KATMANI: TCP VS. UDP ANALİZİ
### 2.1. TCP: Üçlü El Sıkışma (Three-Way Handshake)
TCP, veri göndermeden önce güvenli bir hat kurar. Süreç şu şekilde işler:

SYN: İstemci bağlantı isteği gönderir.

SYN-ACK: Sunucu isteği onaylar.

ACK: İstemci onayı alır ve veri iletimi başlar.

Akış Kontrolü: Alıcının işleyebileceğinden fazla veri gönderilmesini engelleyerek ağ tıkanıklığını önler.

### 2.2. UDP: Performans Odaklı İletişim
Overhead Yok: Başlık (header) bilgisi TCP'ye göre çok daha küçüktür (8 byte vs 20 byte).

Kritik Durum: Paketlerin sırası karışabilir veya paketler kaybolabilir; bu durum yazılım seviyesinde yönetilmelidir.

## 3. AĞ PAKETLERİNİN ANATOMİSİ
Veri paketleri (datagram), ağ katmanlarında kapsüllenerek (encapsulation) iletilir:

Frame (Çerçeve): Fiziksel katman için MAC adreslerini içerir.

Packet (Paket): IP adreslerini ve yönlendirme bilgilerini barındırır.

Segment: TCP/UDP bilgilerini ve asıl uygulama verisini (payload) taşır.

## 4. PROFESYONEL TANI VE ANALİZ ARAÇLARI
Ping (ICMP): "Echo Request" paketleri ile gecikmeyi (latency) ve paket kaybını saniyelik olarak izler.

Traceroute/Tracert: Paketin geçtiği her "hop" (sıçrama) noktasında ne kadar süre harcadığını gösterir.

Nslookup/Dig: DNS kayıtlarını (A, MX, CNAME) sorgulayarak yönlendirme hatalarını teşhis eder.