---
title: 'Zaman Serisi Analizi'
date: '2022-05-03'
author: 'Çağatay Güley'
layout: post
permalink: /zaman-serisi-analizi/
en_url: /time-series-analysis/
redirect_from:
  - /time-series-analysis
  - /time-series-analysis/
  - /zaman-serisi-analizi
tags: [zaman, seri, analiz, tahmin, regresyon]
mathjax: true
image: time-series.jpg 
---

Zaman serisi analizi, geçmiş verilere dayanarak gelecekteki değerleri tahmin etmek için kullanılan istatistiksel bir yöntemdir. Amaç, hisse senedi fiyatları, hava durumu desenleri veya ekonomik göstergeler gibi zaman içinde değişen bir değişkenin değerlerini, geçmiş gözlemleri kullanarak öngörmektir. Bir zaman serisi tahmin modeli oluşturmak için ilk adım, veri setini incelemektir. Veri seti, değişkenin zaman içinde düzenli aralıklarla yapılan ölçümlerinden oluşur; örneğin bir hissenin günlük kapanış fiyatları veya aylık ortalama sıcaklıklar gibi. İlk adım, zaman serisi verisinin istatistiksel özelliklerini analiz etmektir; bunlar arasında trend, mevsimsellik ve periyodik dalgalanmalar yer alabilir. Trend, veride gözlemlenen uzun vadeli artış veya azalış eğilimidir. Mevsimsellik, belirli aralıklarda düzenli olarak tekrar eden desenleri yakalar; örneğin tatil sezonunda perakende satışlarda yaşanan artış gibi. Periyodik dalgalanmalar ise veride gözlemlenen düzenli tekrar eden desenleri temsil eder.

Zaman serisi verisi, belirli veya düzenli zaman aralıklarında kaydedilen veri noktaları veya gözlemler dizisini ifade eder. Bu veriler saatlik, günlük, haftalık, aylık, üç aylık veya yıllık gibi farklı frekanslarda toplanabilir.

Zaman Serisi Tahmini, geçmiş sonuçlara dayalı istatistiksel bir model kullanarak bir zaman serisinin gelecekteki değerlerini tahmin etme sürecidir. Bu karmaşık süreç, geçmiş veri noktalarını kullanarak zaman serisindeki gelecekteki eğilimler hakkında bilinçli öngörülerde bulunmayı içerir.

Tahmine yönelik zaman serisi analizinde, bilinen geçmiş sonuçlara dayalı temel modeller kullanılarak gelecekteki sonuçlar öngörülür. Diyelim ki zaman (t)'de Y'yi tahmin etmek istiyoruz; zaman serisi tahmininin tanımı gereği, bu Y değeri Y(t-1), Y(t-2) vb. önceki değerlere bağlıdır. Dolayısıyla temel model denklemi şu şekilde formüle edilir: Y(t) = Y(t-1) + Y(t-2) / 2.

Yukarıdaki denklemde, Y değeri kendisinden önceki iki değerin ortalamasına bağlıdır. Sonuç olarak, bu yaklaşım tek değişkenli (univariate) zaman serisi tahmini olarak adlandırılabilir. Bu bağlamda, gelecekteki değeri tahmin etmek için yalnızca iki önceki değeri dikkate alırız. Buradaki pencere boyutu (window size) 2'dir. Pencere boyutu bir hiperparametre olarak düşünülebilir ve modele farklı değer aralıkları sağlanmalıdır. En doğru tahmini veren değer, pencere boyutu olarak seçilir.

Bu temel model tek değişkenli zaman serisi tahmininin özünü gösterse de, gerçek dünya uygulamaları genellikle daha karmaşık ve sofistike modeller gerektirir. Bu modeller, ek özellikler içerebilir, dışsal faktörleri entegre edebilir veya tahmin yeteneğini artırmak için daha geniş bir geçmiş veri aralığı kullanabilir. Ayrıca, en uygun pencere boyutunun seçimi basit bir iş değildir ve verideki temel desenleri en iyi yakalayan yapılandırmayı belirlemek için ampirik denemeler gerekebilir.

#### Bilinmesi Gereken Temel Kavramlar

**Trend** — Bir serinin zaman içinde doğrusal olarak artan veya azalan davranışıdır. Trend yukarı, aşağı veya yatay (düz) olabilir.

