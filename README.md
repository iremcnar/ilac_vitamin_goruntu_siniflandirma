# 🏥 Sağlıkta Yapay Zeka: İlaç ve Vitamin Görüntü Sınıflandırma

Bu proje, **Burdur Mehmet Akif Ersoy Üniversitesi** bünyesindeki **Sağlıkta Yapay Zeka** dersi uygulama çalışmaları kapsamında geliştirilmiştir. Projenin amacı, sentetik görüntüler üzerinden farklı ilaç ve vitamin markalarını derin öğrenme yöntemleriyle otomatik olarak sınıflandırmaktır.

## 📌 Proje Özeti
Eczacılık ve sağlık sektöründe hata payını azaltmak adına ilaçların görsel olarak tanınması büyük önem taşır. Bu projede, 10 farklı ilaç/vitamin kategorisi içeren bir veri seti kullanılarak, önceden eğitilmiş bir model üzerinde transfer öğrenme (transfer learning) teknikleri uygulanmıştır.

**Veri Seti:** [Pharmaceutical Drugs and Vitamins Synthetic Images](https://www.kaggle.com/datasets/vencerlanz09/pharmaceutical-drugs-and-vitamins-synthetic-images)

## 🛠️ Kullanılan Teknolojiler
- **Python** (Veri Bilimi ve Derin Öğrenme)
- **TensorFlow & Keras** (Model mimarisi ve eğitim)
- **MobileNetV2** (Önceden eğitilmiş temel model)
- **Pandas & NumPy** (Veri yönetimi)
- **Matplotlib** (Eğitim süreçlerinin görselleştirilmesi)

## 🚀 Proje Uygulama Adımları

### 1. Veri Yükleme ve Önişleme
- **Görüntü İşleme:** Veriler `ImageDataGenerator` kullanılarak normalize edilmiş ve modelin giriş boyutlarına uygun hale getirilmiştir.
- **Veri Ayrımı:** Görüntüler eğitim ve test setlerine bölünerek modelin görmediği veriler üzerindeki performansı ölçülmüştür.

### 2. Model Mimarisi ve Transfer Learning
Projede hafif ve yüksek performanslı bir mimari olan **MobileNetV2** temel alınmıştır:
- **Transfer Learning:** ImageNet üzerinde eğitilmiş ağırlıklar kullanılarak modelin görsel özellikleri tanıma yeteneğinden faydalanılmıştır.
- **Custom Layers:** Temel modelin üzerine `GlobalAveragePooling2D`, `Dense` (128 nöron, ReLU) ve `Dropout` katmanları eklenerek projeye özgü sınıflandırma katmanı oluşturulmuştur.
- **Çıkış Katmanı:** 10 sınıf için `Softmax` aktivasyon fonksiyonu kullanılmıştır.



### 3. Eğitim ve Optimizasyon
- **Callbacks:** Eğitimi optimize etmek için iki önemli fonksiyon kullanılmıştır:
    - `EarlyStopping`: Modelin aşırı öğrenmesini (overfitting) engellemek için başarı artmadığında eğitimi durdurur.
    - `ModelCheckpoint`: En iyi ağırlıklara sahip modeli otomatik olarak kaydeder.
- **Optimizer:** Model, düşük bir öğrenme oranıyla `Adam` optimizasyon algoritması kullanılarak derlenmiştir.

## 📊 Performans ve Sonuçlar
Model, test verisi üzerinde yüksek bir doğruluk oranına ulaşmıştır. Öne çıkan sonuçlar şunlardır:
- **Accuracy:** Ortalama %84 başarı elde edilmiştir.
- **Sınıf Bazlı Analiz:** `Medicol` ve `Decolgen` gibi sınıflarda %90'ın üzerinde yüksek hassasiyet (precision) değerleri gözlemlenmiştir.
- **Değerlendirme:** `classification_report` ile her ilaç türü için ayrı ayrı F1-skoru ve Recall analizleri yapılmıştır.



## 📂 Dosya Yapısı
- `ilac_vitamin.ipynb`: Veri hazırlama, MobileNetV2 tabanlı model eğitimi ve performans raporlarını içeren ana dosya.
- `Drug and Vitamin Görüntüleri`: Modelin eğitildiği sentetik görüntü klasörleri (Alaxan, Biogesic, Fish Oil, vb.).

---
**Not:** Bu çalışma akademik bir uygulama olup, sentetik veriler kullanılarak geliştirilmiştir. Gerçek tıbbi operasyonlarda profesyonel ekipmanlar ve uzman denetimi gereklidir.
