---
title: 'Soothsayer: Zaman Serisi Tahminleme Sistemi'
date: '2025-09-24'
author: 'Cagatay Guley'
layout: post
permalink: /soothsayer-zaman-serisi-tahminleme-sistemi/
en_url: /soothsayer-time-series-forecasting-system/
redirect_from:
  - /soothsayer-zaman-serisi-tahminleme-sistemi
  - /soothsayer-time-series-forecasting-system
  - /soothsayer-time-series-forecasting-system/
tags: [tahmin, öngörü, zaman, seri, soothsayer]
image: timeseries.jpeg
---

Bu yazıda, Python ile geliştirdiğim optimize edilmiş çoklu yöntemli zaman serisi tahminleme sistemi **Soothsayer**'da kullanılan temel tahmin yöntemlerini adım adım anlatacağım. Kod, zaman serisi verilerindeki gelecekteki değerleri tahmin etmek için çeşitli istatistiksel ve makine öğrenimi modellerini entegre eder. Aşağıda, sistemde kullanılan her bir tahmin formülünü (veya yöntemini) açıklıyor, nasıl çalıştıklarını ve zaman serisi tahmininde neden etkili olduklarını özetliyorum.

## Proje Genel Bakış: Soothsayer

Soothsayer, zaman serisi verilerini verimli bir şekilde işlemek için tasarlanmıştır; klasik istatistiksel yöntemleri modern makine öğrenimi teknikleriyle birleştirir. Bir CSV dosyasından veri alır, mevsimselliği tespit eder, model hiperparametrelerini optimize eder ve sağlam tahminler için ağırlıklı toplu (ensemble) tahminler üretir. Sistem; Doğrusal Trend, Mevsimsel Naive, Hareketli Ortalama, Üstel Düzeltme, ARIMA, Prophet ve Random Forest, XGBoost, Sinir Ağları gibi çeşitli makine öğrenimi algoritmalarını içerir.

Aşağıda, `predict_statistical_models_enhanced` ve `predict_ml_models` fonksiyonlarında kullanılan tahmin yöntemlerini ve toplu ağırlıklandırma mekanizmasını açıklıyorum.

---

## İstatistiksel Tahmin Yöntemleri

Soothsayer'daki istatistiksel modeller `predict_statistical_models_enhanced` metodunda uygulanır. Bu yöntemler, zaman serisi verilerindeki trend ve mevsimsellik gibi desenleri yakalamada özellikle etkilidir. Kullanılan formül ve teknikler şunlardır:

### 1. Doğrusal Trend
**Ne yapar**: Zaman serisi verisine düz bir doğru uydurarak doğrusal trendi yakalar.

