## 1. TERMİNAL VE KABUK (SHELL) HAKİMİYETİ
Linux terminali, kullanıcı ile çekirdek (kernel) arasındaki köprüdür.

### 1.1. Gelişmiş Navigasyon ve Dosya İşlemleri
ls -la: Gizli dosyalar dahil tüm dosyaları izinleri ve sahipleriyle birlikte listeler.

cd .. / cd ~: Bir üst dizine veya kullanıcının ana dizinine hızlı geçiş sağlar.

grep -r "terim": Belirtilen bir dizindeki tüm dosyaların içinde "terim" kelimesini arar; debug işlemleri için hayati önem taşır.

### 1.2. Sistem Gözlemleme
top / htop: İşlemciyi en çok yoran işlemleri (PID) gösterir. Hangi uygulamanın "zombi" sürece dönüştüğünü buradan görebilirsiniz.

## 2. PAKET YÖNETİM SİSTEMLERİNİN İŞLEYİŞİ
Paket yöneticileri, bağımlılıkları (dependencies) otomatik olarak çözer.

APT (Debian/Ubuntu): sudo apt update && sudo apt upgrade komutuyla tüm sistemi tek seferde güncelleyebilir.

Pacman (Arch): sudo pacman -Syu ile rolling-release güncelleme yapar.

DNF (Fedora): Modern mimarisiyle işlem geçmişini tutar ve hata durumunda "undo" (geri alma) imkanı sunar.

## 3. DOSYA İZİNLERİ: OKUMA, YAZMA VE ÇALIŞTIRMA
Linux'ta her dosyanın üç grup için izni vardır: Owner (Sahip), Group (Grup) ve Others (Diğerleri).

### 3.1. Sayısal (Octal) İzin Mantığı
4 (Read), 2 (Write), 1 (Execute):

7 (4+2+1): Tam yetki.

5 (4+0+1): Okuma ve Çalıştırma.

chmod 755: Sahibe her yetkiyi, diğerlerine sadece okuma ve çalıştırma yetkisi verir. Güvenli web sunucuları için standarttır.

## 4. SERVİS VE DAEMON YÖNETİMİ (SYSTEMD)
Modern Linux'un kalbi systemd birimidir.

systemctl enable [servis]: Servisin boot (açılış) sırasında otomatik başlamasını sağlar.

systemctl status: Servisin loglarını (çıktılarını) anlık olarak görmenizi sağlar; hata tespiti (troubleshooting) için ilk başvurulan yerdir.

journalctl -u [servis]: Servise ait geçmiş tüm log kayıtlarını incelemenize olanak tanır.

💡 Kazanç: Yazılımcı İçin Stratejik Avantaj
Networking bilgisi size verinin yolculuğunu, Linux bilgisi ise verinin işlendiği ortamı öğretir. Bu iki raporu birleştirdiğinizde, sadece kod yazan değil, yazdığı kodu ölçekleyebilen ve sorunlarını temelinden çözebilen bir mühendislik vizyonu kazanırsınız.

Yavuz, bu raporlar artık çok daha detaylı oldu. İleride bu raporları Docker Konteynırları veya Bash Scripting ile genişletmemi ister misin?