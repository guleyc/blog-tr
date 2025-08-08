---
title: 'Rclone ile Google Drive Yedekleme Adımları'
date: '2024-08-07'
author: 'Cagatay Guley'
layout: post
permalink: /rclone-ile-google-drive-yedekleme-adimlari/
redirect_from:
  - /rclone-ile-google-drive-yedekleme-adimlari
categories: [web]
tags: [rclone, google, drive, yedekleme, cloudpanel, web, linux, windows, guvenlik]
image: backup.jpg
---

Bu rehberde, Windows işletim sistemi üzerinde Rclone kullanarak verilerinizi Google Drive'a nasıl yedekleyeceğinizi adım adım anlatıyoruz. Hem yeni başlayanlar hem de deneyimli kullanıcılar için uygundur.

### Adım 1: Rclone'u İndirin ve Çıkartın
Öncelikle [bu bağlantıdan](https://rclone.org/downloads/) Rclone'u indirin. İndirilen dosyayı bilgisayarınızda belirli bir klasöre çıkartın.

### Adım 2: Komut İstemini Yönetici Olarak Çalıştırın
Başlat menüsünde CMD aratın ve yönetici olarak çalıştırın.

### Adım 3: Rclone Dosya Konumuna Geçin
Rclone'u çıkarttığınız klasöre geçmek için dizini değiştirin:

```
cd #rclone_dosya_konumu
```

### Adım 4: Rclone Konfigürasyon Dosyası Konumunu Not Edin
Rclone konfigürasyon dosyasının konumunu not alın:

```
C:\Users\user\AppData\Roaming\rclone\rclone.conf
```

### Adım 5: Yeni Bir Remote (Uzak Bağlantı) Oluşturun
“No remotes found, make a new one?” sorusu geldiğinde `n` yazın:

```
No remotes found, make a new one? - n
```

### Adım 6: Yeni Remote İçin Bir İsim Girin
Yeni remote için `drive` ismini yazın:

```
Enter name for new remote: drive
```

### Adım 7: Google Drive'ı Seçin
Google Drive için `drive` yazın veya numarasını girin:

```
Storage> drive
```

### Adım 8: Client ID ve Client Secret Alanlarını Boş Bırakın
Bu alanları boş bırakın:

```
client_id>
client_secret>
```

### Adım 9: Scope Belirtin
Scope için `drive` veya `1` yazın:

```
scope> 1
```

### Adım 10: Gelişmiş Ayarları Atlayın
Gelişmiş ayarları düzenlemek isteyip istemediğiniz sorulduğunda `n` yazın:

```
y/n> n
```

### Adım 11: Kimlik Doğrulama İçin Web Tarayıcı Kullanın
Kimlik doğrulama için web tarayıcı kullanmak istiyor musunuz sorusuna `y` yazın:

```
y/n> y
```

### Adım 12: Tarayıcı Üzerinden Kimlik Doğrulama
Tarayıcınız otomatik olarak aşağıdaki gibi bir URL'ye yönlenecek:

```
http://127.0.0.1:53682/auth?state=AbiF4_ck-Q-1x4ZBbQXag
```

Google Drive hesabınızla giriş yapın ve rclone'a izin verin.

### Adım 13: Rclone Konfigürasyon Dosyasını Bulun
Rclone konfigürasyon dosyasının konumuna gidin:

```
C:\Users\user\AppData\Roaming\rclone\rclone.conf
```

### Adım 14: Konfigürasyon Dosyasını Sunucuya Yükleyin
Rclone konfigürasyon dosyasını kopyalayıp sFTP ile sunucunuza yükleyin:

```
/root/.config/rclone
```

**Not:** sFTP istemcinizde ve bilgisayarınızda gizli dosyaları görünür yapmayı unutmayın.

### Sonuç

Bu adımları takip ederek Rclone'u Google Drive ile entegre edebilir ve yedekleme işlemlerinizi güvenli şekilde gerçekleştirebilirsiniz. Daha fazla bilgi ve destek için [Rclone dokümantasyonu](https://rclone.org/install/) veya [Cloudpanel dokümantasyonu](https://www.cloudpanel.io/docs/v2/admin-area/backups/) sayfalarını ziyaret edebilirsiniz.
