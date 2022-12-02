# RPA Projects

ROBUSTA iş birliğiyle düzenlenen RPA Bootcamp kapsamında süreç tasarımı, XPath kullanımı ve Robusta programı üzerinde süreç geliştirme üzerine bir hafta boyunca süren detaylı bir eğitime katıldım. Bu bootcamp kapsamında hazırladığım 2 farklı sürecin örneklerini ilerleyen satırlarda bulabilirsiniz. İki süreçte sorunsuz bir şekilde çalışmaktadır. Süreçlerin detaylarına girmeden genel çalışma mantığını aşağıda bulabilirsiniz.

## Çeşitli alışveriş sitelerinde ürün arama

Bu süreçte: ürün isimleri ve ürün kodları yazılı bir excel dosyasıdan trendyol.com sitesi üzerinde ilgili ürünlerin fiyatlarının karşılaştırılması ve en uygun fiyatın bulunması üzerinde çalıştım. 
  
- Tanımlı excel dosyasından verilerin okunur ve bu veriler yeni bir dataset içerisinde tutulur.
- Elde edilen dataset boyutunda bir döngü kurulur, farklı sitelerde de arama yapılabilmesi için DMN tablosu içinden site isimleri çekilir.

![screencapture-cloud-robusta-ai-8443-modeler-2022-08-01-09_06_07](https://user-images.githubusercontent.com/20983261/182714343-f03cc756-f8df-4be6-b3f5-ed9839fc33db.png)

- Arama yapılacak site açılır ve yeniden bir döngü kurularak her ürün bazında arama yapılması sağlanır.
- Dataset içerisinden ürün kodu çekilir ve site üzerinde arama yapılır.
- Ürünün sitede olup olmadığı ve sonrasında farklı kategorilerde ilgili ürünününün olup olmadığı kontrol edilir.
- ürün yok ise fiyat sıfır olarak dataset'e yazılır. Farklı kategoriler var ise ürün adı ile eşleşen kategori seçilir.
- Bulunan ürün fiyatları yeni bir dataset'e kaydedilir ve en düşük fiyat bulunur. Dateset'e en uygun fiyat yazılır ve süreç sonlanır.

![screencapture-cloud-robusta-ai-8443-modeler-2022-08-01-09_06_18](https://user-images.githubusercontent.com/20983261/182716322-17f214cd-c131-417d-9ae1-e6c03deedc43.png)

## Booking.com üzerinde en iyi bileti bulma

İkinci örnek olarak; mail ile iletilen bir excel dosyası senaryosu üzerine booking.com üzerinde verilen rota üzerinden en uygun biletin bulunması için hazırladığım süreçtir.  

- Süreç üç aşamadan oluşmaktadır. (Mail, excel ve uygulama operasyonları olarak üç aşama)
- İlk olarak mail bağlantısı sağlanır ve hangi adresten ve konu başlığından gelen maillerin seçileceği tanımlanır. Maildeki ek yerel klasöre kaydedilir.

![screencapture-cloud-robusta-ai-8443-modeler-2022-08-01-09_06_58](https://user-images.githubusercontent.com/20983261/182719671-57f2b47c-947c-43a8-bb98-1805de497b35.png)

- Excel'den veriler okunur ve uygun olup olmadığı kontrol edilir.
- Döngü içerisinde her bir satırdaki veriler çekilir.
- Site üzerinde ilgili arama yapıldıktan sonra çıkan sonuca göre bilet bilgisi dataset'e yazılır.

![screencapture-cloud-robusta-ai-8443-modeler-2022-08-01-09_07_06](https://user-images.githubusercontent.com/20983261/182720040-b9ad9e21-8006-4853-bded-37d020417995.png)

- Rota  ve tarih bilgisi çekilir ve site üzerinden arama yapılır.
- Uygun XPath'ler ile best price, cheapest price opsiyonları tespit edilir. Bu aşamada uygun uçuş olup olmadığı da kontrol edilir.
- Best price tespit edildikten sonra site içersindeki paylaş aksiyonu ile ilgili fiyat bilgisi paylaşılır.
- Ek olarak excel'e yazılan her bir rotaya ait best price bilgisi mail ile müşteriye iletilir.

![screencapture-cloud-robusta-ai-8443-modeler-2022-08-01-09_07_15](https://user-images.githubusercontent.com/20983261/182720639-a4e2b6e2-4056-4592-8f30-fc7e0421e28b.png)
