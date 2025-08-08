---
title: 'Yeraltı Enjeksiyon Uygulamaları'
date: '2023-07-11'
author: 'Çağatay Güley'
layout: post
permalink: /yeralti-enjeksiyon-uygulamalari/
redirect_from:
  - /injection-works-in-underground-openings
  - /injection-works-in-underground-openings/
  - /yeralti-enjeksiyon-uygulamalari
categories: [maden]
tags: [enjeksiyon, uygulamalar, yeralti]
image: injection.jpg
mathjax: true
---

Zemin iyileştirme ve su kontrolü, tünellerin güvenliği, stabilitesi ve uzun vadeli işletilebilirliği için kritik öneme sahiptir. Bu makale, modern tünelcilik projelerinde uygulanan ileri enjeksiyon metodolojilerinin teknik bir özetini sunar. Pre-kazı zemin iyileştirmesi, kazı sonrası destek ve yapısal bütünlük için çimento esaslı enjeksiyonun prensipleri ve uygulamaları; Şemsiye Kemer (Umbrella Arch) yöntemi, kaya bulonlama ve kontak enjeksiyonu gibi temel kavramlar dahil olmak üzere ele alınacaktır. Ayrıca, zorlu su yalıtımı senaryolarında kritik rol oynayan poliüretan (PU) ve akrilik reçineler gibi özel kimyasal enjeksiyon sistemleri de detaylandırılacaktır. Tartışmada karışım tasarımı, kalite kontrol parametreleri ve her tekniğin temel mekanikleri de yer almaktadır.

## 1.0 Çimento Esaslı Enjeksiyon: Prensipler ve Uygulamalar

Çimento bazlı enjeksiyon, tünelcilikte çevreleyen zemin kütlesinin mekanik ve hidrolojik özelliklerini değiştirmek için kullanılan temel bir tekniktir. Uygulama, genel olarak pre-kazı, eşzamanlı (kazı ile birlikte) ve post-kazı fazlarına ayrılabilir.

### 1.1 Pre-Kazı Zemin İyileştirme

Pre-kazı enjeksiyonun temel amacı, zeminin ayakta kalma süresini artırmak, geçirgenliği azaltmak ve TBM (Tünel Açma Makinesi) veya geleneksel kazı ekipmanı ilerlemeden önce stabil bir kazı yüzeyi sağlamaktır.

* **a. Şemsiye Kemer Yöntemi (Forepoling):** Bu teknik, tünel hizasının tacı üzerinde ve çevresinde koruyucu, yük taşıyan bir kemer oluşturur. Bir dizi yataya yakın delik açılır ve bu deliklere delikli çelik borular (lanslar) yerleştirilir. Grout (enjeksiyon harcı), bu borular aracılığıyla çevredeki zemin/kaya kütlesine enjekte edilir. Böylece zayıf zemin koşullarında çökme riskini azaltan kompozit, güçlendirilmiş bir kemer oluşur. Genellikle **Kendinden Delmeli Ankrajlar (SDA)** ile uygulanır; bu sistemde delme, ankraj yerleştirme ve enjeksiyon işlemleri tek adımda gerçekleştirilir.

* **b. Yüzey Stabilizasyonu (Yüz Bulonlama):** Özellikle granüler veya çatlaklı zeminlerde kazı yüzeyinin stabilitesini sağlamak veya çökmesini önlemek için, bulonlar doğrudan tünel yüzeyine yerleştirilir ve çimento esaslı grout ile sabitlenir. Bu teknik, "ayna iyileştirmesi" olarak da adlandırılır ve kazı önünde zeminin kohezyonunu ve kayma mukavemetini artırarak kontrollü ilerleme sağlar. İşlem, yüzeye delik açılması, ardından çimento esaslı grout enjeksiyonu ve çoğunlukla cam elyafı veya çelik dübellerin yerleştirilmesini içerir.

* **c. Konsolidasyon Enjeksiyonu:** Daha geniş bir terim olarak, belirli bir zemin hacmine grout enjekte edilerek sıkışabilirlik ve geçirgenlik azaltılır. Amaç, tünelin güvenle kazılabileceği monolitik, stabilize bir zemin bloğu oluşturmaktır. Konsolidasyonun etkinliği, grout reolojisi ve enjeksiyon basıncı ile kontrol edilir; aşırı basınç zeminde kabarmaya yol açabilir. Temel kontrol parametresi **Enjeksiyon Yoğunluk Numarası (GIN)**’dır; zemine aktarılan enerjinin gerçek zamanlı ölçüsüdür:

    $$GIN = P \times V$$

    Burada:
    * $P$ = Son enjeksiyon basıncı (bar)
    * $V$ = Delik başına emilen grout hacmi (L/m)

