# Türkiye Kısa Dönem Elektrik Yük Tahmini

Türkiye'nin saatlik elektrik tüketimini kısa dönemde tahmin etmek için geliştirilmiş, derin öğrenme ve makine öğrenmesi modellerinin karşılaştırmalı analizini içeren bitirme tezi çalışması.

## Özet
EPİAŞ Şeffaflık Platformu'ndan (EPTR2 API) çekilen 2017–2025 saatlik tüketim verisi üzerinde beş model karşılaştırıldı. En iyi sonucu **LSTM (Dual-Input)** mimarisi verdi (1 haftalık test penceresinde **MAPE %1.20, R² 0.9887**).

## Modeller ve Sonuçlar
| Model | MAPE | R² |
|---|---|---|
| LSTM (Dual-Input) | %1.20 | 0.9887 |
| XGBoost (Optuna) | %1.32 | 0.9859 |
| RNN | %1.65 | 0.9678 |
| Transformer | %2.01 | 0.9646 |
| GRU (Standart) | %2.12 | 0.9602 |

> Sonuçlar 1 haftalık test penceresine aittir; modeller ayrıca 1 gün / 1 ay / 3 ay / 1 yıl pencerelerinde de değerlendirilmiştir.

## Özellik Mühendisliği
- 7 bölge ağırlıklı sıcaklık verisi (Open-Meteo API)
- HDD/CDD (18°C baz), dini bayram bayrakları (Ramazan/Kurban + öncesi/sonrası)
- Lag özellikleri (1, 24, 48, 168 saat) ve hareketli istatistikler
- LSTM için univariate seri (168 adım) ile dışsal değişkenleri ayıran Dual-Input mimarisi

## Kullanılan Teknolojiler
Python · TensorFlow/Keras · scikit-learn · XGBoost · pandas · EPTR2 · Open-Meteo · Optuna

## Not
Notebook Google Colab ortamında çalıştırılmak üzere yazılmıştır. Veri dosyaları boyut nedeniyle repoya dahil edilmemiştir; EPTR2 API üzerinden yeniden üretilebilir.
