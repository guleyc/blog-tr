---
title: 'Python ile Veri Analizi'
date: '2023-08-24'
author: 'Çağatay Güley'
layout: post
permalink: /python-ile-veri-analizi/
en_url: /data-analysis-with-python/
redirect_from:
  - /data-analysis-with-python/
  - /data-analysis-with-python
  - /python-ile-veri-analizi
categories: [muhendislik]
tags: [veri, analiz, python, veri bilimi, makine ogrenmesi, istatistik, gorsellestirme, modelleme]
image: python.jpg

---

Python, veri biliminin *lingua franca*'sı olarak kabul edilir; bunun nedeni yalnızca zarif sözdizimi değil, aynı zamanda güçlü ve kapsamlı kütüphane ekosistemidir. Bu ekosistem, veri alımından ve temizlemeden karmaşık istatistiksel modelleme ve görselleştirmeye kadar uçtan uca veri analizi için kapsamlı bir araç seti sunar. Bu makale, temel kütüphanelerin teknik bir özetini ve Python'da veri analizi yapmak için pratik bir iş akışını sunar.

## Python Veri Bilimi Temel Kütüphaneleri

Başarılı bir Python veri analizi projesi, birkaç temel kütüphane üzerine inşa edilir. Bunların bireysel rollerini ve nasıl birlikte çalıştıklarını anlamak kritiktir.

* **NumPy (Numerical Python):** Bilimsel Python ekosisteminin temelidir. NumPy'nin ana özelliği, vektörleştirilmiş aritmetik ve gelişmiş yayınlama işlemlerini mümkün kılan yüksek performanslı bir veri yapısı olan `ndarray` (n-boyutlu dizi) nesnesidir. Diğer çoğu veri analizi kütüphanesi, pandas dahil, NumPy üzerine inşa edilmiştir.

* **Pandas:** Veri manipülasyonu ve analizi için vazgeçilmez kütüphane. Pandas iki ana veri yapısı sunar: `Series` (1D) ve `DataFrame` (2D). Veri okuma/yazma, temizleme, filtreleme, dönüştürme, gruplama ve birleştirme gibi yüksek performanslı araçlar sağlar; bu süreç genellikle "data wrangling" olarak adlandırılır.

* **Matplotlib & Seaborn:** Veri görselleştirme için ana kütüphanelerdir.
    * **Matplotlib**, bir figürün her yönü üzerinde ayrıntılı kontrol sunan temel çizim kütüphanesidir. Güçlüdür ancak karmaşık grafikler için ayrıntılı kod gerekebilir.
    * **Seaborn**, Matplotlib üzerine inşa edilmiş daha üst düzey bir kütüphanedir. Isı haritaları, pair plot'lar ve karmaşık regresyon grafiklerini estetik ve bilgilendirici şekilde oluşturmak için daha deklaratif bir arayüz sunar.

* **Scikit-Learn:** Python'daki başlıca makine öğrenmesi kütüphanesidir. Geniş bir denetimli ve denetimsiz öğrenme algoritması yelpazesi için birleşik ve tutarlı bir API (`.fit()`, `.predict()`, `.transform()`) sunar; regresyon, sınıflandırma, kümeleme ve boyut indirgeme dahil. Ayrıca model seçimi, değerlendirme ve veri ön işleme için temel araçlar içerir.

* **SciPy (Scientific Python):** NumPy temel dizi yapılarını sağlarken, SciPy bunların üzerine inşa edilerek daha gelişmiş bilimsel ve teknik hesaplama algoritmaları sunar. Optimizasyon, lineer cebir, integrasyon, interpolasyon, özel fonksiyonlar ve sinyal/görüntü işleme modüllerini kapsar.

* **Statsmodels:** İstatistiksel modelleme ve çıkarım için özel bir kütüphanedir. Scikit-learn tahmine odaklanırken, Statsmodels ayrıntılı istatistiksel analiz (özet istatistikler, p-değerleri, güven aralıkları) sağlar; lineer regresyon, ANOVA ve zaman serisi analizi gibi modeller için uygundur.

* **Jupyter Notebook:** "Literate programming" için interaktif bir hesaplama ortamıdır. Canlı kod, denklemler, görselleştirmeler ve anlatı metni içeren belgeler oluşturup paylaşmanıza olanak tanır. Analiz iş akışını belgelemek, şeffaflık ve tekrarlanabilirlik sağlamak için idealdir.

