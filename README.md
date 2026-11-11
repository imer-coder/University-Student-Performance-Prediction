# 🎓 University Student Academic Performance Prediction

**Makine Öğrenmesi | Random Forest | Python | Scikit-learn**

Bu proje, üniversite öğrencilerinin akademik başarılarının farklı öğrenci özellikleri kullanılarak makine öğrenmesi ile tahmin edilmesini amaçlamaktadır.

Çalışmada yalnızca ders çalışma alışkanlıkları değil; önceki akademik başarı, demografik ve sosyoekonomik özellikler de değerlendirilmiştir. Ayrıca modelin hangi değişkenlerden daha fazla yararlandığı ve farklı öğrenci gruplarında nasıl performans gösterdiği incelenmiştir.

## 📌 Proje Hakkında

- **Problem:** Çok sınıflı akademik not tahmini
- **Algoritma:** Random Forest Classifier
- **Veri seti:** Higher Education Students Performance Evaluation
- **Veri kaynağı:** UCI Machine Learning Repository
- **Gözlem sayısı:** 145 öğrenci
- **Hedef değişken:** `OUTPUT Grade`
- **Not sınıfları:** FF, DD, DC, CC, CB, BB, BA, AA

## 🎯 Projenin Amaçları

- Öğrencilerin akademik başarılarını makine öğrenmesi ile tahmin etmek.
- Çalışma alışkanlıkları ve önceki akademik başarının katkısını incelemek.
- Demografik ve sosyoekonomik özelliklerin tahmin performansıyla ilişkisini değerlendirmek.
- Önemli değişkenleri belirlemek.
- Özellik çıkarma deneyleriyle model performansındaki değişimi incelemek.
- Cinsiyet gruplarına göre model performansını karşılaştırmak.
- Sınıf bazlı tahmin başarısını değerlendirmek.

## 🗂️ Veri Seti

Çalışmada UCI Machine Learning Repository tarafından yayımlanan Higher Education Students Performance Evaluation veri seti kullanılmıştır.

Hedef değişkenin sınıfları:

| Kod | Not |
|---:|---|
| 0 | FF |
| 1 | DD |
| 2 | DC |
| 3 | CC |
| 4 | CB |
| 5 | BB |
| 6 | BA |
| 7 | AA |

Veri seti; öğrenci özellikleri, aile ve sosyoekonomik koşullar, çalışma alışkanlıkları ve önceki akademik başarı bilgilerini içermektedir.

## ⚙️ Kullanılan Teknolojiler

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook / Google Colab

## 🔬 Uygulanan Yöntemler

1. Veri setinin incelenmesi ve ön işleme
2. Kategorik değişkenlerin OneHotEncoder ile kodlanması
3. Farklı özellik gruplarının karşılaştırılması
4. Random Forest sınıflandırma modeli
5. GridSearchCV ile hiperparametre optimizasyonu
6. Nested Cross-Validation ile model değerlendirmesi
7. Dummy Classifier ile baseline karşılaştırması
8. Permutation Feature Importance
9. Ablation Study (özellik çıkarma analizi)
10. Cinsiyet gruplarına göre performans değerlendirmesi
11. Confusion Matrix ve sınıf bazlı performans analizi

## 📊 Model Performansı

Nihai 29 değişkenli Random Forest modeli, 5 katlı dış ve 3 katlı iç çapraz doğrulama kullanılarak değerlendirilmiştir.

| Metrik | Nested Random Forest | Dummy Baseline |
|---|---:|---:|
| Accuracy | **0.283** | 0.241 |
| Balanced Accuracy | **0.287** | 0.125 |
| Macro F1 | **0.247** | 0.049 |

Random Forest modeli, üç değerlendirme metriğinde de Dummy Baseline modelinden daha yüksek sonuç elde etmiştir.

Bununla birlikte sonuçlar, akademik notların yüksek doğrulukla tahmin edilebildiğini göstermemektedir.

### Çapraz doğrulama değişkenliği

| Metrik | Standart sapma |
|---|---:|
| Accuracy | 0.099 |
| Balanced Accuracy | 0.111 |
| Macro F1 | 0.091 |

