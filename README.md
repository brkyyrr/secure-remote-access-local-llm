# 🌍 Yerel LLM İstasyonuna Güvenli Uzaktan Erişim Rehberi

Bu rehber; evinizdeki güçlü GPU üzerinde çalışan yapay zeka asistanınıza, herhangi bir modem ayarı (Port Forwarding) yapmadan ve güvenlikten ödün vermeden dünyanın her yerinden nasıl erişebileceğinizi anlatır.

## 🛡️ Neden Tailscale (Mesh VPN) Kullanıyoruz?
- **Güvenlik:** İnternete açık port bırakmazsınız. Sadece sizin izin verdiğiniz cihazlar (telefon, laptop vb.) erişebilir.
- **Kolaylık:** Statik IP veya karmaşık modem/firewall ayarları gerektirmez.
- **Şifreleme:** Verileriniz cihazlar arasında uçtan uca şifreli bir tünel içinden geçer.

---

## 🔍 Önemli: Docker Port Kontrolü
Uzaktan erişimin çalışması için Docker üzerindeki port yapılandırmasının doğru olması gerekir. Bunu şu şekilde kontrol edebilirsiniz:

1.  **Docker Desktop** uygulamasını açın.
2.  Sol menüden **"Containers"** sekmesine tıklayın.
3.  `open-webui` konteynerini bulun ve **"Port(s)"** sütununa bakın.
4.  Burada **`3000:8080`** veya **`0.0.0.0:3000->8080`** yazıyorsa sisteminiz dış bağlantılara hazırdır.

---

## 🛠️ Adım Adım Kurulum

### 1. Tailscale Kurulumu
1.  **Hesap Oluşturun:** [Tailscale.com](https://tailscale.com) üzerinden ücretsiz bir hesap açın.
2.  **Ana Bilgisayara Kurun (Host):** LLM'in ve Docker'ın kurulu olduğu ana bilgisayara Tailscale uygulamasını indirin ve giriş yapın.
3.  **İstemci Cihaza Kurun (Client):** Erişmek istediğiniz telefona, tablete veya dışarıda kullandığınız laptopa Tailscale uygulamasını kurun ve **aynı hesapla** giriş yapın.

### 2. Uzaktan Erişim ve Bağlantı
1.  Dışarıdayken (farklı bir Wi-Fi veya hücresel veri üzerindeyken) Tailscale uygulamasını açın ve VPN bağlantısını aktif edin.
2.  Tailscale panelinde ana bilgisayarınızın yanında görünen **IP adresini** (Örn: `100.x.x.x`) not edin.
3.  Tarayıcınızın adres çubuğuna şunu yazın:
    `http://[Kopyaladığınız-IP-Adresi]:3000`

---

## ⚠️ Kritik Güvenlik Uyarıları

> [!IMPORTANT]
> **Asla Port Forwarding Yapmayın:** Modeminizi 3000 portu üzerinden internete açmak, sistemi tüm dünyaya savunmasız bırakmaktır. Tailscale bu riski tamamen ortadan kaldırır.

- **Güçlü Şifreleme:** Open WebUI panelinizde mutlaka güçlü bir şifre belirleyin.
- **Admin Kontrolü:** Settings > General kısmından yeni kullanıcı kayıtlarını (**Allow New Signups**) kapatarak sadece kendi hesabınızın erişmesini sağlayın.

---
