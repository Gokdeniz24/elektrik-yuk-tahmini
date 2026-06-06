# Türkiye Kısa Dönem Elektrik Yük Tahmini

Türkiye'nin saatlik elektrik tüketimini kısa dönemde tahmin etmek için geliştirilmiş, derin öğrenme ve makine öğrenmesi modellerinin karşılaştırmalı analizini içeren bitirme tezi çalışması.

## Özet
EPİAŞ Şeffaflık Platformu'ndan (EPTR2 API) çekilen 2017–2025 saatlik tüketim verisi üzerinde beş model karşılaştırıldı. En iyi sonucu **GRU (Dual-Input)** mimarisi verdi (**MAPE %1.13, R² 0.9914**).

## Modeller ve Sonuçlar
| Model | MAPE | R² |
|---|---|---|
| GRU (Dual-Input) | %1.13 | 0.9914 |
| LSTM (Dual-Input) | %1.15 | 0.9913 |
| XGBoost (Optuna) | %1.17 | 0.9864 |
| RNN | %2.09 | 0.9608 |
| Transformer | %4.09 | — |

## Özellik Mühendisliği
- 7 bölge ağırlıklı sıcaklık verisi (Open-Meteo API)
- HDD/CDD (18°C baz), dini bayram bayrakları (Ramazan/Kurban + öncesi/sonrası)
- Lag özellikleri (1, 24, 48, 168 saat) ve hareketli istatistikler
- LSTM/GRU için univariate seri (168 adım) ile dışsal değişkenleri ayıran Dual-Input mimarisi

## Kullanılan Teknolojiler
Python · TensorFlow/Keras · scikit-learn · XGBoost · pandas · EPTR2 · Open-Meteo · Optuna

## Not
Notebook Google Colab ortamında çalıştırılmak üzere yazılmıştır. Veri dosyaları boyut nedeniyle repoya dahil edilmemiştir; EPTR2 API üzerinden yeniden üretilebilir.
