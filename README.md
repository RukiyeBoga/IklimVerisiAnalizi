#            İklim Verisi Üzerinde Veri Analizi ve Makine Öğrenmesi Modeli
Bu projede, iklim verilerini kullanarak keşifsel veri analizi (EDA) ve makine öğrenmesi modellemesi yapılmıştır. Proje, Türkiye'nin farklı şehirlerinden alınan hava durumu verilerini incelemeyi amaçlamaktadır. Amacımız, verinin genel özelliklerini anlamak, modelleme için uygun hale getirmek ve ardından çeşitli makine öğrenmesi algoritmalarıyla hava durumu tahminleri yapmaktır.

# Veri Keşfi ve Hazırlığı:

Veriyi anlamak için çeşitli histogramlar ve korelasyon matrisleri oluşturulmuştur. Bu adımda verinin dağılımı, ilişkiler ve eksik veriler incelenmiştir.

Histogram matrisleri:

•  Sıcaklık Değerleri: Minimum, ortalama ve maksimum sıcaklık değerlerinin dağılımları benzer bir eğilim göstermektedir. Sıcaklıkların belirli bir aralıkta yoğunlaştığı ve bu aralığın dışında daha az veri olduğu görülmektedir.

•  Yağış (msn): Yağış miktarının büyük bir kısmının sıfır civarında olduğu, yani yağışlı günlerin daha az olduğu anlaşılmaktadır. 

•  Nem: Nem değerlerinin de belirli bir aralıkta yoğunlaştığı ve bu aralığın dışında daha az veri olduğu görülmektedir. 

•  Basınç (hPa): Basınç değerleri de sıcaklık değerleri gibi belirli bir aralıkta yoğunlaşmaktadır. 

•  Saat: Saat verisinin dağılımı, günün farklı saatlerindeki ölçümlerin sayısını göstermektedir. 

•  Rüzgar Hızı (kws): Rüzgar hızının düşük olduğu günlerin daha fazla olduğu anlaşılmaktadır. 


