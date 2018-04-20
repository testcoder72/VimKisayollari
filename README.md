# Vim Kısayolları
Vim shortcuts in Turkish language.

Eklenecekler: 
Vim kültürü mizahı, vim golf, sık kullanılan kısa yollar, uzantı ekleme mini tutorial




# Vim nedir? #

Vim etkili biçimde metin düzenlemek için çok iyi yapılandırılabilir bir metin editorüdür.

# Vim ne değildir? #

Vim kullanıcılarının elinden tutmak için tasarlanmış bir editör değildir. Bir araçtır, kullanılması öğrenilmelidir. Vim kelime işlemci değildir.

# Vim'den Çıkış #

```
ESC :q!
```

# Genel #

```
:q        kapat
:w        kaydet/write
:wa[!]    yaz/kaydet butun pencereler [zorla]
:wq       kaydet ve cik
:x        yaz ve cik, wq ile ayni
:q!       dosya degismişse ve degişiklik kaydedilmeyecekse kapatmaya zorla
```

```
u        Geri al
U        Satirdaki tum degisikligi geri al
C-r      İleri al
```

```
v        Satir degisiklikleri icin görsel/visual moda gec
C-v      Blok degisiklikleri icin visual moda gec
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

### Windows ####

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
. 		 Son komutu tekrarla
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
```


_bilinmesi faydali_
```
E        Kelimenin sonuna zipla (isaretlemelerin kelime olduğu varsayılmaz)
W        Kelimenin basina zipla 
B        Geriye dogru kelimenin basina zipla (isaretleme yok)
#G       # numaralı satıra git Ör: 38G
#gg      #G ile aynı
```

# 		 #'yi ara, #'ya zipla  #

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

### vimgrep ve quickfix listesi ###
built-in grep, vimgrep uses vim's quickfix list. see vimcasts#44 for introduction: http://vimcasts.org/episodes/search-multiple-files-with-vimgrep/
```
:vimgrep /<regex>/g %        Search for <regex> with multiple occasions per line (g) 
                             in current file (%)
:vimgrep /<C-r>// %          On the command line, <C-r>/ (that is: CTRL-R followed by /) 
                             will insert the last search pattern.  
:vimgrep /<a>/g <filelist>   Search in the given files (<filelist>) 
:vimgrep /<a>/g *.cc         Search in all *.cc files current directory
:vimgrep /<a>/g **/*.cc      Search in all *.cc files in every sub-directory (recursively) 
:vimgrep /<a>/g `find . -type f`     
                             Search in all files that are returns by the backtick command.

:vim     short for :vimgrep

:cnext   Jump to next record/match in quickfix list
:cprev   Jump to previous record/match in quickfix list
```
Unimpaired plugin (https://github.com/tpope/vim-unimpaired) provides the following mappings:
```
[q       see :cprev
]q       see :cnext
[Q       see :cfirst
]Q       see :clast
```
Ayrica bkz: http://usevim.com/2012/08/24/vim101-quickfix/ ve http://vimdoc.sourceforge.net/htmldoc/quickfix.html



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


# Linkler #
## Kopya kagitlari ##
* http://www.worldtimzone.com/res/vi.html
* http://www.fprintf.net/vimCheatSheet.html
* https://wiki.archlinux.org/index.php/Vim
* http://www.fprintf.net/vimCheatSheet.html

## Makaleler ##
* Seven habits of effective text editing: http://www.moolenaar.net/habits.html
* Vim After 11 Years: http://statico.github.com/vim.html
* Coming Home to Vim: http://stevelosh.com/blog/2010/09/coming-home-to-vim 

## Tavsiye ve Teknikler ##
* [vimcasts.org](http://vimcasts.org/) Video-casts on vim
* [usevim.com](http://usevim.com/) Eklenti tanitimlari ve tavsiyeler
* [vimregex.com](http://vimregex.com/) Vim'in regex motoru hakkinda bilgiler 
* Kullanışlı vim kisayollari http://stackoverflow.com/questions/1218390/what-is-your-most-productive-shortcut-with-vim 

## Uzantilar ##
* NERDTree
* NERDCommenter
* Ctrl-P
* easytags
* unimpard
* supertab
* tagbar
* omnicomplete (C++)