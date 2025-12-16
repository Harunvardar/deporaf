.

 Akıllı Depo Raf Yerleşimi Optimizasyonu (Genetik Algoritma)
Bu proje, bir lojistik firmasının akıllı deposundaki raf yerleşimini optimize etmek için Genetik Algoritma (Genetic Algorithm) yöntemi kullanılarak geliştirilmiştir. Hazır optimizasyon kütüphaneleri yerine, evrimsel süreç (seçilim, çaprazlama, mutasyon) "Pure Python" ile sıfırdan kodlanmıştır.


🎯 Problem Tanımı
Amaç, aşağıdaki değişkenlere ve kısıtlara bağlı olarak depo verim puanını maksimize etmektir.

Amaç Fonksiyonu (Fitness Function):

y=4x 
1
​
 +3x 
2
​
 −0.5x 
1
​
 x 
2
​
 
Değişkenler (Genler):

x 
1
​
  (Raf Yüksekliği): [2,6] metre aralığında.

x 
2
​
  (Raf Derinliği): [1,4] metre aralığında.

Kısıtlar (Constraints):

Alan Sınırı: x 
1
​
 +x 
2
​
 ≤8 (Tavan yüksekliği limiti).

Güvenlik Sınırı: x 
2
​
 ≥1.5 (Minimum derinlik).

 Algoritma Mantığı ve Kod Mimarisi
Bu projede doğadaki evrim süreci taklit edilmiştir. Kodun çalışma prensibi adım adım şöyledir:

1. Popülasyon Başlatma (Initialization)
Rastgele belirlenen raf ölçülerinden (x 
1
​
 ,x 
2
​
 ) oluşan 20 bireylik bir popülasyon yaratılır.

Özellik: Oluşturulan her birey check_constraints fonksiyonu ile kontrol edilir. Kısıtları sağlamayan bireyler (örneğin toplamı 8 metreyi geçenler) popülasyona alınmaz.

2. Uygunluk (Fitness) Hesabı
Her bireyin başarısı, fitness_function ile hesaplanan depo verim puanıdır. Puanı yüksek olan raf tasarımı, hayatta kalma şansı yüksek olandır.

3. Seçilim (Selection) - Turnuva Yöntemi
Yeni neslin ebeveynlerini seçmek için Turnuva Seçilimi (Tournament Selection) kullanılmıştır. Rastgele seçilen 3 bireyden en yüksek puana sahip olan, genlerini aktarmaya hak kazanır.

4. Çaprazlama (Crossover)
Seçilen iki ebeveynin genleri Aritmetik Çaprazlama yöntemi ile karıştırılır.

Formül:  
C
\c
​
 ocuk=α⋅Anne+(1−α)⋅Baba

Bu işlem sayesinde ebeveynlerin iyi özelliklerinin çocuklara aktarılması hedeflenir.

5. Mutasyon (Mutation)
Yerel optimum tuzağına düşmemek ve genetik çeşitliliği artırmak için, her yeni birey %10 ihtimalle mutasyona uğrar. Genlerinde (boyutlarında) rastgele ufak oynamalar yapılır.

 Sonuçlar
50 nesil süren evrimsel simülasyon sonucunda algoritma şu optimal değerlere yakınsamıştır:

Optimal Raf Yüksekliği (x 
1
​
 ): ~6.00 m

Optimal Raf Derinliği (x 
2
​
 ): ~2.00 m

Maksimum Verim Puanı: ~24.00




📈 Gelişim Grafiği
Kod çalıştırıldığında, nesiller boyunca en iyi fitness değerinin nasıl arttığını gösteren bir grafik üretmektedir. Bu grafik, algoritmanın öğrenme sürecini kanıtlar.
