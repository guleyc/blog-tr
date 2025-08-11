---
title: 'Plesk Panel’de Yandex Mail ile SMTP Hatası Nasıl Çözülür?'
date: '2020-06-01'
author: 'Çağatay Güley'
layout: post
permalink: /plesk-panelde-yandex-mail-ile-smtp-hatasi-nasil-cozulur/
en_url: /how-to-resolve-smtp-error-in-plesk-panel-with-yandex-mail/
redirect_from:
  - /how-to-resolve-smtp-error-in-plesk-panel-with-yandex-mail
  - /how-to-resolve-smtp-error-in-plesk-panel-with-yandex-mail/
  - /plesk-panelde-yandex-mail-ile-smtp-hatasi-nasil-cozulur
categories: [web]
tags: [smtp, hata, plesk, yandex mail]
image: yandex-mail.webp
---

Plesk Panel üzerinden web hosting yönetimi yapıyor ve e-posta servisiniz olarak Yandex Mail kullanıyorsanız, e-posta gönderirken SMTP (Simple Mail Transfer Protocol) hatalarıyla karşılaşabilirsiniz. Bu sorun genellikle “msmtprc” dosyasında yapılacak bazı ayarlamalarla çözülebilir. Bu rehberde, bu problemi nasıl çözebileceğinizi adım adım anlatacağım.

### **Adım 1: “msmtprc” Dosyasına Erişim**

1. Plesk Panel’in kurulu olduğu sunucuya SSH veya tercih ettiğiniz terminal uygulamasıyla giriş yapın.
2. “msmtprc” dosyasının bulunduğu dizine gidin. Genellikle bu dosya `/etc/msmtprc` yolunda bulunur.

### **Adım 2: “msmtprc” Dosyasını Düzenleme**

1. “msmtprc” dosyasını bir metin düzenleyici ile açın. Tercihinize göre `nano`, `edit` veya `vi` komutlarını kullanabilirsiniz:

```
nano /etc/msmtprc
```

```
vi /etc/msmtprc
```

```
edit /etc/msmtprc
```

2. “msmtprc” dosyası içinde çeşitli SMTP yapılandırma ayarlarını göreceksiniz. Bu ayarlar SMTP sunucu adresi, port, kimlik doğrulama bilgileri ve daha fazlasını içerebilir. Ayarların Yandex Mail SMTP sunucusunun gereksinimlerine uygun olduğundan emin olun.

```
#DİKKAT!
#
#BU DOSYAYI DEĞİŞTİRMEYİN, ÇÜNKÜ OTOMATİK OLARAK OLUŞTURULMUŞTUR,
#BU YÜZDEN YAPTIĞINIZ TÜM DEĞİŞİKLİKLER DOSYA YENİDEN OLUŞTURULDUĞUNDA KAYBOLACAKTIR.

# MSMTP yapılandırma dosyası. Söz dizimi için msmtp(1) bakınız.
# Bu dosya msmtpmng aracı tarafından oluşturulmuştur.

#
# Genel ayarlar bölümü
#
defaults

syslog LOG_MAIL
tls_starttls off
tls_certcheck off
tls on

# Otomatik envelope-from oluşturma.
# Dikkat: Bu, --from veya diğer yollarla açıkça ayarlanan envelope-from'u geçersiz kılar.
auto_from off
from mail@domain.com

# Envelope-from adresinin domain kısmını ayarlayın.
maildomain domain.com

# SMTP EHLO (veya LMTP LHLO) komutunun argümanını ayarlar.
domain server.domain.com

#
# Varsayılan hesap.
#
account default

host smtp.yandex.com.tr
port 465

auth on
user mail@domain.com
# Şifre aslında /etc/psa/private/msmtp-pwdeval.conf dosyasında saklanır
passwordeval /usr/lib64/plesk-9.0/msmtp-pwdeval
```

Bu rehberdeki adımları takip ederek, Plesk Panel ile Yandex Mail kullanırken karşılaştığınız SMTP hatalarını çözebilirsiniz. “msmtprc” dosyasındaki SMTP yapılandırma ayarlarını dikkatlice kontrol edin ve e-posta gönderiminin sorunsuz çalıştığından emin olmak için yapılandırmayı test edin.

“msmtprc” dosyasını güvenli bir şekilde saklamayı ve SMTP kimlik doğrulama bilgilerinizi gizli tutmayı unutmayın; böylece e-posta servislerinizin güvenliğini sağlamış olursunuz.