**Mevsimsellik (Seasonality)** — Zaman serisinde belirli aralıklarla tekrar eden bir desen varsa, buna mevsimsellik denir. Mevsimsel desenler birçok zaman serisinde gözlemlenebilir. Örneğin, ısıtma maliyetleri yazın azalırken kışın artabilir. Şirketler, stok yönetimi, iş gücü planlaması ve diğer birçok kritik konuda mevsimselliği anlamak zorundadır.

**ETS Ayrıştırması (ETS Decomposition)** — Zaman serisinin çeşitli bileşenlerini ayrıştırmak için kullanılır.

**Durağanlık (Stationarity)** — Bir serinin ortalama değerinin zaman boyunca sabit kalmasıdır. Geçmiş etkiler birikerek değerler sonsuza kadar artıyorsa, durağanlık sağlanmamış demektir.

**Fark Alma (Differencing)** — Bir seriyi durağan hale getirmek ve otokorelasyonları yönetmek için kullanılır. Zaman serisi analizinde bazen fark almaya gerek olmayabilir; aşırı fark alınmış seriler yanlış tahminlere yol açabilir.

**Bağımlılık (Dependence)** — Aynı değişkenin önceki zaman dilimlerindeki iki gözlem arasındaki ilişkiyi ifade eder.

**Gürültü (Noise)** — Modelin açıklayamadığı gözlemlerdeki değişkenliktir.

Zaman serisi analizinde bu kavramlar, verideki temel dinamikleri ve desenleri anlamak için çok önemlidir. Doğru analiz ve tahmin, bu temel ilkelerin iyi anlaşılmasına bağlıdır. Trendlerin ayrıştırılması, mevsimsel etkilerin belirlenmesi, ayrıştırma yöntemlerinin kullanılması, durağanlığın sağlanması, fark almanın doğru şekilde uygulanması, bağımlılığın dikkate alınması ve gürültünün tanınması sayesinde analistler anlamlı içgörüler elde edebilir ve gelecekteki sonuçları etkili şekilde tahmin eden sağlam modeller kurabilir.

#### Düzleştirme (Smoothing) Teknikleri

**Düzleştirme**, serideki gürültüyü azaltmak ve zaman içinde ortaya çıkabilecek temel desenleri ortaya çıkarmak için temel bir süreçtir. Zaman serisi analizinde üç önemli düzleştirme yöntemi vardır.

**Tek Üstel Düzleştirme (Single Exponential Smoothing):** Basit Üstel Düzleştirme olarak da bilinir; trend veya mevsimsellik içermeyen tek değişkenli veriler için bir zaman serisi tahmin tekniğidir. Durağan serilerde iyi performans gösterir. Burada alfa, 0 ile 1 arasında değer alan bir düzleştirme katsayısıdır ve önceki gözlemlere verilen ağırlığın ne kadar hızlı azaldığını belirler. (yt​ = t anındaki düzleştirilmiş değer, α = Düzleştirme sabiti (0 < α < 1), xt = t anındaki gerçek değer, y(t−1) = t−1 anındaki düzleştirilmiş değer)

$$S_t = \alpha X_t + (1 – \alpha) S_{t-1}$$

$$F_{t+k} = S_t \quad \text{(k = 1, 2, 3, ... için)}$$

Burada:

* $S_t$: Serinin t anındaki düzleştirilmiş (veya seviyelendirilmiş) değeri
* $X_t$: t anındaki gerçek gözlemlenen değer
* $S_{t-1}$: Önceki dönemin ($t-1$) düzleştirilmiş değeri
* $\alpha$ (alfa): Düzleştirme katsayısı ($0 \le \alpha \le 1$). Alfa 1'e yaklaştıkça model son değişikliklere daha hızlı tepki verir; 0'a yaklaştıkça düzleştirme artar ve model son değişikliklere daha az duyarlı olur.
* $F_{t+k}$: t anından itibaren k adım sonrası için tahmin

