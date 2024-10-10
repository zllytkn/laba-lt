# California Housing Price Prediction

Bu proje, Kaliforniya'daki konut fiyatlarını tahmin etmek amacıyla basit bir lineer regresyon modelinin uygulanmasını içermektedir. Aşağıda proje adımları ve kullanılan yöntemler hakkında detaylı açıklamalar verilmiştir.

## Veri Seti

- **Veri Seti Kaynağı**:
  - *california_housing.csv* dosyasından yüklenmiştir.

- **Özellikler**:
  - `median_income`: Hanehalkının medyan geliri.
  - `total_rooms`: Bölgedeki toplam oda sayısı.
  - `median_house_value`: Medyan ev değeri (tahmin edilecek hedef değişken).
  - `longitude` ve `latitude` gibi konum bilgileri içeren sütunlar veri analizine dahil edilmemiştir.

Veri setindeki uç değerler (outliers) IQR (Interquartile Range) yöntemi kullanılarak tespit edilip temizlenmiştir. Bu sayede modelin daha sağlıklı bir şekilde eğitilmesi hedeflenmiştir.

## Modelin Eğitimi

- **Model Türü**: Lineer Regresyon
- **Bağımsız Değişkenler**: `median_income`, `total_rooms`
- **Bağımlı Değişken**: `median_house_value`
- **Veri Bölünmesi**: Veriler eğitim (%80) ve test (%20) olarak ikiye ayrılmıştır.

## Uygulanan Adımlar

1. Verinin yüklenmesi ve genel analiz yapılması (`head()`, `info()`, `describe()` komutları kullanılarak).
2. Eksik veriler kontrol edildi ve gerekirse temizleme yapılması planlandı.
3. Uç değerlerin tespiti ve temizlenmesi için IQR yöntemi uygulandı.
4. Lineer regresyon modeli oluşturuldu ve eğitim verisi üzerinde eğitildi.

## Tahminler

- **Test Seti Tahminleri**: Eğitim sonrasında modelin performansı test seti üzerinde değerlendirildi. Test seti üzerindeki tahminlerin, gerçek ev değerlerine yakınlığı ölçüldü ve ortalama mutlak hata (MAE) hesaplandı.

- **Eğitim Seti Tahminleri**: Modelin eğitimdeki başarısını ölçmek amacıyla, eğitim seti üzerinde de tahminler yapıldı ve MAE değeri hesaplandı.

## Sonuçlar

- **Gerçek ve Tahmin Edilen Değerlerin Karşılaştırılması**: Eğitim ve test setlerinde elde edilen tahminlerin gerçek değerlerle karşılaştırılması için iki ayrı grafik oluşturuldu. Bu grafikler, modelin performansını görselleştirmek amacıyla kullanıldı.

- **Test Seti Grafiği**: Gerçek ve tahmin edilen ev değerleri arasındaki dağılımı gösteren bir dağılım grafiği oluşturuldu.

- **Eğitim Seti Grafiği**: Eğitim sırasında modelin ne kadar başarılı olduğunu göstermek için benzer bir grafik kullanıldı.

- **Model Performansının Oransal Gösterimi**: Ortalama Mutlak Hata (MAE) değeri, veri setinin ortalama ev değeriyle karşılaştırılarak yüzdesel olarak da ifade edildi.

## Modelin Performansı

- **Ortalama Mutlak Hata (MAE)**:
  - Test Seti: 55,380.80 USD (%26.71)
  - Eğitim Seti: 55,982.18 USD (%27.05)

- **Yorum**: MAE değerlerinin %10'dan yüksek olması, modelin tahminlerinin gerçekçi olmadığını ve yüksek bir hata payına sahip olduğunu göstermektedir. Bu, modelin daha fazla iyileştirilmesi gerektiğini ve mevcut durumda gerçek dünyadaki kullanımlar için güvenilir olmadığını işaret eder. İyileştirme adına, daha karmaşık modellerin kullanılması, özellik mühendisliği yapılması veya veri setine ek açıklayıcı özelliklerin dahil edilmesi önerilebilir.

## İyileştirme Önerileri

- **Daha Fazla Özellik Kullanımı**: `total_bedrooms`, `population`, `households` gibi ek özelliklerin kullanımı, modelin tahmin doğruluğunu artırabilir.
- **Model Karmaşıklığını Artırma**: Lineer regresyon yerine Random Forest veya Gradient Boosting gibi daha karmaşık modeller kullanılarak hata oranları azaltılabilir.
- **Veri Normalizasyonu**: Özelliklerin farklı ölçeklerde olmasından kaynaklı sapmaların azaltılması için verilerin ölçeklendirilmesi önerilmektedir.