## 🔍 Önemli Değişkenler

Permutation Feature Importance analizinde öne çıkan ilk 10 değişken:

| Değişken | Önem |
|---|---:|
| Scholarship type | 0.0435 |
| Sex | 0.0401 |
| Mother's education | 0.0278 |
| Accomodation type in Cyprus | 0.0242 |
| Previous semester GPA | 0.0232 |
| Weekly study hours | 0.0198 |
| Student Age | 0.0180 |
| Impact of projects/activities | 0.0168 |
| Department seminars attendance | 0.0129 |
| Flip-classroom | 0.0122 |

Bu değerler modelin tahmin performansına dayalı özellik önemini göstermektedir; nedensel etki olarak yorumlanmamalıdır.

## ⚖️ Grup Bazlı Performans

Nested Cross-Validation tahminleri kullanılarak cinsiyet grupları karşılaştırılmıştır.

| Sex | Öğrenci sayısı | Accuracy | Balanced Accuracy | Macro F1 |
|---:|---:|---:|---:|---:|
| 1 | 58 | 0.190 | 0.172 | 0.130 |
| 2 | 87 | 0.345 | 0.293 | 0.250 |

Gruplar arasında performans farkı gözlenmiştir. Bu sonuç tek başına nedensellik veya algoritmik adaletsizlik kanıtı değildir.

## 📉 Sınıf Bazlı Performans

| Not | Precision | Recall | F1-score |
|---|---:|---:|---:|
| FF | 0.278 | 0.625 | 0.385 |
| DD | 0.375 | 0.257 | 0.305 |
| DC | 0.304 | 0.292 | 0.298 |
| CC | 0.333 | 0.286 | 0.308 |
| CB | 0.000 | 0.000 | 0.000 |
| BB | 0.176 | 0.176 | 0.176 |
| BA | 0.091 | 0.077 | 0.083 |
| AA | 0.400 | 0.588 | 0.476 |

Model AA ve FF sınıflarında görece daha yüksek Recall elde ederken CB ve BA sınıflarında zorlanmıştır.

## 📁 Proje Dosyaları

```text
University-Student-Performance-Prediction/
│
├── README.md
├── project_notebook.ipynb
├── report/
│   └── project_report.pdf
└── images/
    ├── confusion_matrix.png
    └── feature_importance.png
```

## ▶️ Projeyi Çalıştırma

1. Bu depoyu bilgisayarına indir veya klonla.
2. Python ortamını hazırla.
3. Gerekli kütüphaneleri yükle.
4. Jupyter Notebook veya Google Colab üzerinden notebook dosyasını aç.
5. Hücreleri sırasıyla çalıştır.

Gerekli kütüphaneler:

```bash
pip install pandas numpy matplotlib scikit-learn jupyter
```

## ⚠️ Sınırlılıklar

- Veri seti 145 öğrenci gözleminden oluşmaktadır.
- Not sınıflarının dağılımı dengeli değildir.
- Bazı not sınıflarında tahmin başarısı oldukça düşüktür.
- Çapraz doğrulama katları arasında performans değişkenliği bulunmaktadır.
- Sonuçlar veri setinin temsil ettiği öğrenci grubuyla sınırlıdır.
- Özellik önemleri nedensel ilişki göstermez.

## 🚀 Gelecek Çalışmalar

- Daha büyük ve farklı üniversiteleri kapsayan veri setleriyle çalışmak.
- Farklı sınıflandırma algoritmalarını karşılaştırmak.
- Sınıf dengesizliğine yönelik yöntemleri araştırmak.
- Modelin grup bazlı performansını daha kapsamlı incelemek.
- Model yorumlanabilirliğini geliştirmek.

## 📚 Kaynak

UCI Machine Learning Repository – Higher Education Students Performance Evaluation.

https://archive.ics.uci.edu/

---

**Bu proje, makine öğrenmesi yöntemleriyle akademik başarı tahminini inceleyen eğitim ve araştırma amaçlı bir çalışmadır. Model sonuçları gerçek öğrenci başarısı hakkında kesin karar vermek için kullanılmamalıdır.**
