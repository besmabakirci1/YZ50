# Hafta 3 — İlk Language Model: Bigram

Bu haftanın konusu ilk language model'im. Bigram karakter modeli bir harfe bakıp sıradaki harfi tahmin eder. Önce sayarak kuracağım, sonra aynı modeli tek katmanlı bir sinir ağıyla eğiteceğim. İki yol aynı sonuca çıkacak.

Veri iki aşamalı: görev 1-4'te videoyu Karpathy'nin İngilizce isim listesiyle (`names.txt`) takip edeceğim, görev 5'te aynı modeli internetten bulacağım bir Türkçe isim listesiyle çalıştıracağım.

> **Kural:** Kodu kendim yazacağım. Kavramlar için AI'a danışabilirim ama kodu AI'a yazdırmak yasak. Türkçe isim listesi için de aynı kural: veriyi bulmak ve temizlemek görevin parçası.

## Öğrenilecekler
- [ ] Bigram karakter modeli: bir harften sıradaki harfin olasılığı
- [ ] Sayım tablosunu olasılık dağılımına çevirme ve modelden sampling
- [ ] Negative log likelihood: modelin kalitesini tek sayıyla ölçme, neden bu loss
- [ ] One-hot encoding, logits ve softmax ile olasılığa geçiş
- [ ] Aynı bigram modelinin hem sayımla hem gradient descent ile kurulabildiği
- [ ] Geçen hafta yazdığım `backward()`'ın burada da işin çekirdeği olduğu: PyTorch aynı mekanizmayı tensor'larla çalıştırıyor

## Kaynaklar
- [ ] Andrej Karpathy, "The spelled-out intro to language modeling: building makemore": https://www.youtube.com/watch?v=PaCmpygFfXo
- [ ] Karpathy'nin makemore reposu (takılınca referans, `names.txt` de burada): https://github.com/karpathy/makemore
- [ ] PyTorch broadcasting kuralları (görev 2'de lazım): https://pytorch.org/docs/stable/notes/broadcasting.html

## Görevler

### 1. Bigram'ları say (video 3:03 – 24:02)
- [ ] Karpathy'nin İngilizce `names.txt` dosyasıyla başla
- [ ] Bigram'ları önce Python dictionary ile say
- [ ] Sonra 27x27 torch tensor'da say
- [ ] Tabloyu videodaki gibi görselleştir

### 2. Olasılıklar ve sampling (24:02 – 50:14)
- [ ] Sayım tablosunu satır satır olasılıklara çevir
- [ ] Modelden yeni isimler örnekle
- [ ] Broadcasting'e dikkat: videodaki `keepdim` tuzağı sessizce yanlış model üretir

### 3. Negative log likelihood (50:14 – 1:02:57)
- [ ] Negative log likelihood'u hesapla
- [ ] Smoothing için sahte sayım ekle
- [ ] Neden log, neden negatif, neden ortalama? Teslim videosunda kendi cümlelerimle anlatacağım

### 4. Sinir ağı ile aynı model (1:02:57 – 1:54:31)
- [ ] One-hot input
- [ ] 27x27 weight matrix
- [ ] Softmax
- [ ] NLL loss
- [ ] Gradient descent döngüsü
- [ ] Loss'un görev 3'teki sayım modelinin loss'una yaklaştığını göster
- [ ] (Buradaki `backward()` geçen hafta micrograd'da yazdığım mekanizmanın aynısı)

### 5. Türkçe isimler
- [ ] İnternetten bir Türkçe isim listesi bul (GitHub'da açık kaynak listeler var)
- [ ] Veriyi temizle
- [ ] Alfabeyi Türkçe karakterlerle genişlet (ç, ğ, ı, ö, ş, ü)
- [ ] İki modeli de (sayım + sinir ağı) bu veriyle tekrar koştur
- [ ] Modelin ürettiği isimlerden örnekleri ve loss'u göster

### 6. Ek (erken bitirirsem): Trigram
- [ ] Modeli trigram'a çevir (iki önceki harfe bak)
- [ ] Veriyi train/dev/test olarak %80/%10/%10 böl
- [ ] Smoothing gücünü dev loss'una göre ayarla
- [ ] Bigram ile trigram loss'unu karşılaştır
- [ ] Ürettiği isimlerin nasıl değiştiğini göster
- (Videoda bunun kodu yok, Karpathy sonunda egzersiz olarak veriyor)

## Teslim
- [ ] Kodu GitHub repoya `hafta-3` klasörü olarak ekle
- [ ] `yz50` kullanıcısı collaborator olarak ekli kalsın
- [ ] Video kaydet:
  - [ ] Ne yaptım, nerede zorlandım
  - [ ] Negative log likelihood neden bu işin loss'u (kod üzerinden anlat)
  - [ ] Türkçe veriyle üretilen isimlerden örnekler göster
- [ ] Repo linkini ve videoyu maile cevap olarak gönder

**Son teslim:** 6 Eylül Pazar 19.00

---
Video yaklaşık 2 saat. Bu hafta geçen haftadan daha hafif.