**Çift Üstel Düzleştirme (Double Exponential Smoothing):** Çift Üstel Düzleştirme, üstel düzleştirmenin bir uzantısıdır ve tek değişkenli zaman serilerinde trendi açıkça modele dahil eder. Toplayıcı trendli Çift Üstel Düzleştirme, klasik olarak Holt’un Doğrusal Trend modeli olarak bilinir. Burada beta, trend düzleştirme katsayısıdır ve 0 ile 1 arasında değer alır.

$$S_t = \alpha X_t + (1 – \alpha) (S_{t-1} + b_{t-1})$$

$$b_t = \beta (S_t – S_{t-1}) + (1 – \beta) b_{t-1}$$

$$F_{t+k} = S_t + k b_t$$

Burada:

* $S_t$: t anındaki düzleştirilmiş değer
* $\alpha$: Düzleştirme sabiti ($0 < \alpha < 1$)
* $X_t$: t anındaki gerçek değer
* $b_t$: t anındaki trend bileşeni
* $\beta$: Trend düzleştirme sabiti ($0 < \beta < 1$)
* $F_{t+k}$: t anında k adım sonrası için tahmin
* $k$: Tahmin için ileriye bakılan dönem sayısı

**Üçlü Üstel Düzleştirme (Triple Exponential Smoothing):** Üçlü Üstel Düzleştirme, üstel düzleştirmenin bir uzantısıdır ve tek değişkenli zaman serilerinde mevsimselliği açıkça modele dahil eder. Bu yöntem bazen Holt-Winters Üstel Düzleştirme olarak adlandırılır. Gamma, mevsimsel düzleştirme katsayısıdır ve L, mevsim uzunluğunu temsil eder.

$$L_t = \alpha \left( \frac{X_t}{S_{t-m}} \right) + (1 – \alpha) (L_{t-1} + T_{t-1})$$

$$T_t = \beta (L_t – L_{t-1}) + (1 – \beta) T_{t-1}$$

$$S_t = \gamma \left( \frac{X_t}{L_t} \right) + (1 – \gamma) S_{t-m}$$

$$F_{t+k} = (L_t + k T_t) S_{t-m+k \pmod m}$$

Burada:

* $L_t$: t anındaki düzleştirilmiş seviye
* $T_t$: t anındaki düzleştirilmiş trend
* $S_t$: t anındaki mevsimsel bileşen
* $X_t$: t anındaki gerçek değer
* $\alpha$: Seviye düzleştirme katsayısı ($0 < \alpha < 1$)
* $\beta$: Trend düzleştirme katsayısı ($0 < \beta < 1$)
* $\gamma$: Mevsimsel düzleştirme katsayısı ($0 < \gamma < 1$)
* $m$: Bir mevsimdeki dönem sayısı
* $k$: Tahmin için ileriye bakılan dönem sayısı

Bu düzleştirme teknikleri sayesinde analistler, zaman serisi verilerindeki anlamlı desenleri ve trendleri daha iyi görebilir ve gürültünün etkisini azaltabilir. Uygun düzleştirme katsayılarının seçimi ve verideki trend veya mevsimsellik türünün dikkate alınması, tahmin doğruluğunu önemli ölçüde etkiler. Bu teknikler, ekonomiden sağlığa, meteorolojiden birçok farklı alanda karmaşık zamansal veri desenlerini anlamak ve tahmin etmek için değerli araçlar sunar.

#### Otoregresyon (AR) Modelleri

Otoregresyon (AR) yöntemi, bir dizideki bir sonraki adımı, önceki zaman adımlarındaki gözlemlerin doğrusal bir fonksiyonu olarak modeller. Bu yöntem, trend veya mevsimsellik içermeyen tek değişkenli zaman serileri için uygundur. Herhangi bir istatistiksel model uygulamadan önce verimizin durağan olması gerektiğini unutmamak önemlidir.

#### Durağan Veri

Durağan bir zaman serisi, ortalama, varyans ve kovaryans gibi özellikleri serinin gözlemlendiği zamana bağlı olmayan seridir. Dolayısıyla, trend veya mevsimsellik içeren zaman serileri durağan değildir; trend ve mevsimsellik, zaman serisinin farklı noktalarında değeri etkiler. Model, yalnızca belirli özellikler (ortalama, varyans, kovaryans) seçilen zaman aralıklarında tutarlıysa etkili çalışır. Veri setinizde bir trend varsa, devam etmeden önce bunu (fark alma veya detrending ile) kaldırmanız gerekir.

