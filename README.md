# mizan-dini-gunler

Mizan uygulamasının "Dini Günler Galerisi" bölümü için içerik deposu.
Uygulama, her açılışta `manifest.json`'ı bu repodan (raw.githubusercontent.com
üzerinden) çeker — yeni görsel/kandil eklemek için uygulamanın yeni bir
sürümünü yayınlamaya gerek yoktur, sadece bu repoya push yeterlidir.

## Nasıl içerik eklenir

1. Görseli ilgili `images/<klasör>/` altına ekleyin (dosya adı serbest,
   örn. `1.jpg`, `2.jpg`).
2. `manifest.json`'da ilgili günün anahtarı altına görselin ham (raw) GitHub
   URL'sini ekleyin:
   ```
   https://raw.githubusercontent.com/ultrAsailor/mizan-dini-gunler/main/images/<klasör>/<dosya>
   ```
3. Commit + push. Uygulama bir sonraki açılışta yeni içeriği otomatik gösterir
   (raw.githubusercontent.com'un birkaç dakikalık CDN önbelleği olabilir).

## Anahtar (l10nKey) ↔ klasör eşlemesi

Manifest anahtarları, uygulamadaki `ReligiousDay.l10nKey` ile **birebir**
aynı olmalı — yanlış yazılırsa o gün sessizce "Yakında" görünür, hata
vermez.

| Gün | manifest.json anahtarı | önerilen klasör |
|---|---|---|
| Hicri Yılbaşı | `religiousDayHicriYilbasi` | `images/hicri_yilbasi/` |
| Aşure Günü | `religiousDayAsureGunu` | `images/asure_gunu/` |
| Mevlid Kandili | `religiousDayMevlidKandili` | `images/mevlid_kandili/` |
| Regaib Kandili | `religiousDayRegaibKandili` | `images/regaib_kandili/` |
| Miraç Kandili | `religiousDayMiracKandili` | `images/mirac_kandili/` |
| Berat Kandili | `religiousDayBeratKandili` | `images/berat_kandili/` |
| Ramazan Başlangıcı | `religiousDayRamazanBaslangici` | `images/ramazan_baslangici/` |
| Kadir Gecesi | `religiousDayKadirGecesi` | `images/kadir_gecesi/` |
| Ramazan Bayramı | `religiousDayRamazanBayrami` | `images/ramazan_bayrami/` |
| Arefe Günü | `religiousDayArefeGunu` | `images/arefe_gunu/` |
| Kurban Bayramı | `religiousDayKurbanBayrami` | `images/kurban_bayrami/` |

## manifest.json şeması

```json
{
  "religiousDayBeratKandili": {
    "images": [
      "https://raw.githubusercontent.com/ultrAsailor/mizan-dini-gunler/main/images/berat_kandili/1.jpg"
    ],
    "caption": "Berat Kandiliniz mübarek olsun"
  }
}
```

- `images`: zorunlu, en az bir URL.
- `caption`: isteğe bağlı.
- Henüz görseli hazır olmayan bir günü manifeste hiç eklemeyin — uygulama
  otomatik olarak "Yakında" gösterir, hata vermez.
- Yalnızca telifsiz/hakları size ait (markalı, kendi hazırladığınız)
  görseller ekleyin.

## Dini Duvar Kağıtları ("Daha → Dini Duvar Kağıtları")

Kandil günlerinden ayrı, serbest kategorili genel bir duvar kağıdı galerisi
— aynı `manifest.json`'ın `"wallpapers"` anahtarı altında yaşar. Buradaki
kategori id'leri `ReligiousDay.l10nKey` gibi sabit bir listeye bağlı
DEĞİLDİR — istediğiniz kadar kategori serbestçe eklenebilir, uygulama
listeyi doğrudan bu anahtarlardan türetir.

```json
{
  "wallpapers": {
    "esmaul_husna": {
      "label": "Esmaül Hüsna",
      "images": ["https://raw.githubusercontent.com/ultrAsailor/mizan-dini-gunler/main/images/wallpapers/esmaul_husna/1.jpg"]
    },
    "cami": {
      "label": "Cami",
      "images": ["..."]
    },
    "hat_sanati": {
      "label": "Hat Sanatı",
      "images": ["..."]
    }
  }
}
```

- Kategori anahtarı (`esmaul_husna` gibi) serbesttir — yeni bir kategori
  eklemek için `images/wallpapers/<yeni_kategori>/` klasörü açıp
  manifestte yeni bir anahtar eklemeniz yeterli, kod tarafında hiçbir
  değişiklik gerekmez.
- `label`: zorunlu — ekranda gösterilen başlık (kategori id'si değil, bu
  kullanılır).
- Boş bir kategori (`"images": []`) veya hiç eklenmemiş bir kategori
  listede görünmez (kandil günlerinin aksine burada sabit bir "tüm
  kategoriler" listesi yok — yalnızca manifestte olanlar gösterilir).
- Şu an hazır klasörler: `images/wallpapers/esmaul_husna/`,
  `images/wallpapers/cami/`, `images/wallpapers/hat_sanati/` — dilediğiniz
  gibi yenilerini ekleyebilirsiniz.
