# Hafta 2 — Backpropagation

Bu haftanın konusu backpropagation. Geçen hafta türevleri tek tek, sayısal olarak hesapladık. Bu hafta hepsini tek bir geriye geçişte hesaplayan mekanizmayı kuracağız: Karpathy'nin micrograd kütüphanesinin küçük bir versiyonunu kendim yazacağım.

> **Kural:** Kodu kendim yazacağım. Kavramlar için AI'a danışabilirim ama kodu AI'a yazdırmak yasak.

## Öğrenilecekler
- [ ] Chain rule (zincir kuralı) sezgisi
- [ ] Computation graph: her işlem bir node, gradient çıktıdan girdiye doğru akar
- [ ] Backward pass: her node kendi local derivative'ini üstten gelen gradient ile çarpar
- [ ] Analitik gradient'i numerical derivative ile doğrulamak
- [ ] PyTorch autograd'ın çekirdeğinde de aynı mekanizmanın olduğu

## Kaynaklar
- [ ] Andrej Karpathy, "The spelled-out intro to neural networks and backpropagation" (videonun tamamı): https://www.youtube.com/watch?v=VMj-3S1tku0
- [ ] Karpathy'nin micrograd reposu (takılınca referans): https://github.com/karpathy/micrograd
- [ ] 3Blue1Brown, "What is backpropagation really doing?": https://www.youtube.com/watch?v=Ilg3gGewQ5U
- [ ] 3Blue1Brown, "Backpropagation calculus": https://www.youtube.com/watch?v=tIeHLnjs5U8

## Görevler

### 1. Value sınıfı (video 19:09 – 32:10)
- [ ] Toplama ve çarpma ile başlayan bir `Value` sınıfı yaz
- [ ] Her yeni Value, kendisini üreten Value'ları ve hangi işlemden çıktığını saklasın
- [ ] (İsteğe bağlı) Computation graph'i graphviz ile çizdir

### 2. Gradient'leri elle doldur (32:10 – 51:10, 52:52 – 1:09:02)
- [ ] Basit ifadede gradient'leri elle doldur (32:10 – 51:10)
- [ ] `Value`'ya `tanh` ekle
- [ ] Tek neuron örneğinde gradient'leri elle doldur (52:52 – 1:09:02)

### 3. backward() (1:09:02 – 1:27:05)
- [ ] Çıktının gradient'ini 1 yap
- [ ] Node'ları ters topological sırayla gez
- [ ] Her node'da chain rule uygula
- [ ] Bir değişken birden fazla yerde kullanılıyorsa gradient'leri topla (`+=`), üzerine yazma

### 4. tanh'ı parçala ve doğrula (1:27:05 – 1:43:55)
- [ ] `exp`, bölme ve `pow` operasyonlarını ekle
- [ ] Parçalanmış tanh ile aynı gradient'lerin çıktığını göster
- [ ] Aynı ifadeyi aynı değerlerle üç yolla hesapla:
  - [ ] `backward()`
  - [ ] Geçen haftaki numerical derivative
  - [ ] PyTorch
- [ ] Üçünün eşleştiğini göster (eşleşmiyorsa nedenini bul)

### 5. Neuron, Layer, MLP (1:43:55 – 2:14:03)
- [ ] Videodaki sırayla `Neuron`, `Layer`, `MLP` sınıflarını kur
- [ ] Parametreleri tek listede topla
- [ ] Videodaki küçük veri setiyle eğit
- [ ] Loss'un adım adım düştüğünü göster
- [ ] Her adımda gradient'leri sıfırla (videodaki meşhur bug)

> Görev 5'te tıkanırsam 4'e kadar olan kısmı teslim et, nerede kaldığımı yaz. Bitiremeden anlayarak gelmek, kopyalayıp bitirmekten değerli.

## Teslim
- [ ] Kodu GitHub repoya `hafta-2` klasörü olarak ekle
- [ ] `yz50` kullanıcısı collaborator olarak ekli kalsın
- [ ] Video kaydet: ne yaptım, nerede zorlandım, `backward()` nasıl çalışıyor (kod üzerinden anlat)
- [ ] Repo linkini ve videoyu maile cevap olarak gönder

**Son teslim:** 29 Ağustos Cumartesi 19.00

---
Tahmini süre: 10–15 saat (video 2.5 saat, durdurup yazarak izleyince daha uzun sürüyor).
