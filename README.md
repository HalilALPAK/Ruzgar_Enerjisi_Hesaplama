# Rüzgar Enerjisi Tahmin Projesi

Bu proje, hava durumu verilerini kullanarak rüzgar enerjisi üretimini tahmin etmeyi amaçlamaktadır. Verilen bir şehir için hava durumu verileri API aracılığıyla çekilmektedir ve ardından bu veriler, eğitimli bir makine öğrenimi modeli kullanılarak tahminler yapmak için kullanılmaktadır.

## Kullanılan Kütüphaneler

Projede aşağıdaki kütüphaneler kullanılmıştır:

- **Streamlit**: Web tabanlı interaktif arayüz için kullanıldı.
- **Folium**: Harita üzerinde konum ve rüzgar yönünü görselleştirmek için kullanıldı.
- **Requests**: Hava durumu verilerini çekmek için kullanıldı.
- **Pickle**: Eğitimli makine öğrenimi modelini yüklemek için kullanıldı.
- **NumPy**: Veri işleme ve model girişleri için kullanıldı.
- **Scikit-learn**: Model eğitimi ve GridSearchCV ile en iyi hiperparametrelerin bulunması için kullanıldı.

## Proje Açıklaması

Bu projede, rüzgar enerjisi üretimi tahmin etmek için aşağıdaki adımlar izlenmiştir:

1. **Veri Toplama**: Hava durumu verileri, Open Meteo API'si kullanılarak çekildi.
   - **Veri Setinden Alınan Parametreler**:
     - **temperature_2m**: 2 metre yükseklikteki sıcaklık
     - **relativehumidity_2m**: 2 metre yükseklikteki bağıl nem
     - **dewpoint_2m**: 2 metre yükseklikteki çiğ noktası
     - **windspeed_10m**: 10 metre yükseklikteki rüzgar hızı
     - **windspeed_100m**: 100 metre yükseklikteki rüzgar hızı
     - **winddirection_10m**: 10 metre yükseklikteki rüzgar yönü
     - **winddirection_100m**: 100 metre yükseklikteki rüzgar yönü
     - **windgusts_10m**: 10 metre yükseklikteki rüzgar poyrazları
     - **Power**: Rüzgar enerjisi üretimi (hedef değişken)

2. **Veri İşleme ve Özellik Seçimi**: Veri setindeki parametrelerin korelasyonlarına bakılarak en iyi özellikler seçildi.

3. **Model Eğitimi**:
   - **Random Forest Regressor**: Model olarak, rüzgar enerjisi üretimini tahmin etmek için Random Forest algoritması kullanıldı.
   - **GridSearchCV**: Modelin hiperparametrelerini optimize etmek için GridSearchCV kullanıldı. Böylece en iyi parametreler bulundu ve modelin doğruluğu artırıldı.

4. **Tahmin**: Kullanıcıdan alınan şehir bilgisi ve hava durumu verileri doğrultusunda, eğitilmiş model ile rüzgar enerjisi üretimi tahmin edilmiştir.

## Proje Özellikleri

- **Şehir Seçimi ve Hava Durumu Görselleştirmesi**:
  Kullanıcı, bir şehir seçtiğinde, harita üzerinde şehir konumu gösterilmektedir. Ayrıca, API'den alınan hava durumu verileri (sıcaklık, rüzgar hızı, rüzgar yönü, nem) ekranda görüntülenmektedir.
  
- **Rüzgar Yönü ve Harita Üzerinde Ok**:
  Seçilen şehirdeki rüzgar yönü, harita üzerinde bir ok simgesiyle gösterilmektedir. Ok, rüzgarın yönüne göre dönecek şekilde ayarlanmıştır.

- **Rüzgar Enerjisi Tahmini**:
  Kullanıcı, hava durumu verilerine dayalı olarak rüzgar enerjisi üretimi tahmini almak için butona basabilir. Model, tahmin edilen rüzgar enerjisi üretimini kilowatt cinsinden gösterecektir.

## Kullanım

### Gereksinimler

Projenin çalışabilmesi için aşağıdaki kütüphanelerin kurulu olması gerekmektedir:

```bash
pip install streamlit folium requests scikit-learn numpy
