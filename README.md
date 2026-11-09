# Math Arena LIVE — Kahoot tarzı yarışma (V4)

7. sınıf tam sayılar ve rasyonel sayılar, 18 soru, 30 saniyelik süre, 120 kişilik katılım sınırı, 5 şube, 5/10/15. sorularda challenge.

## Kurulum

Node.js 18+ gereklidir.

```bash
npm install
npm start
```

Öğretmen `http://localhost:3000` adresinden **Oyun Oluştur** der. Öğrenciler aynı sunucunun adresini açıp 6 haneli PIN, istedikleri isim, şube ve avatar ile katılır.

## Oyun akışı

- Öğretmen **Sonraki Soruyu Başlat** ile her soruyu başlatır.
- 30 saniyelik süre sunucuda tutulur. Tüm öğrenciler cevapladığında soru erken kapanabilir. Öğretmen de **Soruyu Kapat** diyebilir.
- Doğru cevapta hızla orantılı **500–1000** puan, yanlış cevapta 0 puan.
- Doğru cevap ve cevap dağılımı 2,2 saniye gösterilir; ardından **ilk 10 skor tablosu 6 saniye** gösterilir.
- Challenge sonlarında skor tablosuna **şube puanları** da eklenir. Challenge'lar 5., 10. ve 15. sorulardadır; öğrenciler önceden görmez.
- 6 saniye bitince sistem **öğretmeni bekler**. Otomatik olarak yeni soru başlamaz.
- Avatar ve oyuncu bilgisi aynı tarayıcı sekmesindeki `sessionStorage` ile yeniden bağlanmada korunur.

## Çevrimiçi yayın

Bu proje **henüz internete yayımlanmış değildir**. Farklı evlerden katılım için Node.js ve WebSocket destekleyen bir barındırma ortamına yüklenmesi gerekir. Örneğin, WebSocket destekli Node.js hizmeti üzerinde `npm install` ve `npm start` komutlarıyla başlatılabilir. Sunucunun uykuya geçmediğini ve 120 eşzamanlı bağlantıyı kaldırdığını test edin.

## Sınırlar ve güvenlik

- Oyuncu sınırı **105**; bu kapasitenin gerçek cihazlarda doğrulandığı anlamına gelmez.
- Oyun durumu RAM'de tutulur; sunucu yeniden başlarsa oturumlar kaybolur. Kalıcı veritabanı, oda temizliği, ölçekleme ve yük testi üretim sürümüne eklenmelidir.
- Öğretmen erişimi gizli `hostKey` ile korunur. PIN tek başına yönetim yetkisi vermez.
- Öğrenci isimleri serbest yazılır; temel HTML güvenli kodlama uygulanır. İsim moderasyonu henüz yoktur.
- Sınıf challenge oranı, soru başladığında odada bulunan öğrenciler üzerinden hesaplanır; geçerli cevap vermeyen öğrenci yanlış sayılır.
- Katılım linki ve oyun PIN'i sadece sunucu çalışırken geçerlidir.


## V5: 35 dakikalık ders için kritik notlar

- En fazla 120 kayıtlı oyuncu alınır; daha az katılımcıyla öğretmen istediği anda başlatır. Hiç oyuncu yokken başlatılamaz.
- Her soru 30 saniye açık kalır (öğretmen isterse erken kapatabilir); herkes cevapladı diye otomatik erken kapanmaz.
- Katılımcı sayısı ve bağlı kullanıcı sayısı öğretmen panelinde ayrı gösterilir.
- Skor tablosu 6 saniye gösterilir, ardından sonraki soru için öğretmen beklenir.
- **ÜRETİM İÇİN HAZIR DEĞİL:** RAM'deki oda verisi sunucu yeniden başlarsa kaybolur. Yük testi, kalıcı veritabanı, sunucu yeniden başlama kurtarması, kopma/geri bağlanma testi, mobil cihaz ve hosting testi tamamlanmadan tek seferlik kritik derste kullanılmamalıdır.
- **Ders süresi:** 18 × 30 saniye = 9 dakika cevaplama; kalan 26 dakika açıklama, skor, geçiş, giriş ve teknik gecikmeler için. Öğrenci girişi dersten önce tamamlanmalıdır.
