# IdeaSoft Hediye Paketi ve Planlı Teslimat Modülü

IdeaSoft ürün detay sayfalarına ücretli hediye paketi, isteğe bağlı teslim tarihi ve hediye kartı notu ekleyen özelleştirilebilir tema modülüdür.

**Geliştiren:** Midas Dijital E-Ticaret Danışmanlık

## Özellikler

- Standart ve premium hediye paketi seçenekleri
- Seçilen hediye paketi ürününü otomatik olarak sepete ekleme
- Paket seçeneklerine ürün görseli ekleme
- Ürün görsellerinden paket detayına yönlendirme
- İsteğe bağlı teslim tarihi
- 250 karakter sınırlı hediye kartı notu
- IdeaSoft Ürün Özelleştirme sistemiyle uyum
- Modülleri ayrı ayrı açma ve kapatma
- Mobil uyumlu modern tasarım
- Tema rengini kolayca değiştirme
- Hediye paketi ürünlerinin kendi sayfalarında modülü gizleme

## Dosya Yapısı

```text
ideasoft-gift-delivery-module/
├── src/
│   └── gift-delivery-module.twig
├── .gitignore
├── LICENSE
└── README.md
```

## Gereksinimler

- IdeaSoft tema dosyalarına erişim
- En az bir adet hediye paketi veya hizmet ürünü
- Teslim tarihi ya da hediye kartı notu kullanılacaksa IdeaSoft Ürün Özelleştirme özelliği
- Kullanılan özelleştirme grubunun hediye paketi ürünlerine atanması

## Kurulum

`src/gift-delivery-module.twig` dosyasını IdeaSoft temanızın snippet klasörüne yükleyin.

Örnek dosya yolu:

```text
html/snippets/product/gift-delivery-module.twig
```

Ardından ürün detay şablonunu açın:

```text
templates/product/detail.twig
```

Aşağıdaki bölümü bulun:

```twig
<div class="product-cart-buttons">
```

Bu bloğun hemen üstüne şu satırı ekleyin:

```twig
{% include 'html/snippets/product/gift-delivery-module.twig' %}
```

Tema klasör yapınız farklıysa include yolunu kendi temanıza göre düzenleyin.

## Modülleri Açma ve Kapatma

`gift-delivery-module.twig` dosyasının üst kısmındaki ayarları kullanabilirsiniz:

```twig
{% set giftModule = 'on' %}
{% set standardGiftOption = 'on' %}
{% set premiumGiftOption = 'on' %}
{% set deliveryDateModule = 'on' %}
{% set giftMessageModule = 'on' %}
```

Bir özelliği kapatmak için değerini `off` yapın.

### Hediye paketi sistemini tamamen kapatma

```twig
{% set giftModule = 'off' %}
```

### Standart paketi kapatma

```twig
{% set standardGiftOption = 'off' %}
```

### Premium paketi kapatma

```twig
{% set premiumGiftOption = 'off' %}
```

### Teslim tarihini kapatma

```twig
{% set deliveryDateModule = 'off' %}
```

### Hediye kartı notunu kapatma

```twig
{% set giftMessageModule = 'off' %}
```

## Hediye Paketi Ürünlerini Ayarlama

Hediye paketi seçenekleri IdeaSoft yönetim panelinde normal veya hizmet ürünü olarak oluşturulmalıdır.

Standart paket ayarları:

```twig
{% set standardGiftProductId = 1001 %}
{% set standardGiftTitle = 'Standart hediye paketi' %}
{% set standardGiftDescription = 'Siparişiniz özenle paketlenerek gönderilir.' %}
{% set standardGiftPrice = '100,00 TL' %}
{% set standardGiftUrl = '/urun/standart-hediye-paketi' %}
{% set standardGiftImage = '' %}
```

Premium paket ayarları:

```twig
{% set premiumGiftProductId = 1002 %}
{% set premiumGiftTitle = 'Premium hediye paketi' %}
{% set premiumGiftDescription = 'Siparişiniz premium kutuda özel olarak hazırlanır.' %}
{% set premiumGiftPrice = '159,90 TL' %}
{% set premiumGiftUrl = '/urun/premium-hediye-paketi' %}
{% set premiumGiftImage = '' %}
```

