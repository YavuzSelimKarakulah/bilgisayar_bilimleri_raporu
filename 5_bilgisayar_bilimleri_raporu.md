🏛️ Teknik Rapor: Linux Temelleri ve İşletim Sistemi Yönetimi
Hazırlayan: Yavuz Selim Karakülah
Öğrenci No: 232511043
Konu: Terminal Komutları, Paket Yönetimi, Dosya İzinleri ve Servis Yönetimi
Kategori: Temel Seviye Sistem Yönetimi / Yazılım Altyapısı

## 1. TERMİNAL KOMUTLARI (TEMEL NAVİGASYON VE ANALİZ)
Linux ekosisteminde terminal, sistemle doğrudan iletişim kurmanın en güçlü yoludur.

### 1.1. Dosya ve Dizin Yönetimi
ls (List): Bulunulan dizindeki dosya ve klasörleri listeler.

cd (Change Directory): Dizinler arasında geçiş yapmayı sağlar.

mkdir (Make Directory): Yeni bir klasör/dizin oluşturur.

### 1.2. Metin İşleme ve Sistem İzleme
grep (Global Regular Expression Print): Dosyalar veya çıktılar içerisinde belirli bir metin kalıbını aramaya yarar.

top (Table of Processes): Sistem kaynaklarının (CPU, RAM) kullanımını ve çalışan işlemleri anlık olarak görüntüler.

## 2. PAKET YÖNETİMİ (YAZILIM KURULUMU)
Linux dağıtımları, yazılımları yönetmek için merkezi depolar ve paket yöneticileri kullanır.

APT (Advanced Package Tool): Debian ve Ubuntu tabanlı sistemlerde kullanılır (apt install).

PACMAN: Arch Linux tabanlı sistemlerin hızlı paket yöneticisidir.

DNF (Dandified YUM): Fedora, RHEL ve CentOS sistemlerinde kullanılan modern paket yöneticisidir.

## 3. DOSYA İZİNLERİ VE GÜVENLİK
Linux çok kullanıcılı bir sistem olduğu için dosya erişim yetkileri kritiktir.

### 3.1. chmod (Change Mode)
Dosyaların okuma (r), yazma (w) ve çalıştırma (x) izinlerini değiştirmek için kullanılır.

Örnek: chmod +x script.sh komutu dosyayı çalıştırılabilir hale getirir.

## 4. SERVİS YÖNETİMİ (SYSTEMCTL)
Modern Linux dağıtımlarında arka plan hizmetlerini (servisleri) yönetmek için systemd birimi kullanılır.

systemctl start/stop: Bir servisi başlatır veya durdurur.

systemctl status: Servisin o anki çalışma durumunu raporlar.

systemctl enable: Servisin bilgisayar açıldığında otomatik olarak başlamasını sağlar.