# 🚁 Optimize Edilmiş Tarım Drone'u Simülasyonu

Bu proje, derin pekiştirmeli öğrenme (Deep Reinforcement Learning) kullanarak **tarım alanında hastalıklı bitki tespiti yapan bir drone ajanı** geliştirmeyi amaçlamaktadır. Proje, Google Colab ortamında çalışacak şekilde hazırlanmış ve Google Drive üzerinden görseller ve modellerle entegre edilmiştir.

---

## 🗺️ Tarım Alanı ve Ortam Yapısı

- **Izgara Boyutu:** 6x6 hücre
- **Hücre Tipleri:**
  - `0`: Boş hücre
  - `1`: Sağlıklı bitki
  - `2`: Hastalıklı bitki
- **Başlangıç Pozisyonu:** (0,0) Şarj istasyonu
- **Hedef:** Tespit edilen tüm hastalıklı bitkiler toplandıktan sonra şarj istasyonuna dönmek

### Görselleştirme
- **Drone:** `drone.png`  
- **Hastalıklı Bitki:** `kirmizi.png`  
- **Boş Hücre:** `bos.png`  
- **Şarj İstasyonu:** `sarj.png`  
- **Tarla:** `tarla.png`  

---

## 🎮 Aksiyonlar

| Kod | Aksiyon               |
|-----|---------------------|
| 0   | Yukarı git           |
| 1   | Aşağı git            |
| 2   | Sola git             |
| 3   | Sağa git             |
| 4   | Şarj istasyonunda şarj |

---

## 🏆 Ödül Sistemi (Optimize Edilmiş)

| Olay                                   | Ödül |
|----------------------------------------|-------|
| Hastalıklı bitkiyi tespit etme          | +100  |
| Göreve tamamladıktan sonra eve dönüş    | +50   |
| Boş hücreyi ziyaret etme                | +10   |
| Sağlıklı bitkiyi ziyaret etme           | +5    |
| Ziyaret edilen hücreyi tekrar ziyaret  | -2    |
| Batarya bittiğinde                        | -50   |
| Başarısız şarj denemesi                  | -10   |
| Şarj olma                                 | +5    |

---

## 🤖 Derin Öğrenme Modeli

- **Model:** AdvancedDroneDQN (Gelişmiş Derin Q-Ağı)
- **Girdi Boyutu:** Ortamın durum vektörü
- **Çıktı Boyutu:** 5 (Aksiyon sayısı)
- **Kayıp Fonksiyonu:** MSELoss
- **Optimizasyon:** Adam, StepLR ile öğrenme oranı güncelleme
- **Replay Buffer:** Deney tamponu ile öğrenme
- **Epsilon-greedy:** Keşif ve sömürü politikası

---

## 🏭 Eğitim Süreci

- **Bölüm Sayısı:** 1500
- **Maksimum Adım Sayısı:** 200
- **İstatistikler:** 
  - Ortalama ödül
  - Hastalıklı tespit oranı
  - Eğitim kaybı
- **Model Kaydı:** Google Drive'da `models/` klasörüne kaydedilir
- **Grafikler:** Ödül, tespit oranı ve kayıp grafikleri kaydedilir ve görüntülenir

---

