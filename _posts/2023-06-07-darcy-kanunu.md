---
title: 'Darcy Kanunu'
date: '2023-06-07'
author: 'Çağatay Güley'
layout: post
permalink: /darcy-kanunu/
en_url: /darcys-law/
redirect_from:
  - /darcys-law
  - /darcys-law/
  - /darcy-kanunu
categories: [muhendislik]
tags: [darcy, kanunu, muhendislik, matematik, fizik]
image: darcy.png
mathjax: true
---

Ondokuzuncu yüzyılın ortalarında, Fransız mühendis Henry Darcy, Dijon şehri için halka açık su çeşmelerinin tasarımından sorumluydu. Kum filtrelerinden su akışı üzerine yaptığı çalışmalar, hidrojeoloji, petrol mühendisliği ve inşaat mühendisliğinin temel taşlarından biri haline gelen ampirik bir ilişki kurmasına yol açtı. **Darcy Kanunu** olarak bilinen bu ilişki, bir akışkanın gözenekli bir ortamdan akışını tanımlar. Yeraltı suyunun nasıl hareket ettiğini, petrol ve gazın rezervuarlarda nasıl göç ettiğini ve suyun toprak ve kaya içinde nasıl sızdığını anlamak için nicel bir temel sağlar.

## Darcy Kanununun Matematiksel İfadesi

Darcy Kanunu, gözenekli bir ortamdan geçen bir akışkanın debisinin, hidrolik gradyan ve akışın geçtiği kesit alanı ile orantılı olduğunu belirtir. Denklem şu şekilde ifade edilir:

$$Q = -k \cdot A \cdot \frac{dh}{dL}$$

Bu kritik formülün her bir bileşenini inceleyelim:

* **$Q$ (Debi):** Belirli bir kesit alanından birim zamanda geçen akışkan hacmini temsil eder. SI birimi olarak metreküp/saniye ($m^3/s$) kullanılır.

* **$k$ (Hidrolik İletkenlik/Geçirgenlik Katsayısı):** Gözenekli ortamın bir özelliği olup, akışkanı iletme kabiliyetini ölçer. Hem ortamın özelliklerine (özgül geçirgenlik) hem de akışkanın özelliklerine (yoğunluk, viskozite) bağlıdır. Birçok durumda, özellikle su ile çalışırken, hidrolik iletkenlik olarak sadeleştirilir. Bu formülde, $k$'yı geçirgenlik katsayısı olarak ($m^2$) ele alacağız; akışkan özelliklerinden ayrıldığında bu birim kullanılır, hidrolik iletkenlik olarak ise ($m/s$) kullanılır. *Not: Buradaki örneklerde $m^2$ birimiyle geçirgenlik kullanılmıştır; klasik hidrojeolojide ise genellikle $m/s$ birimiyle hidrolik iletkenlik (K) kullanılır.*

* **$A$ (Kesit Alanı):** Akış yönüne dik olan ve akışkanın geçtiği alanı ifade eder. Birimi metrekare ($m^2$)'dir.

* **$\frac{dh}{dL}$ (Hidrolik Gradyan, $i$):** Akışın "itici gücüdür". Hidrolik yükteki değişimin ($dh$), akış yolundaki mesafeye ($dL$) oranıdır. Boyutsuz bir büyüklüktür (ör. $m/m$).

**Negatif işaret** önemlidir. Akışkanın, hidrolik yükün azaldığı yöne doğru aktığını gösterir. Yani, su her zaman yüksek enerjiden (yüksek yük) düşük enerjiye (düşük yük) doğru akar.

## Derinlemesine: Hidrolik Gradyan ($i = \frac{dh}{dL}$)

Hidrolik gradyan, akışı yönlendiren en kritik kavramdır. Bunu hesaplamak için hidrolik yükü anlamak gerekir.

**Hidrolik Yük ($h$)**, akışkanın birim ağırlığı başına toplam mekanik enerjisidir. Bir piezometrede (küçük çaplı gözlem kuyusu) akışkan sütununun yükseleceği yüksekliği ifade eder.

Hidrolik gradyan ($i$), iki nokta arasındaki hidrolik yük farkının, bu noktalar arasındaki doğrusal mesafeye oranıdır.

$$i = \frac{dh}{dL} = \frac{h_2 - h_1}{L}$$

Burada:
* **$h_1$** başlangıç noktasındaki hidrolik yük,
* **$h_2$** bitiş noktasındaki hidrolik yük,
* **$L$** iki ölçüm noktası arasındaki mesafedir.

