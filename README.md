https://yz50.ai

## **Understanding Neural Network and Backpropagation Algorithm**

  * *(English)*

    1. [The Perceptron Explained](https://youtu.be/i1G7PXZMnSc?si=45-LrjEc2QzKhU2W)
    2. [But what is a neural network? | Deep learning chapter 1](https://youtu.be/aircAruvnKk?si=xkoGPEReRLA_UZ56)
    3. [Gradient descent, how neural networks learn | Deep Learning Chapter 2](https://youtu.be/IHZwWFHWa-w?si=ilfRwZx-0I8Fniu8)
    4. [Backpropagation, intuitively | Deep Learning Chapter 3](https://youtu.be/Ilg3gGewQ5U?si=uBw90JvWbqI09VZD)
  * *(Turkish)*

    1. [Neural Network 1 : Eğitime ve Kavramlara Giriş](https://youtu.be/B5MmXmMMuvI?si=JZ4Yfmc_MdsxPyhU)
    2. [Neural Network 2: Perceptron Kavramı ve Öğrenme](https://youtu.be/5Lo_HUDtxtw?si=DuZ1y9W11aRfIvrd)
    3. [Neural Network 3: Çok Katmanlı Yapay Sinir Ağları](https://youtu.be/qrmaixHBrzU?si=sXHsC0A5XaXsJZId)

### 1. Nöron Nedir? ⚙️
- **Tanım:** Sayı tutan birimdir ve her nöron 0–1 arası bir aktivasyon değeri taşır.  
- **Giriş katmanı:** 784 nöron (28×28 piksellik her piksel için bir nöron)

### 2. Aktivasyon Nedir? 🌟
- **Tanım:** Pikselin gri ton değeridir (0 = siyah, 1 = beyaz).  
- **Anlamı:** Yüksek aktivasyon = o nöron “parlak” (aktiftir)

### 3. Problemin Tanımı 🧐
28×28 piksellik düşük çözünürlüklü el yazısı rakam görüntülerini (örneğin “3”) bilgisayarla otomatik tanımanın ne kadar zor olduğunu vurguluyor.  
> **İnsan Beyni–Bilgisayar Karşılaştırması:** İnsan görsel korteksi bu görevi zorlanmadan çözer; bilgisayarda ise “komik derecede” karmaşık hale gelir.

### 4. Öğrenme (Learning) Kavramı 🚀
Soyut bir şeyi somutlaştırmak sonucu gerçekleşir.  
**Amaç:** On binlerce parametrenin “doğru” değerlerini otomatik ve hızlı bir şekilde bulmak.


### 5. Soyutlama Düzeyleri 🏗️
- **Giriş Katmanı (Input Layer):** Ham pikseller. 784 nöron.  
- **Gizli Katmanlar (Hidden Layers):** Kenar, köşe, döngü gibi alt-bileşenler.  
  - Örnekte iki gizli katman, her biri 16 nöron.  
- **Çıkış Katmanı (Output Layer):** Bileşen kombinasyonlarından rakam tanıması. 10 nöron (0–9).  

> **Genel Amaç:** Aynı yapı, farklı görüntü ve ses tanıma görevlerine de uyarlanabilir.

### 6. İleri Besleme Mekanizması 🔄
- Her gizli katmandaki nöron, önceki katmandaki tüm nöronların aktivasyonlarıyla “bağlantılıdır”.  
- **Ağırlık (weight):** Sinyallerin gücünü belirler.  
- **Bias:** Nöronun “ne zaman” aktif olacağını kontrol eden eşik ayarı.  

> Eğitim aşamasında bias ve weight parametreleri gradient descent ile otomatik olarak ayarlanır.

### 7. Parametre Hesabı 📊
- Her katman atlaması için *önceki katmandaki nöron sayısı* × *sonraki katmandaki nöron sayısı* kadar bağlantı (weight).  
- **Aktivasyon fonksiyonu:** Toplam sonucu 0–1 aralığına sıkıştırmak (sigmoid veya ReLU).  
- **Toplam parametre sayısı:** weight sayısı + bias sayısı.  

| Geçiş                          | Önceki katman | Sonraki katman | Ağırlık Matrisi Boyutu | Ağırlık sayısı   | Bias sayısı | Parametre | Bias vektörü boyutu | Ara Toplam |
| ------------------------------ | ------------- | -------------- | ---------------------- | ---------------- | ----------- | --------- | ------------------- | ---------- |
| Giriş → 1. Gizli katman        | 784 nöron     | 16 nöron       | (16, 784)              | 784 × 16 = 12 544 | 16          | 12 560    | (16, 1)             | 12 560     |
| 1. Gizli katman → 2. Gizli katman | 16 nöron  | 16 nöron       | (16, 16)               | 16 × 16 = 256     | 16          | 272       | (16, 1)             | 272        |
| 2. Gizli katman → Çıkış        | 16 nöron      | 10 nöron       | (10, 16)               | 16 × 10 = 160     | 10          | 170       | (10, 1)             | 170        |
| **Genel Toplam**               |               |                |                        | **12 960**        | **42**      | **13 002**|                     | **13 002** |


### 8. Backpropagation’ın Amacı 🎯
- **Amaç:** Hangi ağırlık, hatayı ne kadar etkiliyor?  
- **Hedef:** Modelin tahmin hatasını (maliyeti) en aza indirmek.  
> **Özet:** Tahmin → Hata → Gradyan → Güncelleme

![Gradient Descent](https://github.com/user-attachments/assets/fc6ecc38-c3a6-4a49-ae62-0e28e6e3a4bf)
<caption><b>Şekil 1.</b> Gradyan yönünde (türev işareti boyunca) küçük adımlarla ağırlıkların güncellenmesi ve maliyetin (cost) en aza indirilmesi.</caption>

### 9. Adım Adım İşleyiş 🚶‍♀️
| Adım | Ne Yapıyoruz?                                                                                 |
| ---- | --------------------------------------------------------------------------------------------- |
| 1    | **Tahmin (Forward Pass):** Girdiyi ağdan geçirip çıktı değerini hesaplıyoruz.                  |
| 2    | **Hata Hesaplama (Loss):** Tahmin ile gerçek etiket arasındaki farkı ölçüyoruz (örn. kare fark). |
| 3    | **Geri Yayılım (Backprop):** Hatanın her ağırlığa ne kadar etki ettiğini belirliyoruz.         |
| 4    | **Ağırlık Güncelleme:** Ağırlıkları, hatayı azaltacak yönde küçük adımlarla güncelliyoruz.      |

### 10. Basit Örnek Görseliyle 🖼️
- **Girdi:** `[x₁, x₂]`  
- **Ağırlıklar:** `[w₁, w₂]`, **Bias:** `b`  
- **Hesap:** `z = w₁·x₁ + w₂·x₂ + b` → `a = sigmoid(z)`  
- **Hata:** `(a − y)²` (`y` = gerçek etiket)  
- **Geri Yayılım:** Hangi `w₁` veya `w₂` değişirse hata ne kadar değişir?  
- **Güncelleme:** `w ← w − η·(etki)` (`η` = öğrenme hızı)

### 11. Döngüyü Tekrarlama 🔁
Her veri noktası veya mini-batch için:  
1. Tahmin  
2. Hata Hesaplama  
3. Geri Yayılım  
4. Ağırlık Güncelleme  

> Bu dört adım tekrarlanarak ağ “öğrenir” ve tahmin doğruluğu artar.


![Loss Landscape](https://github.com/user-attachments/assets/444665a0-637e-4487-b34c-ff7d31048697)
<caption><b>Şekil 2.</b> Çok boyutlu kayıp yüzeyinde (loss landscape) optimizasyonun izlediği yol; yerel minimumlar, eyer noktaları ve zor bölgeler.</caption>



#### 📚 Ek Kaynaklar
- **Ian Goodfellow, Yoshua Bengio & Aaron Courville** – *Deep Learning* (MIT Press, 2016)  
  Resmî web sitesi ve PDF: https://www.deeplearningbook.org/  
- **Michael Nielsen** – *Neural Networks and Deep Learning* (online kitap, 2015)  
  Etkileşimli alıştırmalar: https://neuralnetworksanddeeplearning.com/  
- **Stanford CS231n** – *Convolutional Neural Networks for Visual Recognition*  
  Ders notları: http://cs231n.stanford.edu/  
  Video dersleri: https://www.youtube.com/playlist?list=PL3FW7Lu3i5JvHM8ljYj-zLfQRF3EO8sYv  
----

2. hafta öğrenilenler:
- Chain rule (zincir kuralı) sezgisi
- Computation graph: her işlem bir node, gradient çıktıdan girdiye doğru akar
- Backward pass: her node kendi local derivative'ini üstten gelen gradient ile çarpar
- Analitik gradient'in numerical derivative ile doğrulanması
- PyTorch'taki autograd'ın çekirdeğinde de aynı mekanizmanın olduğu