Durağan veri özellikleri şunlardır:

- Sabit ortalama
- Sabit varyans
- Durağan kovaryans
- Otokorelasyon

Bir otoregresyon modeli, bir zaman serisinin önceki gözlemlerinin, bir sonraki zaman adımındaki değeri tahmin etmek için yararlı olabileceğini varsayar. Değişkenler arasındaki bu ilişkiye korelasyon denir. Her iki değişken de aynı yönde değişiyorsa pozitif korelasyon, zıt yönde değişiyorsa negatif korelasyon vardır. Çıktı değişkeni ile belirli gecikmeli (lagged) zaman adımlarındaki değerler arasındaki korelasyonu hesaplamak için çeşitli istatistiksel ölçüler kullanılabilir. Çıktı değişkeni ile gecikmeli değişken arasındaki korelasyon ne kadar güçlüyse, otoregresyon modeli modelleme sırasında o değişkene o kadar fazla ağırlık verebilir.

**Gecikmeler (Lags):** Bunlar, dikkate alınan zaman aralığındaki değerlerdir ve gecikme olarak adlandırılır. Daha genel olarak, gecikme k otokorelasyonu, k zaman birimi arayla alınan değerler arasındaki korelasyondur.

**ACF (Otokorelasyon Fonksiyonu):** ACF, herhangi bir serinin gecikmeli değerleriyle olan otokorelasyon değerlerini sağlayan bir otokorelasyon fonksiyonudur. Basitçe, serinin mevcut değeri ile geçmişteki değerleri arasındaki ilişkinin ne kadar güçlü olduğunu açıklar. Bir zaman serisi trend, mevsimsellik, çevrimsel ve artık bileşenler içerebilir. ACF, korelasyonları bulurken tüm bu bileşenleri dikkate alır ve bu nedenle 'tam otokorelasyon grafiği' olarak adlandırılır.

**PACF (Kısmi Otokorelasyon Fonksiyonu):** PACF, kısmi otokorelasyon fonksiyonudur. Adından da anlaşılacağı gibi, PACF ACF'nin bir alt kümesidir. PACF, iki zaman noktasında yapılan gözlemler arasındaki korelasyonu, diğer veri noktalarının etkilerini hesaba katarak yakalar. PACF'yi, bir AR modelinde kullanılacak en uygun terim sayısını belirlemek için kullanabiliriz. Terim sayısı, modelin derecesini belirler. Bir AR modeli genellikle en iyi PACF değerleri kullanılarak tanımlanır.

#### Hareketli Ortalama (MA)

Hareketli Ortalama, aynı zamanda Rolling veya Running Average olarak da bilinir, zaman serisi verilerini analiz etmek için tam veri setinin farklı alt kümelerinin ortalamalarını hesaplamak için kullanılır. Zaman içinde veri setinin ortalaması alındığı için, Hareketli Ortalama (MA), Hareketli Ortalama (MM) veya Rolling Mean olarak da adlandırılır.

#### Otoregresif Hareketli Ortalama (ARMA)

ARMA yöntemi, bir dizideki bir sonraki adımı, önceki zaman adımlarındaki gözlemler ve artık hataların doğrusal bir fonksiyonu olarak modeller. Hem Otoregresyon (AR) hem de Hareketli Ortalama (MA) modellerini birleştirir.

#### Otoregresif Entegre Hareketli Ortalama (ARIMA)

ARIMA, ARMA'nın bir uzantısıdır ve bir dizideki bir sonraki adımı, fark alınmış gözlemler ve önceki zaman adımlarındaki artık hataların doğrusal bir fonksiyonu olarak modeller. AR ve MA modellerini birleştirmenin yanı sıra, seriyi durağan hale getirmek için fark alma işlemini de içerir. Bu entegrasyon adımı ARIMA'daki “I” harfiyle gösterilir.

#### Mevsimsel Otoregresif Entegre Hareketli Ortalama (SARIMA)

SARIMA, bir dizideki bir sonraki adımı, fark alınmış gözlemler, artık hatalar, mevsimsel fark alınmış gözlemler ve önceki zaman adımlarındaki mevsimsel artık hataların doğrusal bir fonksiyonu olarak modeller. ARIMA'yı, mevsimsel düzeyde otoregresyon, fark alma ve hareketli ortalama modellemesi yapabilme yeteneğiyle birleştirir.

