# Müşteri Ayrılma Tahmini (Churn Prediction) ile Temel Makine Öğrenmesi Akışı

## 🎯 Projenin Amacı
Bu proje, **Türkiye Yapay Zeka Akademisi & HUAWEI** iş birliğiyle düzenlenen Veri Bilimi ve Makine Öğrenmesi Bootcamp'i kapsamında geliştirilmiştir. Projenin temel amacı, gerçek hayat senaryolarına uygun (kirli, eksik ve aykırı değerler barındıran) sentetik bir müşteri veri seti simüle etmek ve bu veri üzerinde uçtan uca (End-to-End) bir veri ön işleme ile makine öğrenmesi pipeline'ı inşa etmektir.

---

## 🛠️ Proje İş Akışı Adımları

### 1. Sentetik Veri Seti Oluşturma
* Gerekli kütüphanelerin içe aktarılması
* Veri setinin hazırlanması
* Veri setine eksik değer (NaN) ve aykırı değer (outlier) eklenmesi
* Veri setine hatalı veri eklenmesi
* Veri setinin CSV dosyası olarak kaydedilmesi

### 2. Veri Setinin Düzenlenmesi ve Keşifsel Veri Analizi (EDA)
* Veri setinin içe aktarılması
* Veri setinin ilk 4 ve rastgele 7 satırının incelenmesi
* Veri setinin boyutunun ve sütun isimlerinin kontrol edilmesi (Standart snake_case dönüşümleri)
* Veri setinin genel bilgisinin ve veri tiplerinin kontrol edilmesi
* Tekrar eden (mükerrer) kayıtların tespit edilmesi
* Eksik değerlerin (NaN) kontrol edilmesi (Simetrik dağılıma göre Median Imputation uygulaması)
* Özet istatistiklerin görüntülenmesi (Negatif gelir ve uç değer kirliliklerinin tespiti)
* Veri setindeki özelliklerin sayısal ve kategorik olarak ayrılması
* Aykırı ve tutarsız değerlerin incelenmesi (IQR - Interquartile Range analizi ve izolasyon)
* Sütunlardaki benzersiz (unique) değer yapılarının ve sınıf dağılımlarının incelenmesi (Kategorik kirliliklerin .strip() ve .replace() ile temizlenmesi)
* Dağılımların grafiksel (Histogram ve Bar) incelenmesi
* Korelasyon analizi ile değişkenler arasındaki ilişkilerin incelenmesi (Heatmap)

### 3. Makine Öğrenmesi Modelleri
* Bağımlı ve bağımsız değişkenlerin tanımlanması, veri sızıntısını (Data Leakage) önleyecek şekilde %20 Stratify ve Random State=42 ile train/test ayrımı
* Kategorik değişkenlere uygun OneHotEncoder (Kukla Değişken Tuzağı önlemli) uygulanması
* Sayısal değişkenlerin StandardScaler ile ölçeklendirilmesi
* 5 farklı modelin (Logistic Regression, KNN, Decision Tree, Random Forest, SVM) for döngüsü ile eğitilmesi, hata matrislerinin (Confusion Matrix) çizilmesi ve karşılaştırılması
* GridSearchCV ile 5-Fold Cross-Validation kullanılarak Hiperparametre Optimizasyonu yapılması ve nihai model başarılarının raporlanması
* En iyi Random Forest modeli üzerinden "Öznitelik Önem Dereceleri" (Feature Importances) analizi

---

## 📈 Model Başarı Sonuçları (GridSearchCV Sonrası)

| Model | Tuned Accuracy | Tuned Precision | Tuned Recall | Tuned F1-Score |
| :--- | :---: | :---: | :---: | :---: |
| **Logistic Regression** | %90.00 | %95.45 | %84.00 | %89.36 |
| **KNN (K-Nearest Neighbors)** | %90.00 | %91.67 | %88.00 | %89.80 |
| **Decision Tree** | %88.00 | %91.30 | %84.00 | %87.50 |
| **Random Forest** | %88.00 | %88.00 | %88.00 | %88.00 |
| **SVM (Support Vector Machine)** | %86.00 | %90.91 | %80.00 | %85.11 |

---

## 📦 Kullanılan Kütüphaneler ve Versiyonları
Projenin tekrarlanabilirliği (reproducibility) için kullanılan kütüphane versiyonları aşağıda belirtilmiştir ve `requirements.txt` dosyasında sabitlenmiştir:
*   **Pandas** : 2.3.3
*   **NumPy** : 2.2.6
*   **Matplotlib** : 3.10.9
*   **Seaborn** : 0.13.2
*   **Scikit-Learn** : 1.7.2
