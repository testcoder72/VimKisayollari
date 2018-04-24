# Vim Kısayolları

Vim shortcuts in Turkish language.

Eklenecekler: 
Vim kültürü mizahı, vim golf, sık kullanılan kısa yollar, vimgrep, konfigrasyon


# Vim nedir? #

Vim etkili biçimde metin düzenlemek için çok iyi yapılandırılabilir bir metin editorüdür.

# Vim ne değildir? #

Vim kullanıcılarının elinden tutmak için tasarlanmış bir editör değildir. Bir araçtır, kullanılması öğrenilmelidir. Vim kelime işlemci değildir.

# Vim'den Çıkış #

```
ESC :q!
```

# Dosya oluşturma #

```
> vim dosyaAdı
> vim dizin/dosyaAdı 
> vim (Enter)     dosyadan çıkarken :w dosyadı ile önce kaydet ve sonra :q ile çık.
```

# Vim modları #
```
Vim, kullanıcının içeriğe odaklanması için farklı modlar sunar.

Normal mod: Vim normal olarak bu modda başlar. ESC ile bu moda geçilir.
Insert mod: Editöre text bu modla eklenir. İnsert komutlarının biriyle bu moda geçilir.
Görsel mod: Text üzerinde belli alanları seçmek için kullanılır. v ile karakter bazında, V ile satır bazında, C-V ile block bazında görsel moda geçilir.
Komut modu: Normal moda geçtikten sonra : ile geçilir. Komut girilmesini sağlar. Ör. :h CTRL-R
```
# Genel #

```
> vimtutor          vim resmi öğretici metni
:h konu             belirtilen konu hakkında detaylı yardım dosyasını aç


:q                  kapat
:w                  kaydet/write
:saveas dosyaadı    farklı kaydet
:wa[!]              yaz/kaydet butun pencereler [zorla]
:wq                 kaydet ve çık
:x                  yaz ve çık, wq ile aynı
:q!                 dosya degismişse ve degişiklik kaydedilmeyecekse kapatmaya zorla
```

```
u        Geri al
C-r      İleri al
U        Satirdaki tum degisikligi geri al
```

```
y        Secili bolgeyi kopyala (yank)
yy       Butun satiri kopyala
p        Yapistir, satırın altına (paste)
"<reg>y  Seçili bolgeyi registera koplaya (a-z den register) 
c        Seçili bolgeyi kes
"<reg>p  Registera yapistir (a-z den register) 
P        Yapıştır, satırın üstüne
```

```
:!<cmd>  Vim'den ayrılmadan shell'den <cmd> komutunu calistir Ör: !g++ -Wall -std=c++14 main.cpp
C-z      Vim'i arka plana gonder (fg tekrar geri getirir)
```

### Windows ###

```
C-ws     Mevcut pencereyi yatay olaral bol (alternatif :split)
C-wv     Mevcut pencereyi dikey olarak bol (alternatif :vsplit)
C-ww     Sonraki pencereye zipla 
C-wARROW Mevcut pencereden sol/sag/yukari/asagi (ok tuslari) yondeki pencereye zipla
C-w#<    Mevcut pencereyi sagdan # kadar yeniden boyutlandir (default 1) 
C-w#>    Mevcut pencereyi saga # kadar yeniden boyutlandir (default 1) 
```

### Insert moda geçme ###

```
a        İmlecten sonra textin sonuna ekle
A        Satirin sonuna ekle 
i        İmlecten oncesine text ekle
I        Satırın başına ekle
o        İmlecin altina yeni bir satir yap ve text ekle 
O        İmlecin ustune yeni bir satir yap ve text ekle
s        İmlecin altindaki harfi sil 
S        Tum satiri sil
cc       Mevcut satiri sil
cw       Kelimeyi sil
Shift-r  Kelimeyi olduğu yerde değiştir. (Windows'taki insert)
```

### Kaydetme ###
Vim 26 registara sahip (a-z), kaydetmek istedigin bir tanesini sec. Kaydetme modundan ESC ile cik
```
q[a-z]   Kaydetmeye basla, Hareketler dahil hersey kaydedilecek
@[a-z]   Kaydedilen hareketleri baslat
```


# Hareketler #

_temel_
```
h        imlec sola
j        imlec alta
l        imlec saga
k        imlec yukari
```

```
H        Ekranin basina zıpla (High)
M        Ekranin ortasina zıpla (Middle)
L        Ekranin altina zıpla (Low)
C-b      Bir tam ekran yukari git (page up)
C-f      Bir tam ekran asagi git  (page down)
C-d      Bir yarim ekran asagi git
C-u      Bir yarim ekran yukari git
z-enter	 İmlecin altındaki yeri ekranın başına getir
z.       İmlecin altındaki yeri ekranın ortasına getir
z-		 İmlecin altındaki yeri ekranın altına getir
```

```
w        sonraki kelimenin başına zıpla (işaretlemelerin ayrı bir kelime olduğu varsayılır)
e        sonraki kelimenin sonuna zıpla
b        kelimenin başına zıpla
0        satir basi
^        ilk bos olmayan karakter
$        satir sonu
G        Dosyanin en alti
gg       Dosyanin en ustu
+ 		 sonraki satır başına
- 		 önceki satır başına
. 		 Son komutu tekrarla
```

## __operatör [sayı] hareket veya [sayı] operator hareket__ ##
```
cw       kelimeyi değiştir (change word)
c3w 	 veya 3cw, 3 kelime değiştir (cw cw cw)
4j       jjjj 
2w       w w,  iki sonraki kelimenin başına git
c$       imlecin altından kelime sonuna kadar değiştir
2dd 	 2 satırı sil
```