## Standart Bir Veri Analizi İş Akışı

Aşağıdaki adımlar, Python'da veri analizinin tipik ve yinelemeli sürecini özetler.

### Adım 0: Ortam Kurulumu
Öncelikle gerekli tüm paketlerin Python ortamınızda kurulu olduğundan emin olun. Komut satırında `pip` ile kurabilirsiniz.

```shell
pip install numpy pandas matplotlib seaborn scikit-learn
```

### Adım 1: Kütüphanelerin İçe Aktarılması
Script veya notebook'unuza kütüphaneleri geleneksel takma adlarıyla dahil edin.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

### Adım 2: Veri Yükleme ve Alımı
Veri setinizi bir pandas DataFrame'e yükleyin. Pandas birçok dosya formatını destekler, en yaygını `read_csv`'dir.

```python
# CSV dosyasından DataFrame'e veri yükleme
df = pd.read_csv("your_dataset.csv")
```

### Adım 3: Keşifsel Veri Analizi (EDA) ve İnceleme
Herhangi bir resmi analizden önce, verinizin yapısı ve içeriği hakkında genel bir bakış elde edin.

```python
# DataFrame'in ilk 5 satırını göster
print(df.head())

# DataFrame'in özetini al (sütun adları, null olmayan sayılar, veri tipleri)
print(df.info())

# Tanımlayıcı istatistikler (count, mean, std, min, max, çeyrekler)
print(df.describe())
```

### Adım 4: Veri Temizleme ve Ön İşleme
Gerçek dünya verisi genellikle kusurludur. Bu adımda eksik değerlerle başa çıkılır, tekrarlar kaldırılır ve veri tipleri düzeltilir. Genellikle en çok zaman alan ama en kritik kısımdır.

```python
# Eksik değer içeren satırları sil (not: imputasyon gibi başka stratejiler de var)
df_cleaned = df.dropna()

# Tekrarlayan satırları sil
df_cleaned = df.drop_duplicates()
```

### Adım 5: Veri Görselleştirme
Ham sayılardan görünmeyen desenleri, eğilimleri ve ilişkileri ortaya çıkarmak için veriyi görselleştirin.

```python
# İki sütun arasındaki ilişkiyi göstermek için scatter plot
sns.scatterplot(x="column_name_1", y="column_name_2", data=df_cleaned)
plt.title("Sütun 1 ve Sütun 2 Arasındaki İlişki")
plt.xlabel("X Eksen Etiketi")
plt.ylabel("Y Eksen Etiketi")
plt.show()
```

### Adım 6: İstatistiksel Analiz ve Özellik Mühendisliği
Hipotezleri doğrulamak için istatistiksel testler uygulayın. Ayrıca model performansını artırmak için mevcut verilerden yeni özellikler (feature engineering) oluşturabilirsiniz.

```python
# Sütunların ikili korelasyonunu hesapla
correlation_matrix = df_cleaned.corr()
print(correlation_matrix)

# Korelasyon matrisini ısı haritası ile görselleştir
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm')
plt.show()
```

### Adım 7: Tahmine Dayalı Modelleme (Opsiyonel)
Eğer amacınız tahmin yapmaksa, makine öğrenmesi modelleri uygulayabilirsiniz.

```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Özellik (X) ve hedef (y) değişkenlerini tanımla
features = ["feature_column_1", "feature_column_2"]
target = "target_column"

X = df_cleaned[features]
y = df_cleaned[target]

# Veriyi eğitim ve test setlerine ayır
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Modeli başlat ve eğit
model = LinearRegression()
model.fit(X_train, y_train)

# Tahmin yap ve modeli değerlendir
predictions = model.predict(X_test)
print(f"Model R^2 skoru: {model.score(X_test, y_test)}")
```

Python ekosistemi, modern veri analizi için benzersiz ve uçtan uca bir ortam sunar. Temel kütüphaneleri ustalıkla kullanarak ve yapılandırılmış bir iş akışı benimseyerek, analistler ve veri bilimciler ham veriyi etkili bir şekilde eyleme dönüştürülebilir içgörülere dönüştürebilir. Burada özetlenen süreç, her analitik ihtiyaca göre uyarlanıp genişletilebilecek sağlam bir şablondur.