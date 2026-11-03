# 🏛️ İstanbul Kültür Varlıkları ve Nüfus Analizi (Power BI & Python)

Bu proje, İstanbul'un tarihi miras yoğunluğunu ve kültürel yapıların günümüze ulaşma oranlarını demografik verilerle harmanlayarak inceleyen kapsamlı bir veri analizi ve iş zekası (BI) çalışmasıdır. 

Proje iki ana aşamadan oluşmaktadır: Python (Pandas/Numpy) ile veri temizleme/keşifsel veri analizi (EDA) ve Power BI ile ilişkisel veri modelleme/görselleştirme.

## 🛠️ Kullanılan Teknolojiler

* **Veri İşleme ve Analiz:** Python, Pandas, Numpy, Jupyter Notebook
* **İş Zekası (BI) ve Modelleme:** Power BI, Power Query, DAX
* **Veri Dönüştürme:** UPPERCASE, Trim, Hata Ayıklama (Error Handling)

## 📊 Veri Setleri

Projede iki farklı veri seti birleştirilerek ilişkisel bir veri modeli (Data Model) kurulmuştur:
1. **İstanbul Kültür Varlıkları Envanteri:** İBB Açık Veri Portalı'ndan alınmış, İstanbul'daki tarihi yapıların türü, dönemi, ilçesi ve kayıp durumlarını içeren ana veri seti.
2. **TUİK İstanbul İlçe Nüfus Verileri:** 2007 ve sonrası için ilçelere göre yaş ve cinsiyet kırılımlı demografik veri seti.

## ⚙️ Proje İş Akışı

### 1. Python ile Veri Hazırlığı
* Eksik verilerin (NaN) tespiti ve yönetimi.
* Vektörel işlemler (`np.where`) ve koşullu mantıksal atamalar.
* Kümülatif toplamlar ve oransal hesaplamalar ile ilk hipotezlerin test edilmesi.

### 2. Power Query ve Veri Modelleme (Data Modeling)
* Her iki veri setindeki ortak anahtar olan **"İlçe"** isimleri, tam eşleşme sağlanması için Power Query üzerinde `UPPERCASE` ve `Trim` işlemleriyle standartlaştırılmıştır.
* Hatalı satırlar temizlenerek veri bütünlüğü sağlanmıştır.
* `kultur_varliklari` ve `nufus_verisi` tabloları arasında İlçe sütunları üzerinden çapraz filtrelemeye (Cross-filtering) olanak tanıyan **Çoka Çok (Many-to-Many)** veri modeli kurulmuştur.

### 3. Power BI Görselleştirme (Executive Dashboard)
Tek sayfalık profesyonel yönetici özetinde şu görseller kullanılmıştır:
* **Decomposition Tree (Ayrıştırma Ağacı):** Kültür varlıklarının ilçelere ve tarihi dönemlere (Osmanlı, Bizans vb.) göre hiyerarşik dağılımını analiz etmek için kullanılmıştır.
* **100% Stacked Bar Chart:** Sivil mimari ile dini yapıların kayıp oranlarını (lost_artifact) karşılaştırmak ve hipotezleri doğrulamak için tasarlanmıştır.
* **Matrix Heatmap & Line/Column Chart:** İlçe nüfusu ile tarihi eser yoğunluğunu aynı eksende çaprazlayarak iki veri setinin etkileşimini kanıtlar.

## 💡 Temel Bulgular ve Hipotez Testleri

* 📌 **Yığılma Hipotezi:** İstanbul'daki tüm tarihi eserlerin %50'sinden fazlası yalnızca üç ilçede (Fatih, Beyoğlu, Üsküdar) kümelenmiştir.
* 📌 **Mimari Dayanıklılık:** Sivil mimari yapılarının (ev, köşk vb.) kayıp oranı, dini yapılara kıyasla istatistiksel olarak çok daha yüksektir. Kentleşmenin bu yapı türü üzerindeki negatif etkisi veriyle kanıtlanmıştır.
* 📌 **Nüfus ve Eser İlişkisi:** En yüksek nüfusa sahip ilçeler ile en yüksek tarihi eser sayısına sahip ilçeler (Fatih hariç) her zaman aynı paralelde ilerlememektedir.

## 🚀 Projeyi Çalıştırma

1. `Python_Analiz/` klasöründeki `.ipynb` dosyasını Jupyter Notebook veya Google Colab üzerinden çalıştırarak veri işleme adımlarını inceleyebilirsiniz.
2. `PowerBI_Dashboard.pbix` dosyasını Power BI Desktop ile açarak interaktif veri modelini ve raporu deneyimleyebilirsiniz.