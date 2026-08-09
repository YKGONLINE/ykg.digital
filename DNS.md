# GoDaddy DNS — ykg.digital → GitHub Pages

Amaç: siteyi GitHub Pages’e bağlamak. **MX kayıtlarına dokunma** (`ykg@ykg.digital` bozulmasın).

## 1) GitHub tarafı (bitti)

- Repo: https://github.com/YKGONLINE/ykg.digital  
- Pages: `main` / kök  
- Custom domain: `ykg.digital` (repoda `CNAME` dosyası var)

## 2) GoDaddy’de yapılacaklar

Giriş: [GoDaddy DNS](https://dcc.godaddy.com/) → `ykg.digital` → **DNS** / **Manage DNS**

### Sil veya devre dışı bırak (web ile ilgili eski kayıtlar)

Aşağıdakiler genelde GoDaddy parking içindir; **web** için:

| Tip | Ad | Ne yap |
|-----|-----|--------|
| A | `@` | Eski IP’leri sil (ör. `15.197…`, `3.33…`) |
| CNAME | `www` | Varsa parking hedefi ise sil veya güncelle |

**Sakın silme:**

| Tip | Ad | Neden |
|-----|-----|--------|
| MX | `@` | Google e-posta |
| TXT | `@` | SPF, Google doğrulama vb. |
| CNAME | mail / google ile ilgili | e-posta |

### Ekle (GitHub Pages apex)

| Tip | Ad (Host) | Değer | TTL |
|-----|-----------|--------|-----|
| A | `@` | `185.199.108.153` | 600 veya varsayılan |
| A | `@` | `185.199.109.153` | 600 |
| A | `@` | `185.199.110.153` | 600 |
| A | `@` | `185.199.111.153` | 600 |
| CNAME | `www` | `YKGONLINE.github.io` | 600 |

Kaydet. Yayılım genelde 5–30 dk (nadiren birkaç saat).

## 3) Kontrol

```bash
dig +short ykg.digital A
# Beklenen: 185.199.108–111.153

dig +short ykg.digital MX
# Beklenen: aspmx.l.google.com vb. (değişmemeli)

curl -sI https://ykg.digital | head -10
```

Tarayıcı: https://ykg.digital  

## 4) HTTPS (DNS oturduktan sonra)

Repo → **Settings → Pages → Custom domain**

1. `ykg.digital` yazılı olsun, DNS check yeşil  
2. **Enforce HTTPS** kutusu → işaretle  

## 5) İleride subdomain

Örnek `atlas.ykg.digital` için ayrı CNAME (Cloud veya başka host):

| Tip | Ad | Değer |
|-----|-----|--------|
| CNAME | `atlas` | (Cloud load balancer / pages hostname) |

Ana sayfa DNS’i bozmaz.