**Nasıl çalışır**:
- NumPy'nin `polyfit` fonksiyonu ile verilere doğrusal bir polinom (`y = mx + c`) uydurulur. Burada:
  - `x` zaman indeksi (0'dan veri uzunluğuna kadar tamsayılar).
  - `y` zaman serisi değerleri.
  - `m` eğim, `c` sabittir.
- Gelecekteki bir zaman noktasında tahmin:
  ```
  y_pred = m * (n + periods_ahead - 1) + c
  ```
- **Neden faydalı**: Yükselen veya azalan trendi olan verilerde basit ve etkilidir.

**Kod örneği**:
```python
x = np.arange(len(ts_data))
y = ts_data.values
coeffs = np.polyfit(x, y, 1)
trend_pred = coeffs[0] * (len(ts_data) + periods_ahead - 1) + coeffs[1]
```

### 2. Mevsimsel Naive
**Ne yapar**: Gelecekteki değerin, son gözlenen mevsimsel döngüdeki değerle aynı olacağını varsayar.

**Nasıl çalışır**:
- STL ayrıştırması ile mevsimsel periyot (ör. haftalık için 7, aylık için 30, yıllık için 365) tespit edilir.
- Mevsimsellik varsa, tahmin bir mevsimsel döngü öncesinin değeridir:
  ```
  y_pred = y[t - seasonal_period]
  ```
- Mevsimsellik yoksa, en son değer kullanılır:
  ```
  y_pred = y[t - 1]
  ```
- **Neden faydalı**: Haftalık veya aylık gibi tekrar eden desenleri hızlıca yakalar.

**Kod örneği**:
```python
seasonal_period = self.detect_seasonality(ts_data)
if seasonal_period and len(ts_data) >= seasonal_period:
    seasonal_pred = ts_data.iloc[-seasonal_period]
else:
    seasonal_pred = ts_data.iloc[-1]
```

### 3. Hareketli Ortalama
**Ne yapar**: Son gözlemlerin ortalamasını alarak bir sonraki değeri tahmin eder.

**Nasıl çalışır**:
- Son 30 veri veya veri uzunluğunun dörtte biri kadar bir pencere kullanılır.
- Tahmin, pencere içindeki değerlerin ortalamasıdır:
  ```
  y_pred = mean(y[t - window : t])
  ```
- **Neden faydalı**: Kısa vadeli dalgalanmaları yumuşatır ve durağan veriler için iyi bir temel tahmin sunar.

**Kod örneği**:
```python
window = min(30, len(ts_data) // 4, len(ts_data))
if window > 0:
    ma_pred = ts_data.tail(window).mean()
```

### 4. Üstel Düzeltme
**Ne yapar**: Seviye, trend ve mevsimsellik bileşenlerini üstel olarak azalan ağırlıklarla birleştirir.

**Nasıl çalışır**:
- `statsmodels.tsa.holtwinters.ExponentialSmoothing` ile otomatik trend ve mevsimsellik tespiti yapılır.
- Augmented Dickey-Fuller testi (`adfuller`) ile trend olup olmadığı kontrol edilir.
- STL ile mevsimsellik tespit edilir.
- Model şu şekilde yapılandırılır:
  - Trend varsa (`trend='add'`), trend bileşeni eklenir.
  - Mevsimsellik varsa (`seasonal='add'`), mevsimsel bileşen eklenir.
- Tahmin:
  ```
  y_pred = fitted_model.forecast(periods_ahead)
  ```
- **Neden faydalı**: Trend ve mevsimsellik içeren verilerde hem yeni hem eski gözlemleri dengeler.

**Kod örneği**:
```python
seasonal_period = self.detect_seasonality(ts_data)
trend_test = adfuller(ts_data.diff().dropna())[1] < 0.05
model = ExponentialSmoothing(
    ts_data,
    trend='add' if trend_test else None,
    seasonal='add' if seasonal_period else None,
    seasonal_periods=seasonal_period
)
fitted_model = model.fit()
exp_pred = fitted_model.forecast(periods_ahead).iloc[-1]
```

### 5. ARIMA
**Ne yapar**: Otoregresif Entegre Hareketli Ortalama modeli, zaman serisindeki trend ve bağımlılıkları yakalar.

**Nasıl çalışır**:
- `pmdarima` kütüphanesi varsa, `auto_arima` ile en iyi ARIMA parametreleri otomatik seçilir (`p`, `d`, `q`).
  - Maksimum otoregresif derecesi (`max_p=3`), fark alma (`max_d=2`), hareketli ortalama (`max_q=3`).
  - Mevsimsel bileşenler etkin, adım adım arama yapılır.
- Yoksa, basit ARIMA(1,1,1) modeli kullanılır:
  ```
  y_pred = fitted_model.forecast(periods_ahead)
  ```
- **Neden faydalı**: Trend ve kısa vadeli bağımlılıkları modellemede güçlüdür.

**Kod örneği**:
```python
if HAS_AUTO_ARIMA:
    model = auto_arima(
        ts_data, 
        seasonal=True, 
        stepwise=True,
        max_p=3, max_q=3, max_d=2
    )
    arima_pred = model.predict(n_periods=periods_ahead)[-1]
else:
    model = ARIMA(ts_data, order=(1, 1, 1))
    fitted_model = model.fit()
    arima_pred = fitted_model.forecast(periods_ahead).iloc[-1]
```

### 6. Prophet
**Ne yapar**: Facebook tarafından geliştirilen, güçlü mevsimsel desenler ve eksik veri içeren zaman serileri için esnek bir tahmin modelidir.

**Nasıl çalışır**:
- `prophet` kütüphanesi varsa, `ds` (tarihler) ve `y` (değerler) içeren bir DataFrame hazırlanır.
- Veri uzunluğuna göre mevsimsellik etkinleştirilir:
  - Veri >365 günse günlük mevsimsellik.
  - Veri >90 günse haftalık mevsimsellik.
  - Veri >365 günse yıllık mevsimsellik.
- Model, esneklik için 0.05 değişim noktası önceliğiyle fit edilir:
  ```
  y_pred = model.predict(future_df)['yhat']
  ```
- **Neden faydalı**: Eksik veri, aykırı değer ve çoklu mevsimsellik içeren gerçek dünya zaman serilerinde etkilidir.

**Kod örneği**:
```python
if HAS_PROPHET:
    prophet_df = pd.DataFrame({
        'ds': ts_data.index,
        'y': ts_data.values
    })
    model = Prophet(
        daily_seasonality=len(ts_data) > 365,
        weekly_seasonality=len(ts_data) > 90,
        yearly_seasonality=len(ts_data) > 365,
        changepoint_prior_scale=0.05
    )
    model.fit(prophet_df)
    future_df = pd.DataFrame({'ds': [target_date]})
    forecast = model.predict(future_df)
    prophet_pred = forecast['yhat'].iloc[0]
```

---

## Makine Öğrenimi Modelleri

Makine öğrenimi modelleri Soothsayer'da `predict_ml_models` metodunda uygulanır ve `create_enhanced_features` ile oluşturulan özelliklerden faydalanır. Bu modeller, gecikmeli değerler, istatistiksel özetler ve zamana dayalı özelliklerle eğitilir.

### 1. Doğrusal Regresyon
- **Ne yapar**: Girdi özelliklerine doğrusal bir model uydurur.
- **Formül**: `y = w0 + w1*x1 + w2*x2 + ... + wn*xn`
- **Neden faydalı**: Basit, yorumlanabilir ve ilişkiler doğrusal olduğunda etkilidir.

### 2. Ridge Regresyon
- **Ne yapar**: L2 düzenlileştirmeli doğrusal regresyon, aşırı öğrenmeyi önler.
- **Formül**: `||y - Xw||^2 + alpha * ||w||^2` minimize edilir.
- **Neden faydalı**: Özellikler arasında çoklu bağlantı olduğunda etkilidir.

### 3. Lasso Regresyon
- **Ne yapar**: L1 düzenlileştirmeli doğrusal regresyon, özellik seçimi yapar.
- **Formül**: `||y - Xw||^2 + alpha * ||w||_1` minimize edilir.
- **Neden faydalı**: Önemli özellikleri otomatik seçer.

### 4. Elastic Net
- **Ne yapar**: L1 ve L2 düzenlileştirmeyi birleştirir.
- **Formül**: `||y - Xw||^2 + alpha * (l1_ratio * ||w||_1 + 0.5 * (1 - l1_ratio) * ||w||^2)`
- **Neden faydalı**: Özellik seçimi ve düzenlileştirme arasında denge kurar.

### 5. Karar Ağacı
- **Ne yapar**: Özellik eşiklerine göre veriyi bölerek hedefi tahmin eder.
- **Neden faydalı**: Doğrusal olmayan ilişkileri yakalar, ancak aşırı öğrenmeye yatkındır.

### 6. Rastgele Orman (Random Forest)
- **Ne yapar**: Bagging ile birden fazla karar ağacının topluluğunu oluşturur.
- **Neden faydalı**: Aşırı öğrenmeye karşı dayanıklıdır ve karmaşık desenlerde etkilidir.

### 7. Extra Trees
- **Ne yapar**: Random Forest'a benzer, ancak bölünmeler rastgeledir.
- **Neden faydalı**: Daha hızlıdır ve gürültülü verilerde genellikle iyi performans gösterir.

### 8. Gradient Boosting
- **Ne yapar**: Ağaçları ardışık olarak inşa eder, önceki ağaçların hatalarını düzeltir.
- **Neden faydalı**: Yapısal verilerde yüksek doğruluk sağlar.

### 9. Destek Vektör Regresyonu (SVR)
- **Ne yapar**: Bir tolerans aralığında regresyon modeli uydurur (RBF çekirdeği ile).
- **Neden faydalı**: Doğrusal olmayan ilişkilerde uygun ayarlamayla etkilidir.

### 10. Sinir Ağı (MLP)
- **Ne yapar**: Gizli katmanlara sahip çok katmanlı algılayıcı, karmaşık desenleri tanır.
- **Neden faydalı**: Karmaşık doğrusal olmayan desenleri yakalar, daha fazla veri gerektirir.

### 11. XGBoost (Opsiyonel)
- **Ne yapar**: Verimli ağaç budama ile optimize edilmiş gradient boosting.
- **Neden faydalı**: Yapısal verilerde hızlı ve yüksek doğruluk sağlar.

### 12. LightGBM (Opsiyonel)
- **Ne yapar**: Hız için histogram tabanlı öğrenme ile gradient boosting.
- **Neden faydalı**: Büyük veri setlerinde verimlidir.

**Özellik Mühendisliği**:
- Özellikler; gecikmeli değerler (ör. t-1, t-2, t-3, t-7, t-14, t-30), istatistiksel özetler (ortalama, std, min, max, çeyrekler) ve zamana dayalı özellikleri (hafta günü, ay, gün, çeyrek) içerir.
- Özellik seçimi, boyut indirgeme için `SelectKBest` ve `f_regression` ile yapılır.

**Kod örneği**:
```python
features = self.create_enhanced_features(target_date)
if name in self.scalers:
    features_scaled = self.scalers[name].transform(features)
    pred = model.predict(features_scaled)[0]
else:
    pred = model.predict(features)[0]
```

---

## Toplu (Ensemble) Ağırlıklandırma

`calculate_dynamic_weights_enhanced` metodu, tüm modellerin tahminlerini son dönemdeki performanslarına göre dinamik ağırlıklarla birleştirir.

**Nasıl çalışır**:
- Her model için, son tahminlerden elde edilen Ortalama Mutlak Hata (MAE) ve Kök Ortalama Kare Hata (RMSE) ile ağırlık hesaplanır:
  ```
  weight = 1.0 / (0.7 * MAE + 0.3 * RMSE + 1e-6)
  ```
- Ağırlıklar toplamı 1 olacak şekilde normalize edilir.
- Performansı %75'lik dilimin üzerinde olan modeller önceliklendirilir, ancak çeşitlilik için en az üç model tutulur.
- Son tahmin, ağırlıklı toplamdır:
  ```
  final_prediction = sum(pred_i * weight_i)
  ```

**Neden faydalı**: Birden fazla modelin güçlü yönlerini birleştirir, son dönemde daha iyi performans gösteren modellere daha fazla ağırlık verir.

**Kod örneği**:
```python
weight = 1.0 / (0.7 * mae + 0.3 * rmse + 1e-6)
weights = {k: v/total_weight for k, v in weights.items()}
weighted_prediction = sum(pred * weights.get(model, 0) for model, pred in all_predictions.items())
```

---

## Güven Aralığı Hesaplama

Belirsizlik tahmini için Soothsayer, toplu tahmin için %95 güven aralığı hesaplar:
- Bireysel model tahminlerinin standart sapması (`std_pred`) kullanılır.
- %95 güven için z-skoru 1.96 alınır:
  ```
  margin_error = 1.96 * std_pred
  conf_lower = weighted_prediction - margin_error
  conf_upper = weighted_prediction + margin_error
  ```

**Neden faydalı**: Tahminin belirsizliğini nicelendirir, kullanıcıya olası sonuç aralığını gösterir.

**Kod örneği**:
```python
z_score = 1.96
margin_error = z_score * std_pred
conf_lower = weighted_prediction - margin_error
conf_upper = weighted_prediction + margin_error
```

---

Soothsayer tahmin sistemi, sağlam zaman serisi tahminleri üretmek için çeşitli istatistiksel ve makine öğrenimi modellerini bir araya getirir. Doğrusal Trend, Mevsimsel Naive, Hareketli Ortalama, Üstel Düzeltme, ARIMA, Prophet ve çeşitli ML algoritmaları gibi yöntemlerle verideki çok çeşitli desenleri yakalar. Dinamik ağırlıklandırmalı toplu yaklaşım, en güvenilir modellerin son tahmine daha fazla katkı yapmasını sağlarken, güven aralığı tahminin belirsizliğini gösterir.

Soothsayer kodunu kendi projelerinizde denemekten çekinmeyin! Tam uygulamayı [Github'da](https://github.com/guleyc/soothsayer) bulabilirsiniz. Sistemle ilgili sorularınız veya geliştirme önerileriniz varsa yorumlarda belirtmekten çekinmeyin.