Akışın 1'den 2'ye olması için $h_1 > h_2$ olmalıdır; bu durumda gradyan negatif olur, ancak Darcy Kanunu'ndaki negatif işaretle birlikte akış yönü doğru şekilde tanımlanır.

## Geçirgenlik ($k$): Ortamın Özelliği

Geçirgenlik, gözenekli bir malzemenin akışkanların geçişine ne kadar izin verdiğini ölçen içsel bir özelliktir. Çakıl gibi bir malzemenin geçirgenliği yüksektir, kil ise çok düşük geçirgenliğe sahiptir. Aşağıdaki tablo, çeşitli kaya türleri için tipik geçirgenlik katsayısı aralıklarını sunar.

| Kaya Türü           | Geçirgenlik Katsayısı (k) ($m^2$) | Tipik Hidrolik Gradyan ($dh/dL$) ($m/m$) |
| ------------------- | ---------------------------------- | ---------------------------------------- |
| Kum                 | $10^{-10}$ – $10^{-5}$             | 0.001 – 0.1                              |
| Kumtaşı             | $10^{-15}$ – $10^{-12}$            | 0.001 – 0.1                              |
| Çakıl               | $10^{-12}$ – $10^{-9}$             | 0.001 – 0.1                              |
| Çakıllı Kumtaşı     | $10^{-15}$ – $10^{-10}$            | 0.001 – 0.1                              |
| Kil                 | $10^{-18}$ – $10^{-15}$            | 0.0001 – 0.01                            |
| Siltli Kum          | $10^{-16}$ – $10^{-12}$            | 0.0001 – 0.01                            |
| Kireçtaşı           | $10^{-14}$ – $10^{-10}$            | 0.001 – 0.1                              |
| Kaya Tuzu           | $10^{-20}$ – $10^{-17}$            | 0.0001 – 0.01                            |
| Şeyl                | $10^{-20}$ – $10^{-17}$            | 0.0001 – 0.01                            |
| Granit              | $10^{-18}$ – $10^{-14}$            | 0.001 – 0.1                              |

## Darcy Kanununun Uygulamaları

Darcy Kanunu yalnızca akademik bir formül değildir; birçok gerçek dünya uygulamasının temelini oluşturur:

* **Hidrojeoloji:** Yeraltı suyu akış modellemesinin temelidir. Hidrojeologlar, su kaynaklarını yönetmek, atık sahalarından veya endüstriyel sızıntılardan kirleticilerin yayılımını tahmin etmek ve su kuyuları için uygun yerleri belirlemek için kullanır.
* **Petrol Mühendisliği:** Mühendisler, petrol, doğal gaz ve suyun rezervuarlardaki akışını modellemek için Darcy Kanunu'nu kullanır. Bu, rezervuar verimliliğini tahmin etmek ve verimli üretim stratejileri tasarlamak için gereklidir.
* **İnşaat & Geoteknik Mühendisliği:** Toprak barajlar ve setler üzerinden sızıntı analizinde kullanılır; bu, yapıların stabilitesini değerlendirmek için kritiktir. Temel ve istinat duvarları için drenaj sistemlerinin tasarımında da kullanılır.
* **Toprak Bilimi:** Topraktaki su hareketini tahmin etmeye yardımcı olur; bu, sulama ve drenaj sistemlerinin tasarımı için gereklidir.
* **Jeotermal Enerji:** Jeotermal rezervuarlarda sıcak su ve buharın hareketini anlamak için kullanılır; bu, sürdürülebilir enerji üretimi için kritiktir.

## Çözümlü Örnekler

Şimdi, verilen örneklerle kanunu uygulayalım.

### **Örnek 1: Kum Tabakasında Akış**

Kesit alanı 1.2 $m^2$ olan bir kum tabakasının geçirgenlik katsayısı 0.003 $m^2$, hidrolik gradyanı ise 0.015 $m/m$'dir. Sızıntı hızını (debi) hesaplayınız.

**Verilenler:**
* $A = 1.2 \, m^2$
* $k = 0.003 \, m^2$
* $\frac{dh}{dL} = 0.015 \, m/m$

**Hesaplama:**
$$Q = -k \cdot A \cdot \frac{dh}{dL}$$
$$Q = -(0.003 \, m^2) \cdot (1.2 \, m^2) \cdot (0.015 \, m/m)$$
$$Q = -0.000054 \, m^3/s$$

Debi **0.000054 $m^3/s$** (veya 54 mL/s) olarak bulunur. Negatif işaret, akışın azalan gradyan yönünde olduğunu gösterir.

