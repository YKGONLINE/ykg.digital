# ykg.digital

YKG Digital — scroll ile ilerleyen tek sayfalık hikâye: Hiçlik → Big Bang → Atom → DNA → Bit → YKG.

Tüm animasyon `index.html` içindeki canvas parçacık sisteminde; dış bağımlılık yok.
Son sahnedeki geyik, `assets/mark-deer.png` dosyasından örneklenir (yerelde `file://` ile değil, HTTP sunucusuyla açın).

## Yerel önizleme

```bash
cd ~/Projects/ykg.digital
python3 -m http.server 8080
# → http://127.0.0.1:8080
```

## Yayın

GitHub Pages (branch: `main`, klasör: `/`).

Özel domain: `ykg.digital` (`CNAME` dosyası + GoDaddy DNS).

**Not:** MX kayıtlarına dokunma — `ykg@ykg.digital` e-postası bozulmasın.