#### Dışsal Regresörlü Mevsimsel Otoregresif Entegre Hareketli Ortalama (SARIMAX)

SARIMAX, SARIMA'nın bir uzantısıdır ve dışsal değişkenlerin modellemesini de içerir. ARX, MAX, ARMAX ve ARIMAX gibi dışsal değişkenli çeşitli modelleri kapsayabilir. Bu yöntem, trend ve/veya mevsimsel bileşenlerin yanı sıra dışsal değişkenler içeren tek değişkenli zaman serileri için uygundur.

#### Vektör Otoregresif Hareketli Ortalama (VARMA)

VARMA yöntemi, her bir zaman serisinin bir sonraki adımını bir ARMA modeli kullanarak modeller. ARMA'nın çoklu paralel zaman serilerine (yani çok değişkenli zaman serilerine) genelleştirilmiş halidir. Trend ve mevsimsel bileşenler içermeyen çok değişkenli zaman serileri için uygundur.

#### Dışsal Regresörlü Vektör Otoregresif Hareketli Ortalama (VARMAX)

VARMAX, VARMA'nın bir uzantısıdır ve dışsal değişkenlerin modellemesini de içerir. ARMAX yönteminin çok değişkenli versiyonudur ve dışsal değişkenlerin VARMA çerçevesinde modellenmesini kapsar.

#### Python ile ARIMA Modeli Örneği

```python
import pandas as pd
from statsmodels.tsa.arima.model import ARIMA

# Veri setini yükleme
data = pd.read_csv('data.csv')

# 'Date' sütununu datetime'a çevirme
data['Date'] = pd.to_datetime(data['Date'])

# 'Date' sütununu indeks olarak ayarlama
data.set_index('Date', inplace=True)

# ARIMA modelini oluşturma ve eğitme
# order parametresi (p, d, q) şeklindedir:
# p = modele dahil edilen gecikmeli gözlem sayısı (otoregresif kısım)
# d = ham gözlemlerin kaç kez fark alındığı (fark alma kısmı)
# q = hareketli ortalama penceresinin boyutu (hareketli ortalama kısmı)
model = ARIMA(data, order=(1, 1, 1))
model_fit = model.fit()

# Sonraki 5 zaman adımı için tahmin yapma
forecast = model_fit.forecast(steps=5)

# Tahmin edilen değerleri yazdırma
print(forecast)
```

Bu kod örneğinde, zaman serisi verisi data.csv adlı bir dosyadan yüklenir. Ardından, 'Date' sütunu datetime'a çevrilir ve indeks olarak ayarlanır. (1, 1, 1) parametreli ARIMA modeli oluşturulup veriye uygulanır. Son olarak, forecast metodu ile sonraki 5 adım için tahmin yapılır.

#### SARIMA Modeli Örneği

```python
import pandas as pd
from statsmodels.tsa.statespace.sarimax import SARIMAX

# Veri setini yükleme
data = pd.read_csv('data.csv')

# 'Date' sütununu datetime'a çevirme
data['Date'] = pd.to_datetime(data['Date'])

# 'Date' sütununu indeks olarak ayarlama
data.set_index('Date', inplace=True)

# SARIMA modelini oluşturma ve eğitme
# order parametresi (p, d, q) şeklindedir:
# p = modele dahil edilen gecikmeli gözlem sayısı (otoregresif kısım)
# d = ham gözlemlerin kaç kez fark alındığı (fark alma kısmı)
# q = hareketli ortalama penceresinin boyutu (hareketli ortalama kısmı)
# seasonal_order parametresi (P, D, Q, s) şeklindedir:
# P = mevsimsel otoregresif derecesi
# D = mevsimsel fark alma derecesi
# Q = mevsimsel hareketli ortalama derecesi
# s = bir mevsimsel dönemdeki zaman adımı sayısı
model = SARIMAX(data, order=(1, 1, 1), seasonal_order=(1, 1, 1, 12))
model_fit = model.fit()

# Sonraki 5 zaman adımı için tahmin yapma
forecast = model_fit.forecast(steps=5)

# Tahmin edilen değerleri yazdırma
print(forecast)
```

