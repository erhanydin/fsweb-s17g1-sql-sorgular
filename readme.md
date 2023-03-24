# SQL Sorgu Alıştırmaları

Bu hafta SQL sorguları üzerine çalışıyorsunuz. Bugünkü alıştırmada sizin için hazırladığımız veritabanında aşağıda istediğimiz sonuçları elde etmenize yarayan SQL sorgularını oluşturacaksınız.

# Proje Kurulumu
Projeyi forklayın ve clonlayın. Tamamladığınızda da pushlayın.

## Kütüphane Bilgi Sistemi

Bu veritabanı, bir okulun kütüphanesinden öğrencilerin aldıkları kitapların bilgisini barındırmaktadır.

#Tablolar 
`ogrenci` tablosu öğrencilerin listesini tutar.
`islem` tablosu öğrencilerin kütüphaneden aldıkları kitapların bilgilerini tutar
`kitap` tablosu kütüphanedeki kitapların bilgisini tutar
`yazar` tablosu kitapların yazarları bilgisini tutar
`tur` tablosu kitapların türlerini tutar.

Tablo ilişiklerini görmek için [ktphn.png] dosyasına göz atın.

Yazdığınız sorguları buradan test edebilirsiniz: [https://ergineer.com/assets/materials/fkg36so5-kutuphanebilgisistemi-sql/] (update, delete, drop sorguları iptal edilmiştir).

### Görevler

Aşağıda istenilen sonuçlara ulaşabilmek için gerekli SQL sorgularını altlarına yazın. 


	1) ÖRNEK SORU: Öğrenci tablosundaki tüm kayıtları listeleyin.
	
		CEVAP: select * from ogrenci

	
	2) Öğrenci tablosundaki öğrencinin adını ve soyadını ve sınıfını listeleyin.

		CEVAP: SELECT ograd, ogrsoyad, sinif FROM ogrenci 
	
	
	3) Öğrenci tablosundaki kız öğrencileri listeleyin. 

		CEVAP: SELECT * FROM ogrenci WHERE cinsiyet = 'K'
	
	
	4) Öğrenci tablosunda kaydı bulunan sınıfların adını her sınıf bir kez görüntülenecek şekilde listeleyiniz


		CEVAP: SELECT DISTINCT sinif FROM ogrenci;
	
	5) Öğrenci tablosunda, 10A sınıfında olan kız öğrencileri listeleyiniz.

		CEVAP: select * from ogrenci where cinsiyet ="K" and sinif="10A";
	
	6) Öğrenci tablosundaki 10A veya 10B sınıfındaki öğrencilerin adını, soyadını ve sınıfını listeleyiniz.

		CEVAP: select ograd, ogrsoyad, sinif from ogrenci where sinif = '10A' or sinif = '10B'
	
	
	7) Öğrenci tablosundaki öğrencinin adını, soyadını ve numarasını okul numarası olarak listeleyiniz. (as kullanım örneği)

		CEVAP: select ograd, ogrsoyad, ogrno as 'okul numarası' from ogrenci
	
	
	8) Öğrenci tablosundaki öğrencinin adını ve soyadını birleştirip, adsoyad olarak listeleyiniz. (concat, as kullanım örneği)

		CEVAP: select concat(ograd, ogrsoyad) as adsoyad  from ogrenci
	
	
	9) Öğrenci tablosundaki Adı ‘A’ harfi ile başlayan öğrencileri listeleyiniz.

		CEVAP: select * from ogrenci where ograd like 'A%'
	
	
	10) Kitaplar tablosundaki sayfa sayısı 50 ile 200 arasında olan kitapların adını ve sayfa sayısını listeleyiniz.

		CEVAP: select * from kitap where sayfasayisi <= 200 and sayfasayisi >=50


	11) Öğrenci tablosunda adı Fidan, İsmail ve Leyla olan öğrencileri listeleyiniz.

		CEVAP: select * from ogrenci where ograd in('Fidan', 'İsmail', 'Leyla')
	
	
	12) Öğrenci tablosundaki öğrencilerden adı A, D ve K ile başlayan öğrencileri listeleyiniz.
	
		CEVAP:  select * from ogrenci where ograd like 'A%' or ograd like 'D%' or ograd like 'K%'

	13) Öğrenci tablosundaki sınıfı 9A olan Erkekleri veya sınıfı 9B olan kızların adını, soyadını, sınıfını ve cinsiyetini listeleyiniz.

		CEVAP: select ograd, ogrsoyad, sinif, cinsiyet from ogrenci where (sinif = '9A' and cinsiyet = 'E') or (sinif = '9B' and cinsiyet = 'K') order by sinif;
	
	
	14) Sınıfı 10A veya 10B olan erkekleri listeleyiniz.

		CEVAP: select * from ogrenci where (sinif = '10A' and cinsiyet = 'E') or (sinif = '10B' and cinsiyet = 'E') order by sinif;
	
	
	15) Öğrenci tablosunda doğum yılı 1989 olan öğrencileri listeleyiniz.

		CEVAP: select * from ogrenci where dtarih like '1989%'
	
	
	16) Öğrenci numarası 30 ile 50 arasında olan Kız öğrencileri listeleyiniz.

		CEVAP: select * from ogrenci where cinsiyet = 'K' and (ogrno < 50 and ogrno > 30)
	
	
	17) Öğrencileri adına göre sıralayınız (alfabetik).
	
		CEVAP: select * from ogrenci order by ograd 
	
	18) Öğrencileri adına, adı aynı olanlarıda soyadlarına göre sıralayınız.

		CEVAP: select * from ogrenci order by ograd, ogrsoyad asc
	
	
	19) 10A sınıfındaki öğrencileri okul numarasına göre azalan olarak sıralayınız.

		CEVAP: select * from ogrenci where sinif = '10A' order by ogrno
	
	
	20) Öğrenciler tablosundaki ilk 10 kaydı listeleyiniz.
	[İPUCU: `Select top tüm mysql versiyonlarında düzgün çalışmaz. LİMİT kullanmak daha faydalıdır`]

		CEVAP: select * from ogrenci limit 10
	
	21) Öğrenciler tablosundaki ilk 10 kaydın ad, soyad ve doğum tarihi bilgilerini listeleyiniz.

		CEVAP: select ograd, ogrsoyad, dtarih from ogrenci limit 10
	
	
	22) Sayfa sayısı en fazla olan kitabı listeleyiniz.

		CEVAP: select * from kitap order by sayfasayisi desc limit 1
	
	
	23) Öğrenciler tablosundaki en genç öğrenciyi listeleyiniz.

		CEVAP: select * from ogrenci where dtarih= (SELECT MAX(dtarih) from ogrenci)

	
	
	24) 10A sınıfındaki en yaşlı öğrenciyi listeyin.

		CEVAP: select * from ogrenci where  dtarih = (SELECT MIN(dtarih) from ogrenci where sinif = '10A')

	
	
	25) İkinci harfi N olan kitapları listeleyiniz.

		CEVAP: select * from kitap where kitapadi like '_n%'


	
	26) Öğrencileri sınıflarına göre gruplayarak listeleyin.

		CEVAP: select * from ogrenci order by sinif
	
	
	27) Öğrencileri her sorgulamada sıralaması farklı olacak şekilde rastgele listeleyin. 
	[İPUCU: rand() fonksiyonu]

		CEVAP: select * from ogrenci order by rand()
	
	
	28) Öğrenci tablosundan Rastgele bir öğrenci seçiniz.

		CEVAP: select * from ogrenci order by rand() limit 1
	
	
	29) 10A sınıfından rastgele bir öğrencinin adını, soyadını, numarasını ve sınıfını getirin.

		CEVAP: select ograd, ogrsoyad, ogrno, sinif from ogrenci where sinif = '10A' order by rand() limit 1
	
	
	# Esnek
	30) Öğrenci tablosunda aynı isimde kaçar öğrenci olduğunu bulmak istiyoruz. 
	Öğrenci isimlerinin sayısını "adet" olarak öğrencilerin isimleri "isim" olarak listeleyin. 
	[İPUCU: count() ve group by]

		CEVAP: select count(ograd) as adet, ograd as isim from ogrenci group by ograd

