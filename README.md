# 🍋 Limon Satış Takip

Limon satışlarını kaydetmek için basit, tek dosyalık bir web uygulaması. Kurulum gerektirmez, çevrimdışı da çalışır; veriler cihazın kendi tarayıcısında saklanır.

**Canlı adres:** https://seydaozdmr.github.io/limon/

## Özellikler

- **Cari yönetimi** — satış yaptığın kişi/firmaları ekle, düzenle, sil.
  - Cari listesi Türkçe alfabetik sırayla gösterilir; ad, telefon veya not içinde arama yapılabilir.
  - Telefon alanı otomatik formatlanır: `5438888888` yazınca `0(543)888 88 88` olur.
  - `+90` / `90` / `0090` ile başlayan numaralar da otomatik ayıklanıp doğru formatlanır.
  - Android Chrome'da 📇 butonuyla telefon rehberinden isim ve numara doğrudan seçilebilir (Contact Picker API; iOS/Safari desteklemez).
- **Satış kaydı** — cari seç, tarih, kilo, kilogram bazlı fiyat gir; toplam otomatik hesaplanır. Peşin / veresiye seçilir.
- **Raporlar** — toplam ciro, toplam kilo, peşin/veresiye dağılımı, cari bazlı özet, tarih/cari/ödeme türüne göre filtrelenebilir detaylı satış listesi.
- **Yedekleme** — tüm veriyi JSON olarak dışa aktarma / içe aktarma, tüm veriyi sıfırlama.
- **Çevrimdışı çalışma** — Service Worker ile sayfa önbelleğe alınır, internet olmadan da açılıp kullanılabilir.
- **Yüklenebilir uygulama (PWA)** — kendi ikonu ve manifest dosyasıyla telefonun ana ekranına gerçek bir uygulama gibi eklenebilir.

## Veri saklama

Veriler yalnızca tarayıcının `localStorage`'ında tutulur:

- Ekstra kurulum, hesap veya sunucu gerekmez.
- Veriler cihaza/tarayıcıya özeldir — farklı bir cihazdan girildiğinde otomatik senkronize olmaz.
- Tarayıcı verilerini temizlersen veya farklı bir tarayıcı/cihaz kullanırsan kayıtlara erişemezsin. Bu yüzden ara sıra **Yedek** sekmesinden JSON dosyası indirmen önerilir.
- Uygulama, aynı anda birden fazla sekme/pencerede açık olsa bile her kayıt işleminden önce güncel veriyi diskten tekrar okur; böylece eski bir sekmenin üzerine yazıp veri kaybına yol açması engellenir.

## Telefonda kullanma

1. https://seydaozdmr.github.io/limon/ adresini Chrome'da aç (çevrimdışı önbelleğin oluşması için ilk açılışın internetli olması gerekir).
2. Sağ üstteki ⋮ menüsünden **"Ana ekrana ekle"** seçeneğini kullan.
3. Artık kendi ikonuyla, normal bir uygulama gibi ana ekrandan açabilirsin — internet olmasa da çalışır.

## Geliştirme / Yayına alma

Bu depo şu dosyalardan oluşur:

- `index.html` — uygulamanın tamamı (saf HTML/CSS/JS, framework veya derleme adımı yok).
- `manifest.json` — PWA (ana ekrana ekleme) tanımı.
- `sw.js` — çevrimdışı çalışmayı sağlayan Service Worker.
- `icon.svg` — uygulama ikonu.

`main` dalına yapılan her push, `.github/workflows/deploy-pages.yml` içindeki GitHub Actions iş akışı ile otomatik olarak GitHub Pages'e yayınlanır.

Yerelde denemek için:

```bash
python3 -m http.server 8000
```

ve tarayıcıda `http://localhost:8000/index.html` adresini aç.

> Not: Service Worker sadece `https://` veya `localhost` üzerinden çalışır; dosyayı doğrudan `file://` ile açtığında çevrimdışı önbellekleme devreye girmez.
