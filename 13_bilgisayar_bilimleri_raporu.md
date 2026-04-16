# 🛡️ Yazılım Güvenliği Temelleri Raporu

Bu rapor; kullanıcı doğrulama, yetkilendirme mimarileri ve en yaygın web saldırı vektörlerini teknik detaylarıyla ele almaktadır.

---

## 1. Authentication vs. Authorization (Kimlik Doğrulama vs. Yetkilendirme)

Bu iki terim sıkça birbirine karıştırılır, ancak kapıdaki koruma ile içerideki izinler kadar farklıdırlar.

* **Authentication (Kimlik Doğrulama):** "Sen kimsin?" sorusuna yanıt verir. Kullanıcının iddia ettiği kişi olduğunu kanıtlama sürecidir (Kullanıcı adı/şifre, parmak izi, MFA).
* **Authorization (Yetkilendirme):** "Neleri yapmaya yetkin var?" sorusuna yanıt verir. Kimliği doğrulanmış kullanıcının hangi kaynaklara erişebileceğini belirler (Örn: Bir kullanıcı kendi profilini düzenleyebilir ama başkasınınkini silemez).



---

## 2. Modern Güvenlik Protokolleri: JWT ve OAuth

### A. JWT (JSON Web Token)
Stateless (durumsuz) bir kimlik doğrulama yöntemidir. Sunucu, kullanıcı giriş yaptıktan sonra bilgileri içeren şifrelenmiş bir "token" (anahtar) oluşturur ve kullanıcıya verir. 
* **Mantık:** Sunucu her seferinde veritabanına bakmak yerine, gelen token'ın imzasını kontrol ederek kullanıcının geçerli olduğunu anlar. 
* **Yapısı:** `Header.Payload.Signature` şeklindedir.

### B. OAuth (Open Authorization)
Bir uygulamanın, kullanıcının şifresini bilmeden başka bir uygulamadaki (Google, GitHub, Facebook) bilgilerine erişmesine izin verme protokolüdür.
* **Örnek:** "Google ile giriş yap" butonuna bastığında, uygulama senin Google şifreni almaz; sadece Google'dan senin adına bir "erişim izni" (Access Token) alır.

---

## 3. Web Saldırıları: SQL Injection ve XSS

Geliştiricilerin yaptığı en büyük hatalar bu iki gedikten sızar:

###  SQL Injection (SQLI)
Saldırganın, uygulamanın giriş alanlarına zararlı SQL kodları enjekte ederek veritabanını ele geçirmesidir.
* **Hata:** Kullanıcıdan alınan verinin (`'OR 1=1 --`) doğrudan SQL sorgusuna eklenmesi.
* **Çözüm:** **Prepared Statements** veya **Parameterized Queries** kullanmak. Kullanıcı girdisini asla doğrudan koda gömme!



###  XSS (Cross-Site Scripting)
Saldırganın, web sitesine zararlı JavaScript kodları yüklemesidir. Bu kod, siteyi ziyaret eden masum kullanıcıların tarayıcısında çalışır.
* **Sonuç:** Kullanıcıların oturum çerezleri (cookies) çalınabilir veya sayfa manipüle edilebilir.
* **Çözüm:** Kullanıcıdan gelen tüm verileri **"Sanitize"** etmek (temizlemek) ve çıktıları encode etmek.

---

## 4. Elde Edilecek Kazanç (The Payoff)

1.  **Güven İnşası:** Kullanıcı verilerini sızdırmayan, profesyonel bir yazılım imajı çizersin.
2.  **Yasal Uyumluluk:** KVKK veya GDPR gibi veri koruma kanunlarına uygun yazılım geliştirirsin.
3.  **Maliyet Tasarrufu:** Sistem hacklendikten sonra yapılacak temizlik ve itibar kaybı, güvenlik önlemi almaktan çok daha maliyetlidir.

---
> **Altın Kural:** "Never trust user input" (Kullanıcıdan gelen girdiye asla güvenme). Her veriyi kirli kabul et ve öyle işle!