Bu örnekte, zaman serisi verisi data.csv adlı bir dosyadan yüklenir. Ardından, 'Date' sütunu datetime'a çevrilir ve indeks olarak ayarlanır. (1, 1, 1) parametreli ve mevsimsel olarak (1, 1, 1, 12) parametreli SARIMA modeli oluşturulup veriye uygulanır. Son olarak, forecast metodu ile sonraki 5 adım için tahmin yapılır.

#### ETS Modeli Örneği

```python
import pandas as pd
from statsmodels.tsa.holtwinters import ExponentialSmoothing

# Veri setini yükleme
data = pd.read_csv('data.csv')

# 'Date' sütununu datetime'a çevirme
data['Date'] = pd.to_datetime(data['Date'])

# 'Date' sütununu indeks olarak ayarlama
data.set_index('Date', inplace=True)

# ETS modelini oluşturma ve eğitme
# Parametreler:
# trend: 'add' eklemeli trend bileşeni olduğunu belirtir
# seasonal: 'add' eklemeli mevsimsel bileşen olduğunu belirtir
# seasonal_periods: bir mevsimdeki dönem sayısı (ör. aylık veri için 12)
model = ExponentialSmoothing(data, trend='add', seasonal='add', seasonal_periods=12)
model_fit = model.fit()

# Sonraki 5 zaman adımı için tahmin yapma
forecast = model_fit.forecast(steps=5)

# Tahmin edilen değerleri yazdırma
print(forecast)
```

Bu örnekte, zaman serisi verisi data.csv adlı bir dosyadan yüklenir. Ardından, 'Date' sütunu datetime'a çevrilir ve indeks olarak ayarlanır. Eklemeli trend ve eklemeli mevsimsellik içeren ETS modeli oluşturulup veriye uygulanır. seasonal_periods parametresi 12 olarak ayarlanmıştır (yıllık mevsimsellik için aylık veri). Son olarak, forecast metodu ile sonraki 5 adım için tahmin yapılır.

#### GARCH Modeli Örneği

```python
import pandas as pd
import arch

# Veri setini yükleme
data = pd.read_csv('data.csv')

# 'Date' sütununu datetime'a çevirme
data['Date'] = pd.to_datetime(data['Date'])

# 'Date' sütununu indeks olarak ayarlama
data.set_index('Date', inplace=True)

# GARCH modelini oluşturma ve eğitme
# Parametreler:
# vol: 'Garch' modeli volatilite modellemesi için kullanılır
# p: gecikmeli volatilite terimi sayısı (GARCH derecesi)
# q: gecikmeli kareli getiri terimi sayısı (ARCH derecesi)
model = arch.arch_model(data, vol='Garch', p=1, q=1)
model_fit = model.fit()

# Sonraki 5 zaman adımı için volatilite tahmini yapma
forecast = model_fit.forecast(horizon=5)

# Tahmin edilen varyansları yazdırma
print(forecast.variance.values[-1, :])
```

Bu örnekte, zaman serisi verisi data.csv adlı bir dosyadan yüklenir. Ardından, 'Date' sütunu datetime'a çevrilir ve indeks olarak ayarlanır. p=1 ve q=1 parametreli GARCH modeli oluşturulup veriye uygulanır. Son olarak, forecast metodu ile sonraki 5 adım için volatilite tahmini yapılır.

#### data.csv Örneği

```
Date,Value 
2010-01-01,10 
2010-02-01,15 
2010-03-01,12 
2010-04-01,18 
2010-05-01,20 
2010-06-01,16 
2010-07-01,14 
2010-08-01,18 
2010-09-01,22 
2010-10-01,25 
2010-11-01,20 
2010-12-01,16
```

Uygun zaman serisi tahmin modeli seçildikten sonra, bu model veri üzerinde tahminler üretmek için kullanılır. Bu tahminler genellikle gerçek değerlerle karşılaştırılır ve modelin uyum başarısı değerlendirilir. Modelin performansını değerlendirmek için yaygın olarak kullanılan metrikler arasında ortalama karesel hata (MSE), ortalama mutlak hata (MAE) ve kök ortalama karesel hata (RMSE) bulunmaktadır.