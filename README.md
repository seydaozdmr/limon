# 🍋 Limon Satış Takip

Limon satışlarını kaydetmek için basit, tek dosyalık bir web uygulaması. Kurulum gerektirmez, internet olmadan da çalışır; veriler cihazın kendi tarayıcısında saklanır.

**Canlı adres:** https://seydaozdmr.github.io/limon/

## Özellikler

- **Cari yönetimi** — satış yaptığın kişi/firmaları ekle, düzenle, sil.
  - Telefon alanı otomatik formatlanır: `5438888888` yazınca `0(543)888 88 88` olur.
  - `+90` / `90` / `0090` ile başlayan numaralar da otomatik temizlenip doğru formatlanır.
  - Android Chrome'da 📇 butonuyla telefon rehberinden isim ve numara doğrudan seçilebilir (Contact Picker API; iOS/Safari desteklemez).
- **Satış kaydı** — cari seç, tarih, kilo, kilogram bazlı fiyat gir; toplam otomatik hesaplanır. Peşin / veresiye seçilir.
- **Raporlar** — toplam ciro, toplam kilo, peşin/veresiye dağılımı, cari bazlı özet, tarih/cari/ödeme türüne göre filtrelenebilir detaylı satış listesi.
- **Yedekleme** — tüm veriyi JSON olarak dışa aktarma / içe aktarma, tüm veriyi sıfırlama.

## Veri saklama

Veriler yalnızca tarayıcının `localStorage`'ında tutulur:

- Ekstra kurulum, hesap veya sunucu gerekmez.
- Veriler cihaza/tarayıcıya özeldir — farklı bir cihazdan girildiğinde otomatik senkronize olmaz.
- Tarayıcı verilerini temizlersen veya farklı bir tarayıcı/cihaz kullanırsan kayıtlara erişemezsin. Bu yüzden ara sıra **Yedek** sekmesinden JSON dosyası indirmen önerilir.

## Telefonda kullanma

1. https://seydaozdmr.github.io/limon/ adresini Chrome'da aç.
2. Sağ üstteki ⋮ menüsünden **"Ana ekrana ekle"** seçeneğini kullan.
3. Artık normal bir uygulama gibi ana ekrandan açabilirsin.

## Geliştirme / Yayına alma

Bu depo tek bir `index.html` dosyasından oluşur (saf HTML/CSS/JS, framework veya derleme adımı yok). `main` dalına yapılan her push, `.github/workflows/deploy-pages.yml` içindeki GitHub Actions iş akışı ile otomatik olarak GitHub Pages'e yayınlanır.

Yerelde denemek için:

```bash
python3 -m http.server 8000
```

ve tarayıcıda `http://localhost:8000/index.html` adresini aç.
