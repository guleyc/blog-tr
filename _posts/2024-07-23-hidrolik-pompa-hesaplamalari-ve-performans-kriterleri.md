---
title: 'Hidrolik Pompa Hesaplamaları ve Performans Kriterleri'
date: '2024-07-23'
author: 'Çağatay Güley'
layout: post
permalink: /hidrolik-pompa-hesaplamalari-ve-performans-kriterleri/
en_url: /comprehensive-guide-to-hydraulic-pump-calculations-and-performance-metrics/
redirect_from:
  - /hidrolik-pompa-hesaplamalari-ve-performans-kriterleri
  - /comprehensive-guide-to-hydraulic-pump-calculations-and-performance-metrics
  - /comprehensive-guide-to-hydraulic-pump-calculations-and-performance-metrics/
mathjax: true
tags: [enerji, hidrolik, pompalar, makineler, guc, verimlilik, rehber]
image: hydraulic.jpg
---

Şimdi, her biri kendine özgü tasarıma, güçlü yönlere ve ideal kullanım alanlarına sahip en yaygın pompa tiplerini inceleyelim.

#### Dişli Pompalar: Sağlam İşçi

![Dişli Pompa Animasyonu](https://guley.com.tr/upload/gear_pumps.gif)

**Özet:** Basit, sağlam ve ekonomik olan dişli pompalar, güvenilirliğin ön planda olduğu birçok orta basınçlı uygulamanın vazgeçilmezidir.

**Nasıl Çalışır?** İki dişlinin sıkı bir gövde içinde birbirine geçerek döndüğünü hayal edin. Döndükçe giriş tarafında bir vakum oluşur ve sıvı içeri çekilir. Sıvı, dişliler ile gövde arasındaki boşluklarda hapsolur, çıkışa taşınır ve dişliler tekrar birleşirken dışarı itilir.

**Temel Özellikler & Kullanım Alanları:**
* **Basınç Aralığı:** Genellikle 250 bar'a kadar.
* **Deplasman:** Sabit. Debi yalnızca pompa devri (RPM) değiştirilerek ayarlanabilir.
* **Verimlilik:** Hacimsel verimlilik genellikle %85-95 arasındadır. Pistonlu pompalara göre daha düşüktür.
* **Artıları:** Ekonomik, son derece güvenilir ve hidrolik yağ kirliliğine çok toleranslıdır. Ani arızalar nadirdir; genellikle yavaşça aşınırlar.
* **Eksileri:** Gürültülü olabilir, daha düşük verimle çalışır ve sabit deplasmanlıdır.
* **Yaygın Kullanım Alanları:** Odun yarıcılar, hidrolik güç üniteleri, yağlama sistemleri ve ağır ekipmanlarda yardımcı fonksiyonlar.

**Formül (Deplasman Hacmi):**
Harici dişli bir pompanın deplasmanı, dişlilerinin geometrisine bağlıdır.

$$V_d \approx \frac{\pi}{4} \times (D_o^2 - D_i^2) \times W$$

Burada:
* $V_d$ = Deplasman Hacmi (ör. cm³/devir)
* $D_o$ = Dişlilerin dış çapı (cm)
* $D_i$ = Dişlilerin iç çapı (kökte, cm)
* $W$ = Dişli genişliği (cm)

#### Kanatlı Pompalar: Sessiz Operatör

![Kanatlı Pompa Animasyonu](https://guley.com.tr/upload/vane_pumps.gif)

**Özet:** Düşük ses seviyesi ve yüksek verimlilikleriyle bilinen kanatlı pompalar, orta basınçlı endüstriyel ve mobil uygulamalarda popülerdir.

**Nasıl Çalışır?** Yivli bir rotor, kam halkası içinde döner. Dikdörtgen kanatlar bu yivlerde ileri geri hareket eder. Rotor ile halka arasındaki eksantriklik, kanatların genişleyen ve daralan odacıklar oluşturmasını sağlar. Odacıklar genişlerken sıvı içeri çekilir, daralırken dışarı itilir.

**Temel Özellikler & Kullanım Alanları:**
* **Basınç Aralığı:** Genellikle 200 bar'a kadar.
* **Deplasman:** Sabit veya değişken olabilir. Değişken deplasmanlı modeller, enerji tasarrufu için debiyi ayarlayabilir.
* **Verimlilik:** Dişli pompalardan daha yüksek hacimsel verimlilik (%85-92 arası).
* **Artıları:** Çok düşük ses seviyesi, düşük basınç dalgalanması (düzgün akış) ve yüksek verimlilik.
* **Eksileri:** Pistonlu pompalara göre kirliliğe ve yüksek basınca daha az toleranslıdır.
* **Yaygın Kullanım Alanları:** Döküm ve enjeksiyon makineleri, hidrolik direksiyon sistemleri ve orta ölçekli hidrolik presler.

**Formül (Deplasman Hacmi):**

$$V_d = \frac{\pi}{2} \times (D_c + D_r) \times e \times W$$

Burada:
* $V_d$ = Deplasman Hacmi (cm³/devir)
* $D_c$ = Kam halkası çapı (cm)
* $D_r$ = Rotor çapı (cm)
* $e$ = Rotor ile halka arasındaki eksantriklik (cm)
* $W$ = Kanat genişliği (cm)

#### Pistonlu Pompalar: Yüksek Basınç Şampiyonları

Pistonlu pompalar, hidrolik dünyasının ağır toplarıdır; en yüksek basınçları üretebilir ve en iyi genel verimliliği sunar. Zorlu uygulamalar için en iyi tercihtir. En yaygın tasarımlar bükük eksenli ve doğrusal (swashplate) tiplerdir.

##### Bükük Eksenli Pistonlu Pompalar

![Bükük Eksenli Pistonlu Pompa Animasyonu](https://guley.com.tr/upload/bent_axis_pumps.gif)

**Özet:** Mevcut en verimli hidrolik pompa tasarımıdır; çok yüksek basınç ve devirlerde çalışabilir.

**Nasıl Çalışır?** Silindir bloğu, tahrik mili tarafından döndürülür ancak ona bir açıyla yerleştirilmiştir ("bükük eksen"). Bu açı, pistonların silindir deliklerinde ileri geri hareket etmesini sağlar ve pompalama işlemini oluşturur. Daha büyük açı, daha uzun piston stroku ve daha fazla deplasman demektir.

**Temel Özellikler & Kullanım Alanları:**
* **Basınç Aralığı:** Sürekli çalışmada genellikle 400 bar'ı aşar.
* **Deplasman:** Sabit veya değişken olabilir.
* **Verimlilik:** Tüm pompa tipleri arasında en yükseği; toplam verimlilik çoğunlukla %95'i aşar.
* **Artıları:** Son derece yüksek verimlilik, yüksek basınç ve devir, çok dayanıklı.
* **Eksileri:** Yüksek maliyet, büyük fiziksel boyut ve karmaşık tasarım.
* **Yaygın Kullanım Alanları:** Ağır inşaat ve madencilik ekipmanları (ekskavatör, damperli kamyon), ormancılık makineleri ve endüstriyel üretim.

##### Doğrusal Eksenli (Swashplate) Pistonlu Pompalar
![Doğrusal Eksenli Pistonlu Pompa Animasyonu](https://guley.com.tr/upload/radial_piston_pumps.gif)

**Özet:** Bükük eksenli pompaya göre daha kompakt ve yaygın bir tasarımdır; yüksek basınçlı sistemler için mükemmel performans ve çok yönlülük sunar.

**Nasıl Çalışır?** Pistonlar ve silindir bloğu, tahrik miliyle aynı hizada bulunur. Pistonlar, açılı bir swashplate'e bağlıdır. Swashplate döndükçe pistonları silindir bloğunda ileri geri hareket ettirir ve pompalama işlemini oluşturur. Swashplate'in açısı debiyi belirler.

**Temel Özellikler & Kullanım Alanları:**
* **Basınç Aralığı:** Bükük eksenliyle benzer, genellikle 350-420 bar.
* **Deplasman:** Neredeyse her zaman değişken; gelişmiş kontrol seçenekleri (basınç kompanzasyonu, yük algılama) bulunur.
* **Verimlilik:** Çok yüksek, bükük eksenli pompalarla neredeyse eşit.
* **Artıları:** Bükük eksenli tasarımlara göre daha kompakt ve daha ucuz, enerji tasarrufu için çok yönlü kontrol.
* **Eksileri:** Bükük eksenli pompalara göre biraz daha az verimli ve sıvı kirliliğine daha hassas.
* **Yaygın Kullanım Alanları:** En yaygın değişken pompa tipidir; mobil vinçlerden tarım makinelerine, endüstriyel güç ünitelerine kadar her yerde bulunur.

**Formül (Pistonlu Pompalarda Deplasman):**
Deplasman, tüm pistonların bir tam devirde süpürdüğü hacimdir.

$$V_d = A_p \times s \times n$$

Burada:
* $V_d$ = Deplasman Hacmi (cm³/devir)
* $A_p$ = Bir pistonun alanı (cm²)
* $s$ = Piston stroku (cm)
* $n$ = Piston sayısı

---

### Özet: Doğru Pompayı Seçmek

Doğru hidrolik pompayı seçmek, performans, verimlilik ve maliyet arasında bir denge kurmaktır. Kararınızı kolaylaştıracak hızlı bir karşılaştırma:

| Pompa Tipi | Basınç Aralığı | Verimlilik | Maliyet | Temel Avantaj |
| :--- | :--- | :--- | :--- | :--- |
| **Dişli Pompa** | Düşük-Orta | İyi | Düşük | Basit & Sağlam |
| **Kanatlı Pompa** | Orta | Çok İyi | Orta | Düşük Ses |
| **Pistonlu Pompa**| Çok Yüksek | Mükemmel | Yüksek | Yüksek Basınç & Verimlilik |

Sonuç olarak, hidrolik sisteminizin temel gereksinimlerini – ihtiyaç duyduğu hız (debi) ve kuvvet (basınç) – anlamak, hidrolik gücün inanılmaz potansiyelinden yararlanmanın ilk adımıdır.