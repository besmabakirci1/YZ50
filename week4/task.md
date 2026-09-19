# Hafta 4 — İlk Neural Network Language Model: MLP + BatchNorm

Bu haftanın konusu ilk gerçek neural network language model'im. Tablo yok. Her harfi küçük bir vektöre (embedding) çeviriyorum, önceki üç harfin vektörlerini yan yana koyup geçen hafta kurduğum türden bir MLP'ye veriyorum, model sıradaki harfi tahmin ediyor. Bu Bengio'nun 2003 makalesindeki model.

Haftanın ikinci yarısında bu modeli eğitirken içinde ne olup bittiğine bakıyorum: aktivasyonlar neden doyuyor, init neden önemli, BatchNorm neyi düzeltiyor.

> **Kural:** Kodu kendim yazacağım. Kavramlar için AI'a danışabilirim ama kodu AI'a yazdırmak yasak. Türkçe veri setini büyütmek için veri üretiminde LLM kullanılabilir (ilk distillation).

## Öğrenilecekler
- [ ] Embedding: harfi one-hot vektör yerine öğrenilen küçük bir vektörle temsil etmek
- [ ] Bağlam penceresi: bir harf yerine önceki üç harfe bakan model
- [ ] Minibatch ile eğitim ve learning rate seçimi
- [ ] Train / dev / test ayrımı ve neden gerektiği
- [ ] Tanh saturation: aktivasyonlar 1 ve -1'e yığılınca gradient'in ölmesi
- [ ] Kaiming init: ağırlıkları hangi ölçekte başlatmak gerektiği
- [ ] BatchNorm: aktivasyonları katman katman normalize etmek ve bunun eğitime etkisi

## Kaynaklar
- [ ] Andrej Karpathy, "Building makemore Part 2: MLP": https://www.youtube.com/watch?v=TCH_1BHY58I
- [ ] Andrej Karpathy, "Building makemore Part 3: Activations & Gradients, BatchNorm": https://www.youtube.com/watch?v=P6sfmUTpUmc
- [ ] (İsteğe bağlı) "A Neural Probabilistic Language Model" (Bengio, 2003), Part 2'nin ilk 9 dakikasında anlatılıyor: https://www.jmlr.org/papers/volume3/bengio03a/bengio03a.pdf
- [ ] Karpathy'nin makemore reposu: https://github.com/karpathy/makemore

## Görevler

Görev 1-4 Part 2, görev 5-6 Part 3.

### 1. Veri seti ve embedding (Part 2, 9:03 – 18:35)
- [ ] Önceki üç harfi bağlam alan veri setini kur (X: 3 harf indeksi, Y: sıradaki harf)
- [ ] Embedding tablosunu (27x2) oluştur
- [ ] İndeksleme ile embedding'leri çek

### 2. Gizli katman ve çıkış katmanı (18:35 – 37:56)
- [ ] Embedding'leri düzleştir
- [ ] W1 ve b1 ile tanh (gizli katman)
- [ ] W2 ve b2 ile logits (çıkış katmanı)
- [ ] Loss'u geçen haftaki gibi elle hesapla
- [ ] `F.cross_entropy` ile aynı sonucu aldığını göster
- [ ] Neden `F.cross_entropy`'yi tercih ettiğimizi videodan anla

### 3. Eğitim döngüsü (37:56 – 1:00:49)
- [ ] Önce tek bir minibatch'i overfit et
- [ ] Sonra bütün veriyi minibatch'lerle eğit
- [ ] Learning rate'i videodaki gibi tara, iyi bir değer seç
- [ ] Veriyi train / dev / test olarak böl
- [ ] Loss'u dev üzerinde raporla

### 4. Modeli büyüt ve incele (1:00:49 – 1:13:24)
- [ ] Gizli katmanı büyütüp dev loss'un nasıl değiştiğini göster
- [ ] Embedding boyutunu büyütüp dev loss'un nasıl değiştiğini göster
- [ ] Embedding'leri 2 boyutta çizdir: hangi harfler birbirine yakın düşüyor?
- [ ] Modelden isimler örnekle
- [ ] Bigram'ın ürettikleriyle karşılaştır

### 5. Init sorunları ve Kaiming init (Part 3, 4:19 – 40:40)
- [ ] Başlangıç loss'unun neden çok yüksek olduğunu göster
- [ ] Tanh'ın neden doyduğunu göster
- [ ] Videodaki histogramı çizdir
- [ ] Kaiming init ile ağırlıkları ölçekle
- [ ] İki sorunun da düzeldiğini göster

### 6. BatchNorm (40:40 – 1:04:50)
- [ ] BatchNorm katmanını gizli katmandan sonra ekle
- [ ] Eğitim sırasında batch istatistiğini kullan
- [ ] Tahmin sırasında running mean kullan
- [ ] BatchNorm'lu ve BatchNorm'suz modelin dev loss'unu karşılaştır

> Görev 6'da tıkanırsam 5'e kadar olan kısmı teslim et, nerede kaldığımı yaz.

### 7. Türkçe isimler
- [ ] Geçen haftaki Türkçe isim listesiyle aynı modeli eğit
- [ ] (İsteğe bağlı) Veri setini LLM ile üretilen isimlerle büyüt
- [ ] Türkçe ürettiği isimlerden örnekleri göster
- [ ] Dev loss'u göster
- [ ] Bigram'ın Türkçe sonuçlarıyla yan yana koy

### 8. Ek (erken bitirirsem): birini seç
- [ ] **Part 3, E01:** Bütün weight ve bias'ları sıfırla başlat, ağı eğit, neyin kısmen öğrendiğini gradient ve aktivasyonlardan bul
- [ ] **Part 3, E02:** BatchNorm'u eğitimden sonra bir önceki Linear katmanın W ve b'sine katla, forward pass'in aynı kaldığını göster
- [ ] **Part 2, E01:** Hiperparametreleri ayarlayıp Karpathy'nin 2.2 validation loss'unu geç

## Teslim
- [ ] Kodu GitHub repoya `hafta-4` klasörü olarak ekle
- [ ] `yz50` kullanıcısı collaborator olarak ekli kalsın
- [ ] Video kaydet:
  - [ ] Ne yaptım, nerede zorlandım
  - [ ] BatchNorm neyi düzeltiyor (kod ve grafik üzerinden anlat)
  - [ ] Embedding çizimini göster
  - [ ] Türkçe üretilen isimleri göster
- [ ] Repo linkini ve videoyu maile cevap olarak gönder

**Son teslim:** 13 Eylül Pazar 19.00

---
İki video, toplam 3 saat 10 dakika. Geçen haftadan ağır.
