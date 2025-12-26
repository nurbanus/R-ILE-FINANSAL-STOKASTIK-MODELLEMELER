ZIP DOSYASINI İNDİREREK KULLANILAN VERİ SETLERİNE , KODLARA VE RAPORA ULAŞABİLİRSİNİZ.

#### Proje Özeti
Bu proje, EUR/USD ve BTC/USD finansal varlıklarının fiyat ve getiri serileri üzerinden stokastik süreçler kullanılarak analiz edilmesini kapsamaktadır. Çalışmada, finansal varlıkların uç değer davranışları (Extreme Value Theory), portföy optimizasyonu ve Markov Zincirleri ile gelecek dönem fiyat hareketlerinin olasılıkları incelenmiştir. Analizler R Programlama Dili kullanılarak gerçekleştirilmiştir.

#### Veri Seti
Projede iki temel veri seti kullanılmıştır:

EUR/USD (Forex): 2005-2020 yılları arasındaki saatlik Açılış (BO), Yüksek (BH), Düşük (BL) ve Kapanış (BC) fiyatları.

BTC/USD (Kripto): Bitcoin'in saatlik fiyat verileri.

#### Kullanılan Yöntemler ve Analizler
#### Temel İstatistikler ve Görselleştirme
Veri setinde eksik değer kontrolü yapılmış ve temizlenmiştir.

Zaman serisi grafikleri ile 2008 krizi, 2010-2015 dalgalanmaları gibi makroekonomik olayların fiyat üzerindeki etkileri gözlemlenmiştir.

Logaritmik getirilerin histogramı çizilerek dağılımın normale yakın ancak uç değerler (fat tails) barındırdığı tespit edilmiştir.

#### Uç Değer Teorisi (Extreme Value Theory - EVT)
Finansal riskleri (beklenmedik büyük kayıpları/kazançları) modellemek için iki yöntem karşılaştırılmıştır:

Eşiği Aşan Değerler (Peaks Over Threshold - POT): Genelleştirilmiş Pareto Dağılımı (GPD) denenmiş ancak model uyumu (QQ plot diyagonalden uzak) düşük bulunmuştur.

Blok Maksima Yöntemi (Block Maxima): Aylık maksimum değerler üzerinden Genelleştirilmiş Ekstrem Değer (GEV) dağılımı uygulanmıştır.

Sonuç: GEV dağılımı veriye istatistiksel olarak uygun bulunmuştur (p-value < 0.05).

Geri Dönüş Seviyeleri (Return Levels): 2, 5 ve 10 yıllık periyotlarda görülebilecek maksimum risk seviyeleri hesaplanmıştır (Örn: 5 yılda bir 1.3973 seviyesinin aşılması beklenmektedir).

#### Portföy Analizi
EUR/USD ve BTC/USD varlıklarından oluşan eşit ağırlıklı (%50-%50) bir portföy oluşturulmuştur:

Risk/Getiri: Portföy varyansı ve standart sapması tekil varlıklara göre daha düşük çıkmıştır, bu da portföy oluşturmanın riski azalttığını (diversification benefit) kanıtlamıştır.

Korelasyon: İki varlık arasındaki korelasyon katsayısı -0.047 (neredeyse sıfır) olarak hesaplanmıştır. Bu durum, varlıkların birbirinden bağımsız hareket ettiğini ve risk çeşitlendirmesi için mükemmel bir ikili olduklarını göstermektedir.

#### Markov Zincirleri (Markov Chains)
Fiyat hareketleri "Up" (Artış), "Down" (Azalış) ve "Stable" (Sabit) olmak üzere üç duruma ayrılmış ve stokastik geçişler modellenmiştir:

Geçiş Matrisi (Transition Matrix): Bir sonraki adımda fiyatın yönünü tahmin etmek için 3x3'lük olasılık matrisi oluşturulmuştur.

Denge Dağılımı (Steady States): Uzun vadede piyasanın %49.35 "Down", %49.87 "Up" durumunda olacağı hesaplanmıştır. "Stable" durumu (%0.79) piyasanın sürekli hareket halinde olduğunu göstermektedir.

Tahmin: Fiyatı düşen ("Down") bir varlığın 3 dönem sonra fiyatının artma ("Up") olasılığı %49.9 olarak hesaplanmıştır.

#### Kullanılan R Kütüphaneleri
Analiz sürecinde aşağıdaki kütüphanelerden yararlanılmıştır:

evd, fExtremes, extremes (Uç Değer Analizi)

PerformanceAnalytics, quantmod, zoo (Finansal Analiz ve Portföy)

markovchain, diagram, expm (Markov Zincirleri)

ggplot2, pheatmap, corrplot (Görselleştirme)

Bu çalışma, finansal serilerin rassal davranışlarını modellemek ve risk yönetimi stratejileri geliştirmek amacıyla akademik bir ödev kapsamında hazırlanmıştır
