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