### 1.2 Post-Kazı Destek Sistemleri

* **Kaya Bulonlama (Ankrajlama):** Kazı sonrası, tünel çevresini sistematik olarak güçlendirmek ve kaya kütlesi deformasyonlarını kontrol etmek için kaya bulonları yerleştirilir. Süreç:
    1.  **Delme:** Tasarlanan derinlik ve desende delikler açılır.
    2.  **Ankraj Yerleştirme:** Çelik veya cam elyafı çubuk yerleştirilir.
    3.  **Enjeksiyon:** Delik ile ankraj arasındaki boşluk çimento veya reçine grout ile doldurulur.
    4.  **Ön Germe:** Aktif destek için bulon somununa tork uygulanır ve bulonda çekme kuvveti oluşturulur. Bu, tünel çevresindeki kaya kütlesinde basınç bölgesi yaratır ve stabiliteyi artırır. Uygulanan tork ile oluşan çekme kuvveti arasındaki ilişki yaklaşık olarak:

        $$T = K \cdot D \cdot P$$

        Burada:
        * $T$ = Uygulanan tork (Nm)
        * $K$ = Somun katsayısı (boyutsuz, çelik için genellikle ~0.2)
        * $D$ = Nominal bulon çapı (m)
        * $P$ = Oluşan çekme kuvveti (N)

* **Kontak ve Anülüs Enjeksiyonu:** Birincil (shotcrete) veya nihai (segmental) kaplama yerleştirildikten sonra, kaplama ile kazılmış kaya profili arasında boşluklar kalabilir. Bu boşluklar kontak enjeksiyonu ile doldurulur. Amaç:
    * Yükün zeminden kaplamaya düzgün aktarılmasını sağlamak,
    * Su yolları ve sızıntı oluşumunu önlemek,
    * Kaplamanın boşluklara doğru deformasyonunu engellemektir.

## 2.0 Su Kontrolü için Grout Karışım Tasarımı

Yüksek yeraltı suyu girişinin olduğu ortamlarda, standart çimento-su karışımları etkisiz olabilir; grout, priz almadan önce sulanabilir veya yıkanabilir. Bu gibi durumlarda, kimyasal katkılar içeren özel karışım tasarımları gereklidir.

Aşağıdaki tablo, sodyum silikat hızlandırıcı kullanılan, suya doygun zeminler için tasarlanmış 1 m³’lük gelişmiş bir grout karışım örneği sunar.

**Tablo 1: Su Kontrolü için Örnek Grout Karışım Tasarımı**

| Bileşen | Yoğunluk (kg/m³) | 1 m³ için Kütle (kg) | 1 m³ için Hacim (L) | Fonksiyon |
| :--- | :--- | :--- | :--- | :--- |
| Su | 1000 | 780 | 780 | Çözücü / Reaktant |
| Çimento (CEM I 42.5R) | 3090 | 295 | 95.5 | Bağlayıcı |
| Bentonit | 1700 | 40 | 23.5 | Kanama önleyici / Tiksotropik ajan |
| Yavaşlatıcı (örn. EUCON 130) | 1095 | 5 | 4.6 | Priz süresini uzatır |
| Sodyum Silikat (örn. CreteShot NS 303) | 1375 | 132 | 96 | Hızlandırıcı (ani priz için) |
| **TOPLAM** | **~1252** | **1252** | **1000** | **-** |

**Temel Karışım Tasarım Parametreleri:**

* **Su/Çimento Oranı ($w/c$):** Dayanım ve geçirgenliğin ana belirleyicisidir. Bu karışımda kütle bazında $w/c$ oranı:
    $$\frac{w}{c} = \frac{\text{Su Kütlesi}}{\text{Çimento Kütlesi}} = \frac{780 \text{ kg}}{295 \text{ kg}} \approx 2.64$$
    *Not: Bu çok yüksek $w/c$ oranı, grout’un yüksek dayanım yerine boşluk doldurma ve su durdurma amacıyla tasarlandığını gösterir. Yüksek bentonit içeriği, stabil, hacimli ve düşük dayanımlı bir bulamaç oluşturur.*