### **Örnek 2: Çakıl Tabakasında Akış**

Bir çakıl tabakasında, su 0.8 $m^2$'lik bir kesit alanından sızmaktadır. Geçirgenlik katsayısı 0.0015 $m^2$, hidrolik gradyan ise 0.02 $m/m$'dir. Debiyi hesaplayınız.

**Verilenler:**
* $A = 0.8 \, m^2$
* $k = 0.0015 \, m^2$
* $\frac{dh}{dL} = 0.02 \, m/m$

**Hesaplama:**
$$Q = -k \cdot A \cdot \frac{dh}{dL}$$
$$Q = -(0.0015 \, m^2) \cdot (0.8 \, m^2) \cdot (0.02 \, m/m)$$
$$Q = -0.000024 \, m^3/s$$

Debi **0.000024 $m^3/s$** (veya 24 mL/s) olarak bulunur.

## Python ile Darcy Akışı Hesaplama

Tekrarlı hesaplamalar için basit bir Python scripti oluşturabiliriz. Bu script, kanunun parametrelerine göre debiyi hesaplayan bir fonksiyon tanımlar.

```python
def calculate_darcy_flow(permeability_k, area_A, head_1, head_2, length_L):
    """
    Darcy Kanunu ile akışkan debisini hesaplar.

    Args:
        permeability_k (float): Ortamın geçirgenlik katsayısı (m^2).
        area_A (float): Akışın geçtiği kesit alanı (m^2).
        head_1 (float): Akış yolunun başlangıcındaki hidrolik yük (m).
        head_2 (float): Akış yolunun sonundaki hidrolik yük (m).
        length_L (float): Akış yolu uzunluğu (m).

    Returns:
        float: Debi Q (m^3/s). Akış için pozitif değer döner.
    """
    if length_L <= 0:
        raise ValueError("Uzunluk (L) pozitif bir sayı olmalıdır.")

    # Hidrolik gradyan hesapla (i = dh/dL)
    hydraulic_gradient = (head_2 - head_1) / length_L

    # Debi hesapla (Q = -k * A * i)
    discharge_rate_Q = -permeability_k * area_A * hydraulic_gradient
    
    # Alternatif: Q = k * A * (h1 - h2) / L
    # discharge_rate_Q = permeability_k * area_A * (head_1 - head_2) / length_L

    return discharge_rate_Q

# --- Örnek Kullanım ---
# Örnek 1'i tekrar hesaplayalım.
# Gradyan doğrudan verilmiş (0.015), yani:
# (h2 - h1) / L = -0.015 (akış yüksekten düşüğe)
# h1 = 10m, L = 100m ise, h2 = h1 - 0.015*100 = 8.5m olur.

k_sand = 0.003  # m^2
A_sand = 1.2   # m^2
h1 = 10.0      # m (yukarıdaki yük)
h2 = 8.5       # m (aşağıdaki yük, gradyandan hesaplandı)
L = 100.0      # m (akış yolu uzunluğu)

# Debiyi hesapla
flow_rate = calculate_darcy_flow(
    permeability_k=k_sand,
    area_A=A_sand,
    head_1=h1,
    head_2=h2,
    length_L=L
)

print(f"Verilen Parametreler:")
print(f"  Geçirgenlik (k): {k_sand} m^2")
print(f"  Alan (A): {A_sand} m^2")
print(f"  Yukarıdaki Yük (h1): {h1} m")
print(f"  Aşağıdaki Yük (h2): {h2} m")
print(f"  Akış Yolu Uzunluğu (L): {L} m")
print("-" * 30)
print(f"Hesaplanan Hidrolik Gradyan (i): {(h2 - h1) / L:.4f} m/m")
print(f"Hesaplanan Debi (Q): {flow_rate:.6f} m^3/s")
print(f"Hesaplanan Debi (Q): {flow_rate * 1000 * 1000} mL/s")
```

## Sonuç

Darcy Kanunu, yeraltında akışkan hareketini nicel olarak tanımlamak için zarif ve güçlü bir araçtır. Sınırlamaları olsa da (doygun, homojen ortamda, laminer ve kararlı akış varsayımı), mühendislik ve yer bilimlerinde çok geniş bir problem yelpazesi için temel denklemdir. Büyük bir barajın güvenliğinden, yeraltı suyunun sürdürülebilir yönetimine kadar, Henry Darcy'nin 150 yıl önce ortaya koyduğu prensipler bugün her zamankinden daha günceldir.