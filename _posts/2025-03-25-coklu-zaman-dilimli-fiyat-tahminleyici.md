---
title: 'Çoklu Zaman Dilimli Fiyat Tahminleyici'
date: '2025-03-25'
author: 'Cagatay Guley'
layout: post
permalink: /coklu-zaman-dilimli-fiyat-tahminleyici/
redirect_from:
  - /multi-timeframe-price-predictor
  - /multi-timeframe-price-predictor/
categories: [muhendislik]
tags: [fiyat, tahmin, indikator, binance, kripto]
image: crypto-asset.png
---

Her piyasaya ve fiyat aralığına uyum sağlayan güçlü, çoklu zaman dilimli fiyat tahmin indikatörü.

## ✨ Temel Özellikler
- Çoklu zaman dilimlerinde tahmin (1dk'dan 1G'ye)
- Her varlık için uyarlanabilir fiyat formatı (BTC'den küçük altcoinlere kadar)
- Net Al/Sat sinyalleri ve görsel uyarılar
- RSI, MACD, Bollinger Bantları ve EMA'lar ile gelişmiş teknik analiz motoru
- Olası fiyat hareketlerini gösteren tahmin yolları
- Volatilite ayarlı, güven ağırlıklı tahminler

## 🔧 Ayarlar
- Tahmin periyodu: Desen analizinde kullanılan geçmiş veri uzunluğu (varsayılan: 14)
- Düzgünleştirme katsayısı: Tahminlerin ne kadar yumuşak değişeceği (0.1-0.9)
- Ondalık basamak: Varlık fiyatına göre otomatik veya manuel hassasiyet
- Volatilite ağırlığı: Piyasa oynaklığının tahminlere etkisi
- Güven seviyesi: Tahminlerin ne kadar agresif olacağı

## 📊 Sinyallerin Açıklaması
- GÜÇLÜ AL: Yüksek güvenle yukarı yönlü hareket bekleniyor
- AL: Orta düzeyde yukarı hareket bekleniyor
- NÖTR: Net bir yön yok
- SAT: Orta düzeyde aşağı hareket bekleniyor
- GÜÇLÜ SAT: Yüksek güvenle aşağı yönlü hareket bekleniyor

## 📈 Nasıl Kullanılır
1. Farklı zaman dilimleri için sinyal tablosunu izleyin
2. Birden fazla zaman diliminde uyum arayın
3. Olası hedefleri görmek için tahmin yollarını kullanın
4. Kendi işlem stratejinizle birlikte onay için kullanın

Günlük al-sat ve uzun vadeli pozisyon analizi için idealdir. Hisse, forex, kripto ve emtia piyasalarında çalışır.

```pinescript
//@version=6
//
// @author guleyc
// 
indicator("Çoklu Zaman Dilimli Fiyat Tahminleyici", overlay=true)

// Ana Ayarlar
predictionPeriods = input.int(14, "Tahmin periyodu", minval=5, maxval=100)
smoothingFactor = input.float(0.5, "Düzgünleştirme katsayısı", minval=0.1, maxval=0.9, step=0.1) 
showBuySell = input.bool(true, "Al/Sat sinyallerini göster")
timeFrames = input.string("1,5,15,1H,4H,1D", "Tahmin zaman dilimleri (virgül ile ayrılmış)")
manualDecimalsOption = input.string("Otomatik", "Ondalık basamak", options=["Otomatik", "2", "4", "6", "8"])

// Gelişmiş ayarlar
volatilityWeight = input.float(1.0, "Volatilite ağırlığı", minval=0.1, maxval=2.0, step=0.1)
confidenceLevel = input.float(0.75, "Güven seviyesi", minval=0.5, maxval=1.0, step=0.05)

// Renk ayarları
bullColor = color.rgb(0, 180, 0, 80)   // Yeşil
bearColor = color.rgb(255, 0, 0, 80)   // Kırmızı

// İndikatör hesaplamaları
rsi = ta.rsi(close, 14)
rsiShort = ta.rsi(close, 7)
[macdLine, signalLine, _] = ta.macd(close, 12, 26, 9)
[middle, upper, lower] = ta.bb(close, 20, 2)
ema20 = ta.ema(close, 20)
ema50 = ta.ema(close, 50)
ema200 = ta.ema(close, 200)

// Gelişmiş sinyal hesaplamaları
rsiSignal = rsi < 30 ? 1 : rsi > 70 ? -1 : (50 - rsi) / 20
rsiShortSignal = rsiShort < 30 ? 1 : rsiShort > 70 ? -1 : (50 - rsiShort) / 20
macdSignal = macdLine > signalLine ? 1 : macdLine < signalLine ? -1 : (macdLine - signalLine) * 5
bbSignal = close < lower ? 1 : close > upper ? -1 : (middle - close) / (upper - lower) * 2
emaSignal = ema20 > ema50 ? 0.5 : ema20 < ema50 ? -0.5 : 0
emaLongSignal = ema50 > ema200 ? 0.5 : ema50 < ema200 ? -0.5 : 0

// Toplam sinyal (ağırlıklı)
totalSignals = (rsiSignal * 2 + rsiShortSignal + macdSignal * 1.5 + bbSignal * 1.5 + emaSignal + emaLongSignal) / 7.5
normSignal = math.max(math.min(totalSignals, 1), -1)  // -1 ile 1 arası normalize

// Volatilite hesaplama
atr = ta.atr(14)
atrShort = ta.atr(7) 
atrRatio = atr / ta.sma(atr, 50)
volatilityFactor = math.min(atrRatio * volatilityWeight, 3.0)

// Zaman dilimi dizisini ayır
var string[] tf_array = str.split(timeFrames, ",")

// Fiyata göre otomatik ondalık basamak algılama
getDecimalPlaces() =>
    int decimals = 2 // çoğu varlık için varsayılan
    
    if manualDecimalsOption != "Otomatik"
        decimals := int(str.tonumber(manualDecimalsOption))
    else
        if close < 0.0001
            decimals := 8
        else if close < 0.01
            decimals := 6
        else if close < 1
            decimals := 4
        else if close < 100
            decimals := 2
        else
            decimals := 2
    
    decimals

// Fiyatı uygun ondalıkla formatla
formatPrice(price) =>
    int decimals = getDecimalPlaces()
    string format = "#." + str.repeat("#", decimals)
    str.tostring(price, format)

// Her zaman dilimi için tahmin hesapla
calculatePrediction(timeframe) =>
    float mult = timeframe == "1" ? 0.5 : timeframe == "3" ? 0.75 : timeframe == "5" ? 1.0 : timeframe == "15" ? 2.0 : timeframe == "30" ? 3.0 : timeframe == "1H" ? 5.0 : timeframe == "4H" ? 15.0 : timeframe == "1D" ? 30.0 : timeframe == "1W" ? 120.0 : 4.0
    
    // Gelişmiş tahmin mantığı
    float priceDelta = close * (normSignal * volatilityFactor * 0.01 * mult)
    float rawPrediction = close + priceDelta
    
    // Güven seviyesi uygula
    float adjustedPrediction = close + priceDelta * confidenceLevel
    
    // Son fiyat hareketiyle yumuşatma
    var float smoothedPrediction = na
    smoothedPrediction := na(smoothedPrediction) ? adjustedPrediction : adjustedPrediction * (1 - smoothingFactor) + smoothedPrediction * smoothingFactor
    
    // Sinyal gücü ve volatiliteye göre güven hesapla
    float signalConfidence = math.abs(normSignal) * confidenceLevel
    float volatilityImpact = math.max(0, 1 - (atrRatio - 1) * 0.5)
    float totalConfidence = math.min(signalConfidence * volatilityImpact, 0.95)
    
    [smoothedPrediction, normSignal * volatilityFactor, totalConfidence]

// Son değerleri tutan diziler
var float[] lastPredictions = array.new_float(10, na)
var float[] lastSignals = array.new_float(10, na)
var float[] lastConfidence = array.new_float(10, na)
var int lastSignalDir = 0

// Gelişmiş al-sat koşulları
buySignal = normSignal > 0.4 and normSignal > normSignal[1] and (lastSignalDir <= 0 or (lastSignalDir > 0 and normSignal > normSignal[3] * 1.2))
sellSignal = normSignal < -0.4 and normSignal < normSignal[1] and (lastSignalDir >= 0 or (lastSignalDir < 0 and normSignal < normSignal[3] * 1.2))

if buySignal or sellSignal
    lastSignalDir := buySignal ? 1 : -1

// Sadece barstate.islast'ta tahmin ve göstergeleri güncelle
if barstate.islast
    // Tahmin tablosu oluştur
    var table predictionTable = table.new(position.top_right, 4, math.min(array.size(tf_array), 10) + 1, bgcolor=color.rgb(0, 0, 0, 80), frame_width=2, border_width=1)
    
    // Tablo başlıkları
    table.cell(predictionTable, 0, 0, "Zaman Dilimi", bgcolor=color.rgb(0, 0, 40, 90), text_color=color.white)
    table.cell(predictionTable, 1, 0, "Fiyat", bgcolor=color.rgb(0, 0, 40, 90), text_color=color.white)
    table.cell(predictionTable, 2, 0, "% Değişim", bgcolor=color.rgb(0, 0, 40, 90), text_color=color.white)
    table.cell(predictionTable, 3, 0, "Sinyal", bgcolor=color.rgb(0, 0, 40, 90), text_color=color.white)
    
    // Etiketleri yeniden oluştur
    var label[] predictionLabels = array.new<label>()
    
    // Önceki etiketleri temizle
    if array.size(predictionLabels) > 0
        for i = 0 to array.size(predictionLabels) - 1
            label.delete(array.get(predictionLabels, i))
        array.clear(predictionLabels)
    
    // Her zaman dilimi için tahmin hesapla
    int tfCount = math.min(array.size(tf_array), 10)
    
    for i = 0 to tfCount - 1
        string tf = array.get(tf_array, i)
        [predictedPrice, signalStrength, confidence] = calculatePrediction(tf)
        
        // Değerleri kaydet
        array.set(lastPredictions, i, predictedPrice)
        array.set(lastSignals, i, signalStrength)
        array.set(lastConfidence, i, confidence)
        
        // Yüzde değişimi hesapla
        float percentChange = (predictedPrice - close) / close * 100
        
        // Renk ve sinyal metni hesapla
        color predColor = signalStrength > 0 ? bullColor : bearColor
        string signalText = signalStrength > 0.5 ? "GÜÇLÜ AL" : signalStrength > 0.2 ? "AL" : signalStrength < -0.5 ? "GÜÇLÜ SAT" : signalStrength < -0.2 ? "SAT" : "NÖTR"
        
        // Yüzde değişim ve fiyatı uygun ondalıkla formatla
        string formattedPrice = formatPrice(predictedPrice)
        string changeText = percentChange > 0 ? "+" + str.tostring(math.round(percentChange * 100) / 100, "#.##") + "%" : str.tostring(math.round(percentChange * 100) / 100, "#.##") + "%"
        
        // Tabloya ekle
        table.cell(predictionTable, 0, i + 1, tf, text_color=color.white)
        table.cell(predictionTable, 1, i + 1, formattedPrice, text_color=percentChange > 0 ? color.green : color.red)
        table.cell(predictionTable, 2, i + 1, changeText, text_color=percentChange > 0 ? color.green : color.red)
        table.cell(predictionTable, 3, i + 1, signalText, text_color=signalStrength > 0.5 ? color.rgb(0, 255, 0) : signalStrength > 0 ? color.rgb(0, 200, 0) : signalStrength < -0.5 ? color.rgb(255, 0, 0) : signalStrength < 0 ? color.rgb(200, 0, 0) : color.gray)
        
        // Fiyat tahmin etiketi (uyarlanabilir format)
        if i < 4  // En fazla 4 tahmin göster
            int labelOffset = i == 0 ? 3 : i == 1 ? 7 : i == 2 ? 12 : 20
            label newLabel = label.new(bar_index + labelOffset, predictedPrice, tf + ": " + formattedPrice + " (" + changeText + ")", color=color.new(predColor, 20), style=signalStrength > 0 ? label.style_label_up : label.style_label_down, textcolor=color.white)
            array.push(predictionLabels, newLabel)

// Temel hareketli ortalamaları her zaman göster
plot(ema20, "EMA 20", color.new(color.blue, 60), 1)
plot(ema50, "EMA 50", color.new(color.yellow, 60), 1)

// Al/Sat sinyallerini göster
plotshape(showBuySell and buySignal ? low - atr : na, "Al Sinyali", shape.triangleup, location.belowbar, color.green, 0, text="AL")
plotshape(showBuySell and sellSignal ? high + atr : na, "Sat Sinyali", shape.triangledown, location.abovebar, color.red, 0, text="SAT")

// Tahmin çizgilerini göster (son bardan itibaren)
var line[] predictionLines = array.new<line>()

// Önceki çizgileri temizle
if barstate.islast and array.size(predictionLines) > 0
    for i = 0 to array.size(predictionLines) - 1
        line.delete(array.get(predictionLines, i))
    array.clear(predictionLines)

// Yeni tahmin çizgilerini çiz
if barstate.islast
    for i = 0 to math.min(array.size(tf_array) - 1, 4)
        if not na(lastPredictions.get(i))
            color lineColor = lastSignals.get(i) > 0 ? color.new(color.green, 50) : color.new(color.red, 50)
            int lineOffset = i == 0 ? 3 : i == 1 ? 7 : i == 2 ? 12 : i == 3 ? 20 : 30
            newLine = line.new(x1=bar_index, y1=close, x2=bar_index + lineOffset, y2=lastPredictions.get(i), color=lineColor, width=2, style=lastSignals.get(i) > 0 ? line.style_solid : line.style_dashed)
            array.push(predictionLines, newLine)
```