## _bilinmesi faydali_ ##
```
E        Kelimenin sonuna zipla (isaretlemelerin kelime olduğu varsayılmaz)
W        Kelimenin basina zipla 
B        Geriye dogru kelimenin basina zipla (isaretleme yok)
#G       # numaralı satıra git Ör: 38G
#gg      #G ile aynı
```


## #'yi ara, #'ya zipla  ##

```
*        imlecin altindaki kelimeden sonraki kelimeleri ara
%        Eslenen paranteze zipla
[{       Mevcut kod blogunun basina zipla 
]}       Mevcut kod blogunun sonuna zipla 
gd       Degisken deklerasyonuna zipla
f<c>     Mevcut imlec pozisyonundan <c> karakterini bul
'.       Son duzenlenen satira zipla
g;       Son duzenlenen pozisyona geri zipla 
```


# Düzenleme #
```
x        Imlecin altindaki karakteri sil
X        Imlecten onceki karakteri sil 
#x       Imlecin altindaki karakterden itibaren # tane karakter sil
dw       Sonraki kelimeyi sil 
dW       Sonraki kelimeye kadar sil 
d^       Satir basina kadar sil
d$       Satir sonuna kadar sil 
D        Satir sonuna kadar sil d$ ile ayni 
dd       Tum satiri sil
dib      Parantez blogundaki icerigi sil (Ör: fonksiyon argumanlari)
```

```
C-n      Anahtar kelime tamamlama
Tab      Anahtar kelime tamamlama (SuperTab uzantisi)
r<c>     <c> karakterini degistir
```

```
:s/xxx/yyy/    xxx'i yyy'nin ilk goruldugu yerde degistir 
:s/xxx/yyy/g   xxx'i yyy'nin goruldugu yerde degistir, tumcede (global)
:s/xxx/yyy/gc  xxx'i yyy'nin goruldugu yerde degistir ama onay iste, tumcede
:%s/xxx/yyy/g  xxx'i yyy'nin goruldugu yerde degistir, tum dosyada
```

```
u        Secimi kucuk harfe cevir (visual mode)
U        Secimi buyuk harfe cevir (visual mode)
```

```
:g/^#/d  # ile baslayan tum satirlari sil
:g/^$/d  Tum bos satirlari sil
```

## Birden fazla dosya ile çalışma ##

```
> vim -o3 f1.txt f2.txt f3.txt      Dosyaları yan yana aynı pencerede aç (horizontally split)
> vim -O3 f1.txt f2.txt f3.txt      Dosyaları alt üst aynı pencerede aç (vertically split)

> vim f1.txt f2.txt f3.txt          Dosyaların her birini aç ama aynı anda sadece birini gör, birbirleri arasında :next ve :prev ile geçiş yap, :n dosyaAdı ile yeni dosya ekle
```
### Tabları kullanma ###

```
> vim -p f1.txt f2.txt f3.txt

:tabn               sonraki tab, normal modda gt, 3gt üçüncü tab, insert modda C-PgDn
:tabp               önceki tab, normal modda gT, insert modda C-PgUp
:tabedit dosyaadı   belirtilen dosyayı yeni bir tabda düzenle
:tabfind dosyaAdı   dosyayı yeni bir tabda aç ve düzenle
:tabfirst           ilk taba git
:tablast            son taba git
:tabm {i}           mevcut tabı i+1 inci taba taşı. Ör: :tabm 0 mevcut tabı ilk tab yap, :tabm  mevcut tabı son tab yap
:tabclose i         i numaralı tabı kapat
:tabclose           mevcut tabı kapat
:tabonly            diğer tüm tabları kapat
:tabs               tabları listele
```

# Sık kullanılanlar #

```
yyp     Alt satıra kopyala
yyP     Üst satıra kopyala
```


# Linkler #

## Kopya kagitlari ##

* http://www.worldtimzone.com/res/vi.html
* http://www.fprintf.net/vimCheatSheet.html
* https://wiki.archlinux.org/index.php/Vim
* http://www.fprintf.net/vimCheatSheet.html

## Makaleler ##

* Vim notları: https://www.emrah.com/notlar/vim_notlari.txt
* Etkili 7 metin düzenleme alışkanlığı: http://www.moolenaar.net/habits.html
* 11 yıl sonra Vim: http://statico.github.com/vim.html
* Vim'e, eve dönüş: http://stevelosh.com/blog/2010/09/coming-home-to-vim 

## Tavsiye ve Teknikler ##

* [vimcasts.org](http://vimcasts.org/) Video-casts on vim
* [usevim.com](http://usevim.com/) Eklenti tanitimlari ve tavsiyeler
* [vimregex.com](http://vimregex.com/) Vim'in regex motoru hakkinda bilgiler 
* http://stackoverflow.com/questions/1218390/what-is-your-most-productive-shortcut-with-vim Kullanışlı vim kisayollari 
* Practical Vim - Edit Text at the Speed of Though - Kitap

## Siteler ##

* Vim - heryerde bulunan editor: https://www.vim.org/
* Vim uzantıları: https://vimawesome.com/
* Belirtilen alıştırmaları en kısa vim komutu kullanarak tamamlama https://vimgolf.com/

## Uzantilar ##

* NERDTree
* NERDCommenter
* Ctrl-P
* easytags
* unimpard
* supertab
* tagbar
* omnicomplete (C++)