![image](https://github.com/user-attachments/assets/e3275f00-6f04-41e3-aac0-482022b34fad)

Kolerasyon matrisi: 

Sıcaklık Değişkenleri Arasındaki İlişki: min_c, ort_c ve mak_c gibi sıcaklık değişkenleri arasında çok yüksek bir korelasyon gözlemleniyor. Bu beklenen bir durum, çünkü minimum, ortalama ve maksimum sıcaklıklar genellikle benzer şekilde değişir ve birlikte hareket ederler.

Sıcaklık ile Zaman Arasındaki İlişki: Sıcaklık değişkenleri ile saat arasındaki ilişki de dikkat çekiyor. Bu, günün farklı saatlerinde sıcaklıkların farklı şekilde değiştiği anlamına geliyor. Yani sabah, öğle ve akşam saatlerinde sıcaklıklar değişiklik gösteriyor.

Nem ve Basınç Arasındaki İlişki: Nem ile hava basıncı (hPa) arasında negatif bir korelasyon var. Bu da, nemin artmasıyla hava basıncının genellikle azaldığını gösteriyor, bu meteorolojide bilinen bir ilişki.
Diğer Değişkenler: Diğer değişkenler arasında da bazı korelasyonlar görülüyor ama bunlar, sıcaklık ve zaman arasındaki ilişki kadar güçlü değil.


![image](https://github.com/user-attachments/assets/9f8fcfb9-49f0-4f1c-91f4-9344189a8279)

# Makine Öğrenmesi Algoritmaları: 

Lineer Regresyon: 

Model, verilen verilerden elde edilen özellikleri kullanarak, örnek bir veri seti için 9.91°C tahmininde bulunmuştur. Bu sonuç, modelin sıcaklık tahminleri üzerinde yaptığı hesaplamanın bir örneğidir. R² skoru ise 0.68'dir; bu, modelin verilerdeki değişkenliğin %68'ini doğru bir şekilde açıkladığını gösterir. Ancak, %32'lik kısım model tarafından açıklanamayarak hataya yol açmaktadır. Modelin doğruluğunu artırmak amacıyla daha kapsamlı veri setleri ve farklı regresyon yöntemleri ile iyileştirmeler yapılabilir.
![image](https://github.com/user-attachments/assets/8f121919-d1eb-4801-b7ea-c06de266ff32)

Karar Ağacı:

Model, veri seti üzerinde eğitim alarak test verileri üzerinden tahminler yapmıştır. Ortalama Kare Hata (MSE) değeri 9.88 olarak hesaplanmıştır. Bu değer, modelin tahminlerinin gerçek sıcaklık değerlerinden ortalama sapmasını gösterir. MSE'nin düşük olması, modelin tahminlerinin gerçek değerlere yakın olduğunu belirtir, ancak daha da düşük bir MSE değeri modelin daha doğru tahminler yaptığını gösterir.
Modelin görselleştirilmesi de yapılmış ve karar ağacının yapısı analiz edilmiştir. Karar ağacında, sıcaklık tahminlerinde en etkili olan değişkenler yıl, nem, basınç (hPa) gibi faktörlerdir. Bu, sıcaklık tahmininde bu özelliklerin önemli bir rol oynadığını ortaya koymaktadır.

![image](https://github.com/user-attachments/assets/acef4418-e6f5-435f-a31c-d0cc6e7c7fc2)

Son olarak, yeni bir veri örneği üzerinde yapılan tahmin 14.73°C'dir. Bu, modelin eğitim verilerinden elde ettiği bilgileri kullanarak yapılan makul bir sıcaklık tahminidir.
Karar ağacı görsel şekli:

![image](https://github.com/user-attachments/assets/9c39ef9d-5227-4b0e-bd4f-9ee05491a0d6)

Random Forest: 

Model, veri setini öğrenerek test verileri üzerinde tahminler yapmıştır. Ortalama Kare Hata (MSE) değeri 1.89 olarak hesaplanmıştır. Bu düşük MSE değeri, modelin oldukça doğru tahminler yaptığını göstermektedir. Daha düşük bir MSE, modelin tahminlerinin gerçek verilere daha yakın olduğunu ve modelin genel olarak daha başarılı olduğunu ifade eder.

![image](https://github.com/user-attachments/assets/0bd7927c-6276-4374-b893-b146af593871)

Görselleştirme adımında, gerçek ve tahmin edilen değerler karşılaştırılmıştır. Grafik üzerinde mavi noktalar, test verisindeki gerçek sıcaklık değerleri ile model tarafından tahmin edilen sıcaklıkları göstermektedir. Kırmızı çizgi, ideal durumda gerçek ve tahmin edilen değerlerin tam olarak örtüşmesini gösteren bir referans çizgisidir. Çizginin etrafındaki dağılma, modelin tahmin doğruluğunu ve hata seviyesini görsel olarak yansıtır. Grafik, modelin büyük ölçüde doğru tahminler yaptığını ve bazı küçük sapmalar olduğunu gösteriyor.
Yeni bir veri örneği kullanılarak yapılan tahmin sonucu 10.69°C olarak bulunmuştur. Bu, modelin eğitim verilerinden öğrendiği bilgilere dayanarak makul bir tahmindir.

![image](https://github.com/user-attachments/assets/d9237190-8d8d-45b0-b6b7-a73ef197ccc3)

# Sonuç Analizi:

Bu çalışmada, ortalama sıcaklık tahminleri yapmak için üç farklı makine öğrenimi modeli kullanılmıştır: Doğrusal Regresyon, Karar Ağacı ve Random Forest. Her modelin performansı değerlendirildiğinde, doğrusal regresyonun genel olarak yeterli sonuçlar verdiği ancak daha karmaşık ilişkilerde sınırlı kaldığı görülmüştür. Doğrusal Regresyon modeli, MSE değeri 9.91 ile belirli bir doğruluk sağlamış olsa da, gerçek dünyadaki verilerin doğrusal ilişkilerden ziyade daha karmaşık yapılar içerdiği göz önüne alındığında, daha esnek modellere ihtiyaç duyulmaktadır.

Karar Ağacı modeli, daha esnek bir yaklaşım sunduğundan, verilerdeki doğrusal olmayan ilişkileri daha iyi modellemiştir. Bununla birlikte, karar ağacının MSE değeri 9.88 olarak doğrusal regresyona oldukça yakın kalmış ve modelin karmaşıklığından tam anlamıyla faydalanılmamış gibi görünmüştür. Karar ağaçları genellikle çok güçlü sonuçlar verse de, derin ağaçların aşırı uyum yapma riski vardır, bu da genel performansı sınırlayabilir.
En yüksek başarıyı ise Random Forest modeli göstermiştir. Random Forest, birden fazla karar ağacının birleşiminden oluşan bir ansambl modelidir ve bu yapı sayesinde daha doğru ve güvenilir sonuçlar üretmektedir. MSE değeri 1.89 ile diğer iki modele kıyasla çok daha düşük kalmıştır, bu da modelin karmaşık veri yapılarıyla daha iyi başa çıktığını ve genelleme yeteneğinin daha güçlü olduğunu göstermektedir. Bu model, veri setindeki karmaşık ilişkileri çözmede ve daha tutarlı tahminler yapmada en başarılı olmuştur.

Genel olarak, bu üç modelin karşılaştırılması, doğrusal regresyonun yalnızca basit veri yapıları için uygun olduğunu ve daha karmaşık veriler için daha gelişmiş modellerin tercih edilmesi gerektiğini ortaya koymaktadır. Karar ağacı ve Random Forest gibi ansambl yöntemler, doğrusal olmayan ilişkileri daha iyi modelleyebilirken, özellikle Random Forest, doğruluk açısından en iyi sonuçları sağlayarak bu çalışmada en uygun model olarak öne çıkmıştır. Bu sonuçlar, veri biliminde ve iklim analizi gibi karmaşık veri setlerinde doğru tahminler yapmak için ansambl yöntemlerinin ve güçlü modellerin önemini vurgulamaktadır.

















