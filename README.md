# 🚕 Taksi Ortamı ile Q-Öğrenme Eğitimi

## 🗺️ Harita ve Engeller
Harita, görselden (`taksi.png`) alınmıştır.  

- **Kırmızı hücreler 🚫** ve **kahverengi tuğla duvarlar 🧱** geçilemez alanlar olarak belirlenmiştir.  
- Bu engeller, eğitim ortamını hazırlamak için otomatik olarak tespit edilir.  

## 🧩 Ortamın Yapısı (CustomTaxiEnv)
- **Izgara:** 10x10 hücre, her biri 50x50 piksel boyutunda  
- **Özellikler:**  
  - Taksi 🟡 özel bir ikonla temsil edilir  
  - Yolcu 🧍 özel bir ikonla gösterilir  
  - Hedef 🟩 yeşil bir kareyle belirtilir  
  - Geçilemez alanlar 🔴 kırmızı veya kahverengi olarak görselleştirilir  

- **Durum (state):**  
(taksi_x, taksi_y, yolcu_x, yolcu_y, yolcu_taksidemi)


## 🎮 Aksiyonlar
| Aksiyon Kodu | Açıklama           |
|--------------|------------------|
| 0            | Yukarı git       |
| 1            | Aşağı git        |
| 2            | Sola git         |
| 3            | Sağa git         |
| 4            | Yolcuyu al (pick up) |
| 5            | Yolcuyu bırak (drop) |

## 🏆 Ödül Sistemi
| Olay                        | Ödül |
|-----------------------------|------|
| Yolcuyu doğru yerde alma     | +10  |
| Yolcuyu doğru yerde bırakma | +20  |
| Yanlış pick/drop            | -10  |
| Her adım                    | -1   |

## 👁️ Görselleştirme (Render)
- Yolcu taksideyse:  
- Taksinin etrafına kırmızı çember çizilir  
- Yolcunun alındığı yere kırmızı "X" çizilir  

- Yolcu dışarıdaysa:  
- Yolcu ikonu gösterilir  

- Hedef:  
- Yeşil bir kutu olarak görünür  

- Taksi:  
- Taksi ikonu her zaman görünür  

## 🤖 Q-learning Eğitimi
- Toplam **500 epoch** boyunca eğitim yapılır  
- Aksiyonlar rastgele keşfedilir veya Q-table’dan seçilir  
- Her adımda Q-table aşağıdaki formül ile güncellenir:  

```python
Q(s, a) ← (1 - α) * Q(s, a) + α * [r + γ * max Q(s', a')]

### Not: Bu çalışma Google Colab üzerinde yapılmış ve taksi adlı klasörde, Google Drive'da kaydedilmiştir.