### Ayarların açıklaması

| Ayar | Açıklama |
|---|---|
| `ProductId` | IdeaSoft ürün ID’si |
| `Title` | Müşterinin göreceği paket başlığı |
| `Description` | Paket seçeneğinin kısa açıklaması |
| `Price` | Ekranda gösterilecek fiyat |
| `Url` | Hediye paketi ürün bağlantısı |
| `Image` | Hediye paketi görsel bağlantısı |

> Fiyat ayarı yalnızca müşteriye gösterilen metindir. Sepete yansıyacak gerçek ücret, IdeaSoft ürün kartındaki satış fiyatından alınır.

## Görsel Ekleme

Paket görsellerini tam bağlantı olarak ekleyebilirsiniz:

```twig
{% set standardGiftImage = 'https://www.siteadresi.com/gorseller/standart-paket.webp' %}
{% set premiumGiftImage = 'https://www.siteadresi.com/gorseller/premium-paket.webp' %}
```

Görsel bağlantısı boş bırakılırsa ilgili pakette görsel gösterilmez:

```twig
{% set standardGiftImage = '' %}
```

## Ürün Özelleştirme Ayarları

IdeaSoft panelinde aşağıdaki özelleştirme grubunu oluşturun:

### Grup adı

```text
Teslimat ve Hediye Kartı Bilgileri
```

### Alanlar

1. **Teslim Tarihi**
   - Kısa metin alanı
   - İsteğe bağlı

2. **Hediye Kartı Notu**
   - Metin alanı
   - İsteğe bağlı

Grup ve alan ID’lerini modülün üst kısmında tanımlayın:

```twig
{% set customizationGroupId = 1 %}
{% set deliveryDateFieldId = 1 %}
{% set giftMessageFieldId = 2 %}
```

Özelleştirme grubunu modülde kullanılan standart ve premium hediye paketi ürünlerine atayın.

## Renk Ayarı

Modülün ana rengini değiştirmek için:

```twig
{% set moduleAccentColor = '#dc2237' %}
```

Örnek renkler:

```twig
{% set moduleAccentColor = '#4A0C12' %}
{% set moduleAccentColor = '#2563EB' %}
{% set moduleAccentColor = '#111827' %}
```

## Çalışma Mantığı

1. Müşteri ürün sayfasında hediye paketi seçeneğini açar.
2. Standart veya premium paketi seçer.
3. İsterse teslim tarihi ve hediye kartı notu girer.
4. Ana ürün normal şekilde sepete eklenir.
5. Seçilen hediye paketi ürünü ayrıca sepete eklenir.
6. Özelleştirme bilgileri hediye paketi ürünüyle birlikte siparişe aktarılır.

## IdeaSoft Uyumluluğu

Modül, sepete ekleme butonunda aşağıdaki IdeaSoft yapısını kullanan temalar için hazırlanmıştır:

```html
data-selector="add-to-cart"
data-context="detail"
data-product-id="..."
```

Özel olarak değiştirilmiş temalarda sepete ekleme butonunun CSS seçicisinin uyarlanması gerekebilir.

## Önemli Notlar

- Hediye paketi ürünleri satışa açık olmalıdır.
- Hediye paketi ürünlerinin stokları bulunmalıdır.
- Ekranda yazan fiyat ile IdeaSoft ürün fiyatı aynı tutulmalıdır.
- Teslim tarihi veya hediye notu kullanılacaksa özelleştirme grubu doğru ürünlere atanmalıdır.
- Değişikliklerden sonra IdeaSoft tema önbelleği temizlenmelidir.
- Tarayıcıda test ederken `Ctrl + F5` ile zorla yenileme yapılması önerilir.

## Lisans

Bu proje MIT Lisansı ile sunulmaktadır.

## Geliştirici

**Midas Dijital E-Ticaret Danışmanlık**

IdeaSoft tema geliştirmeleri ve e-ticaret çözümleri.
