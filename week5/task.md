# Hafta 5 — Backprop Ninja: Gradient'leri Elle Hesaplamak

Bu haftanın konusu geçen hafta kurduğum modelin gradient'lerini `loss.backward()` olmadan, elle hesaplamak. Autograd'ın ne yaptığını anlamanın tek yolu bir kez kendim yapmak.

Bu hafta yük daha dengeli; geçen haftadan tam oturmayan kısımları oturtmak için de zaman var.

> **Kural:** Kodu kendim yazacağım. Kavramlar için AI'a danışabilirim ama kodu AI'a yazdırmak yasak. "Bu ifadenin türevi ne?" diye sormak serbest, gradient kodunu yazdırmak değil.

## Öğrenilecekler
- [ ] Her ara değişkenin gradient'ini elle yazmak ve PyTorch'unkiyle karşılaştırmak
- [ ] Broadcasting'in gradient'e etkisi: toplanan boyut geri dönerken nerede sum alınır
- [ ] Cross entropy ve BatchNorm'un türevlerinin neden tek satıra indiği

## Kaynaklar
- [ ] Andrej Karpathy, "Building makemore Part 4: Becoming a Backprop Ninja": https://www.youtube.com/watch?v=q8SA3rM6ckI
- [ ] Videodaki egzersiz notebook'u: https://github.com/karpathy/nn-zero-to-hero/tree/master/lectures/makemore

## Görevler

### 1. Modeli küçük adımlara böl (Egzersiz 1, videonun ilk yarısı)
- [ ] Geçen haftaki MLP + BatchNorm modelini videodaki gibi küçük adımlara böl (logits, counts, probs, logprobs, ...)
- [ ] `loss.backward()` ile her ara değişkenin gradient'ini al

### 2. Gradient'leri elle yaz
- [ ] Aynı gradient'leri elle yaz
- [ ] `cmp` fonksiyonuyla tek tek karşılaştır
- [ ] Hepsi "exact" ya da "approximate" olana kadar devam et
- (Takıldığım türevi videoda bul, ama önce kendim dene)

### 3. Ek (isteğe bağlı) (Egzersiz 2, 3, 4)
- [ ] Cross entropy'nin geriye yayılımını tek ifadeye indir
- [ ] BatchNorm'un geriye yayılımını tek ifadeye indir
- [ ] Modeli `loss.backward()` olmadan kendi gradient'lerimle eğit

### Hafta 4'ten eksikler
- [ ] Hafta 4'te eksik kalan görevleri `hafta-4` klasörüne tamamlayıp ekle
- [ ] Teslim mailinde "hafta 4'e şunları ekledim" diye yaz

## Teslim
- [ ] Kodu GitHub repoya `hafta-5` klasörü olarak ekle
- [ ] `yz50` kullanıcısı collaborator olarak ekli kalsın
- [ ] Video kaydet: en çok zorlandığım türev ve onu nasıl doğruladığım
- [ ] Repo linkini ve videoyu maile cevap olarak gönder

**Son teslim:** 20 Eylül Pazar 19.00
