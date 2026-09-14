# IdeaSoft Hediye Paketi ve Planlı Teslimat Modülü

IdeaSoft ürün detay sayfalarına ücretli hediye paketi, isteğe bağlı teslim tarihi ve hediye kartı notu ekleyen tema modülüdür.

**Güncel sürüm:** v1.0.1

**Geliştiren:** Midas Dijital E-Ticaret Danışmanlık

## Özellikler

- Standart ve premium hediye paketi seçenekleri
- Paket ürününü ana üründen sonra otomatik sepete ekleme
- Tıklanabilir paket görselleri
- İsteğe bağlı teslim tarihi
- 250 karakter sınırlı hediye kartı notu
- IdeaSoft Ürün Özelleştirme sistemiyle siparişe bilgi aktarma
- Modülleri ayrı ayrı `on` / `off` yapabilme
- Mobil uyumlu ve renkleri değiştirilebilir tasarım

## Gereksinimler

- IdeaSoft tema dosyalarına erişim
- En az bir adet hizmet/hediye paketi ürünü
- Teslim tarihi veya kart notu kullanılacaksa IdeaSoft Ürün Özelleştirme özelliği
- Aynı özelleştirme grubunun modülün gösterileceği ana ürünlere atanması

## Kurulum

1. `src/gift-delivery-module.twig` dosyasını temanızdaki uygun snippet klasörüne yükleyin.
2. `templates/product/detail.twig` dosyasında `.product-cart-buttons` bloğunun hemen üstüne include ekleyin:

```twig
{% include 'html/snippets/product/gift-delivery-module.twig' %}
```

Tema klasör yapınız farklıysa yolu buna göre değiştirin.

## Modülleri açma ve kapatma

Dosyanın başındaki değerleri `on` veya `off` yapın:

```twig
{% set giftModule = 'on' %}
{% set standardGiftOption = 'on' %}
{% set premiumGiftOption = 'on' %}
{% set deliveryDateModule = 'on' %}
{% set giftMessageModule = 'on' %}
```

Örnek: teslim tarihini kapatıp hediye kartı notunu açık bırakmak için:

```twig
{% set deliveryDateModule = 'off' %}
{% set giftMessageModule = 'on' %}
```

## Ürün ayarları

Hediye paketi ürün ID, başlık, açıklama, fiyat, bağlantı ve görsellerini dosyanın başındaki ayarlardan değiştirin:

```twig
{% set standardGiftProductId = 1001 %}
{% set standardGiftPrice = '100,00 TL' %}
{% set standardGiftUrl = '/urun/standart-hediye-paketi' %}
{% set standardGiftImage = '' %}
```

Fiyat metni yalnızca ekranda gösterilir. Gerçek sepet fiyatı IdeaSoft ürün kartındaki satış fiyatıdır.

## Ürün özelleştirme ayarları

IdeaSoft panelinde bir özelleştirme grubu oluşturun:

- Teslim Tarihi: kısa metin, isteğe bağlı
- Hediye Kartı Notu: metin alanı, isteğe bağlı

Grup ve alan ID’lerini modülün başında tanımlayın:

```twig
{% set customizationGroupId = 1 %}
{% set deliveryDateFieldId = 1 %}
{% set giftMessageFieldId = 2 %}
```

Özelleştirme grubunu hediye paketi seçeneğinin gösterileceği ana ürünlere atayın. Çok sayıda ürün varsa IdeaSoft Çoklu Ürün Güncelleme özelliğini kullanabilirsiniz.

Modülde görünen tarih ve mesaj alanları kullanıcı arayüzüdür. Girilen değerler ana üründeki IdeaSoft özelleştirme alanlarına aktarılır. Paket ürünü ayrıca sepete eklenirken özelleştirme alanları geçici olarak devre dışı bırakılır; böylece tarih ve kart notu ikinci kez kaydedilmez.

## v1.0.1 düzeltmeleri

- Takvimden seçilen teslim tarihinin siparişe aktarılmaması düzeltildi.
- Hediye Kartı Notu bilgisinin iki kez kaydedilmesi düzeltildi.
- Görünen alanlar ile IdeaSoft’un yerleşik özelleştirme alanları senkronize edildi.
- Paket ürünü eklenirken özelleştirme verisinin yeniden gönderilmesi engellendi.

## Renk

Ana rengi değiştirmek için:

```twig
{% set moduleAccentColor = '#dc2237' %}
```

## Uyumluluk

Modül, ürün detay butonunda aşağıdaki IdeaSoft yapısını kullanan temalar için hazırlanmıştır:

```html
data-selector="add-to-cart"
data-context="detail"
data-product-id="..."
```

Özel olarak değiştirilmiş temalarda sepete ekle butonunun CSS seçicisi uyarlanabilir.

## Lisans

MIT Lisansı ile sunulmuştur.