* **Katkıların Rolleri:**
    * **Bentonit:** Suda şişen bir kil minerali olup grout kanamasını azaltır ve tiksotropik özellik kazandırır (pompalarken akışkan, durunca jel).
    * **Yavaşlatıcı:** Çimento hidratasyonunu yavaşlatır, grout’un uzun mesafelere pompalanabilmesi için yeterli çalışma süresi sağlar.
    * **Sodyum Silikat:** Ayrı veya uygulama noktasında enjekte edilen hızlandırıcıdır. Çimento esaslı grout ile neredeyse anında reaksiyona girerek ani priz (flash setting) sağlar. Yüksek basınçlı su girişlerinin kapatılmasında vazgeçilmezdir.

## 3.0 Su Yalıtımı için Kimyasal Enjeksiyon

Çimento partiküllerinin giremeyeceği ince çatlaklar ve sürekli su sızıntılarında, düşük viskoziteli kimyasal reçineler kullanılır. Bunlar genellikle iki bileşenli pompa sistemiyle, delinmiş deliklere yerleştirilen enjeksiyon packer’ları aracılığıyla uygulanır.

### 3.1 Poliüretan (PU) Enjeksiyonu

Poliüretan reçineler, genellikle izosiyanat ve poliol olmak üzere iki bileşenli sistemlerdir ve reaksiyon sonucu esnek veya rijit köpük/jel oluştururlar.

* **Mekanizma:** 20 kg poliüretan ile 2 kg katalizör karıştırılması, **hidrofobik** PU sistemine işaret eder. Bu reçine tipi esas olarak katalizörüyle reaksiyona girer, ancak suyla temas ettiğinde hacmi önemli ölçüde artar ve yoğun, kapalı hücreli bir köpük oluşturur. Bu köpük, su girişine karşı dayanıklı ve esnek bir bariyer görevi görür.
* **Uygulama:** Su taşıyan çatlak veya derzlerin arkasına ulaşmak için yaklaşık 45° açıyla delikler açılır. Packer’lar yerleştirilir ve PU reçinesi, dolum tamamlanana veya sızıntı noktasında reçine görülene kadar enjekte edilir.

### 3.2 Akrilik Enjeksiyon

Akrilik reçineler, özellikle ince çatlakların kapatılması ve zemin veya yapı içinde su geçirmez “perde” oluşturulması için kullanılır.

* **Mekanizma:** Akrilikler, polimerleşerek yüksek esnekliğe sahip, bütünleşik bir jel oluşturan çok bileşenli sistemlerdir. En büyük avantajı, genellikle suya yakın çok düşük viskoziteleridir ($\eta \approx 1-5 \text{ mPa} \cdot \text{s}$). Bu sayede, diğer grout’ların giremeyeceği en ince çatlaklara dahi nüfuz edebilirler.
* **Uygulama:** Açıklamada belirtildiği gibi—bir tankta akrilik (25 kg) ile katalizör (1.25 kg), diğer tankta su (25 kg) ile başlatıcı tuz (0.625 kg) karıştırılır—standart uygulamadır.
    * **İki Bileşenli Pompa:** İki karışım enjeksiyon noktasına kadar ayrı tutulur. Packer öncesi “Y” bağlantısında birleşir.
    * **Kontrollü Jel Süresi:** Tüm bileşenler karıştığında hızlı polimerizasyon başlar. Jel süresi (karışımdan katılaşmaya kadar geçen süre), katalizör ve başlatıcı miktarı ayarlanarak birkaç saniyeden birkaç dakikaya kadar hassas şekilde kontrol edilebilir. Bu kontrol, reçinenin hedef bölgeye ulaşmadan önce priz almasını önlemek için kritiktir.

## Sonuç

Tünellerin başarılı inşası ve uzun vadeli bakımı, sistematik ve uyarlanabilir bir zemin mühendisliği ve su yalıtımı yaklaşımına bağlıdır. Çimento esaslı enjeksiyon, zemin stabilizasyonu ve yapısal destek için temel çözümken; poliüretan ve akrilik reçinelerle yapılan kimyasal enjeksiyonlar, karmaşık su kontrolü sorunlarında vazgeçilmez, yüksek performanslı çözümler sunar. Uygun teknik, malzeme ve karışım tasarımının seçimi; saha özelindeki jeolojik ve hidrojeolojik koşulların iyi anlaşılmasıyla mümkündür ve güvenli, dayanıklı ve uzun ömürlü bir yeraltı altyapısı için temeldir.