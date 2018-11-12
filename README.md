# Vim Kısayolları

> Vim shortcuts in Turkish.

<img alt="PRs Welcome" src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg" />

## Vim nedir? 

Vim etkili biçimde metin düzenlemek için çok iyi yapılandırılabilir bir metin editorüdür.

### Vim Tarihi <sup>1</sup>

**ed** Unix'in orijinal text editörüydü. Video ekranların yaygın olmadığı bir zamanda yazılmıştı. Kaynak kod
genelde sarılmış bir kağıda yazılır ve teletype terminalde düzenlenirdi. Terminala girilen komutlar işlenmesi
 için anabilgisayara gönderilir ve her bir komutun çıktısı yazdırılırdı. O günlerde terminal ile anabilgisayar
 arasındaki bağlantı yavaştı, hatta o kadar ki hızlı yazan biri ağı, işlenecebilecekten daha fazla komut
göndererek, doldurabilirdi. Bu bağlamda **ed**'in kısa komutlar sunması hayli önemliydi. Mesela *p* mevcut 
satırı yazdırırken, *%p* tüm dosyayı yazdırır.


**ed** birkaç kuşak ilerlemeden geçti, mesela **em** ("editor for mortals", ölümlüler için editör), **en**, 
ve sonunda **ex**. O zamana gelindiğinde video ekranlar daha yaygındı, **ex** terminal ekranını, dosyanın
 içeriğini gösteren etkileşimli pencerelere çeviren bir özellik ekledi. Şimdi yapılan değişikleri 
gerçek-zamanlı olarak görmek olanaklıydı. Ekran-düzenleme modu **:visual** veya kısaca **:vi** komutu ile 
aktif hale getiriliyordu.  **vi** ismi burdan geldi.


**Vim**, *vi improved* (vi geliştirildi)'nin kısaltmasıdır. Vim bundan çok daha fazlasıdır -ben düz vi kullanmaya katlanamam!- 
vi'de olmayan Vim özelliklerinin listesi için **vi-differences**'a bakınız. Vim'in geliştirmeleri
 çok önemlidir ama atalarına hala çok şey borçludur. Vim'in atalarının tasarımına rehberlik eden
 kısıtlar bize bugün hala değerli olan bir komut kümesi bıraktı.

##  Vim ne değildir? 

Vim kullanıcılarının elinden tutmak için tasarlanmış bir editör değildir. Bir araçtır, kullanılması
 öğrenilmelidir. Vim kelime işlemci değildir.

## [Vim'den Çıkış](https://stackoverflow.blog/wp-content/uploads/2017/05/country_stuck_vim-1-2-1024x1024.png)

```
<esc> :q! <enter> 
```

* [Dosya oluşturma](#dosya-oluşturma)
* [Vim modları](#vim-modları)
* [Genel](#genel)
* [Hareketler](#hareketler)
* [Insert moda geçme](#insert-moda-geçme)
* [Birden Fazla Dosyayla Çalışma](#birden-fazla-dosyayla-çalışma)
    * [Tabları kullanma](#tabları-kullanma)
* [Kaydetme](#kaydetme)
* [Komutlari tekrar etme](#komutları-tekrar-etme)
* [Düzenleme](#düzenleme)
    * [Bul ve Değiştir](#bul-ve-değiştir)
* [Sık kullanılanlar](#sık-kullanılanlar)
* [Yapılandırma](#yapılandırma)
    * [vimrc dosyası](#vimrc-dosyası)
    * [Mapping](#mapping)
* [Uzantı ekleme](#uzantı-ekleme) 
    * [Vundle ile uzantı ekleme](#vundle-ile-uzantı-ekleme)
    1. [Kurulum](#kurulum)
    2. [Uzantıyı yükleme](#uzantıyı-yükleme)
    3. [Uzantılar hakkında bilgi](#uzantılar-hakkında-bilgi)
* [Bazı Uzantılar](#bazı-uzantılar)
* [Linkler](#linkler)

## Dosya oluşturma

```
$ vim <enter>
$ vim dosyaAdı
$ vim dizin/dosyaAdı 

```

## Vim modları

```
Vim, kullanıcının içeriğe odaklanması için farklı modlar sunar.

normal mod: vim normal olarak bu modda başlar. esc ile bu moda geçilir.
insert mod: editöre text bu modla eklenir. [insert komutları](insert-moda-geçme)nın biriyle bu moda geçilir.
görsel mod: text üzerinde belli alanları seçmek için kullanılır. v ile karakter bazında, v ile satır bazında, C-v ile block bazında görsel moda geçilir.
komut modu: normal moda geçtikten sonra : ile geçilir. komut girilmesini sağlar. her bir komuttan sonra <enter> basılmalıdır. ör. :h ctrl-r <enter>

```
## Genel

```
$ vimtutor          vim resmi öğretici metni
:h konu             belirtilen konu hakkında detaylı yardım dosyasını aç, yardım dosyası içindeki hyperlinke tıklamak için imlec linkin altıdayken C-], geri C-[

:q                  kapat
:w                  kaydet/write
:saveas dosyaadı    farklı kaydet
:wa[!]              yaz/kaydet butun pencereler [zorla]
:wq                 kaydet ve çık
:wqa                bütün tabları kaydet ve çık (write, quit all) bkz: [tabları kullanma](#tablari-kullanma)
:x                  yaz ve çık, wq ile aynı
:q!                 dosya değismişse ve değişiklik kaydedilmeyecekse kapatmaya zorla

```

```
u                geri al, ör: 4u
C-r              ileri al        (Ctrl'ye basılı tutarak r) 
U                satırdaki tüm değisikliği geri al

s=seconds, m=minute, h=hour, d=day
:earlier #m     dosyayı # dakika önceki haline döndür ör: :earlier 2m  veya :ea 3d
:later #m       dosyayı # dakika sonraki haline döndür ör: :later 7s  veya  :lat 9h

```

```
y                seçili bölgeyi kopyala (yank)
yy               bütün satırı kopyala
p                yapıstır, satırın altına (paste)
"<reg>y          seçili bolgeyi registera koplaya (a-z den register) 
c                seçili bolgeyi kes
"<reg>p          registera yapistir (a-z den register) 
P                yapıştır, satırın üstüne
.                son komutu tekrarla

```

```
:!<cmd>  vim'den ayrılmadan shell'den <cmd> komutunu calistir ör: `!g++ -wall -std=c++14 main.cpp`, `!ruby %`
:sh      shell'e git, `exit` ile tekrar vim'e dön
C-z      vim'i arka plana gonder (fg geri getirir)

```

## Hareketler

```

                                k
h        imlec sola             ^
j        imlec alta        h <     > l
l        imlec saga             v
k        imlec yukarı           j

```

```
0        satır başına
$        satır sonu
<home>   satır başı
<end>    satır sonu 
```

```
w        sonraki kelimenin başına zıpla (işaretlemelerin ayrı bir kelime olduğu varsayılır)
e        sonraki kelimenin sonuna zıpla
b        kelimenin başına zıpla
```

```
h        ekranin başına zıpla (high)
m        ekranin ortasina zıpla (middle)
l        ekranin altına zıpla (low)
```

```
C-b      tam ekran boyu kadar yukarı git (page up)
C-f      tam ekran boyu kadar aşağı git  (page down)
C-d      yarım ekran aşağı
C-u      yarım ekran yukarı
```

```
zt       imlecin bulunduğu yeri ekranın üstüne getir
z<enter> zt ile aynı
zb       imlecin bulunduğu yeri ekranın altına getir
z-       zb ile aynı
z.       imlecin bulunduğu yeri ekranın ortasına getir
zz       z. ile aynı
```
```
%        eşleşen paranteze zıpla
(        önceki cümle
)        sonraki cümle
{        önceki paragraf
}        sonraki paragraf
[{       mevcut kod blogunun basina zıpla 
]}       mevcut kod blogunun sonuna zıpla 
gd       degisken deklerasyonuna zıpla 

```

```
w        sonraki kelimenin başına zıpla (işaretlemelerin ayrı bir kelime olduğu varsayılır)
e        sonraki kelimenin sonuna zıpla
ge       önceki kelimenin sonuna zıpla
b        kelimenin başına zıpla
^        boşluk olmayan ilk karakter
gg       dosyanin en üstü
g        dosyanin en altı
+        sonraki satır başına
-        önceki satır başına
.        son komutu tekrarla

```
 
```                                                                                            v           v
E        kelimenin sonuna zıpla (isaretlemelerin ayrı bir kelime olduğu varsayılmaz) Ör: e (abcd)   E (abcd)
W        kelimenin basina zıpla 
B        geriye dogru kelimenin basina zıpla (isaretleme yok)
#g       # numaralı satıra git ör: 38g
#gg      #g ile aynı

```

## Insert moda geçme ##

```
/~~~~~~~~~~\<---Esc------/~~~~~~~~~~\
|normal mod|             |insert mod|
\~~~~~~~~~~/--aAiIoOsS-->\~~~~~~~~~~/
 |        | 
 v vV     ^ Esc
 |        | 
/~~~~~~~~~~\
|visual mod|
\~~~~~~~~~~/

```

```
i        imlecten öncesine text ekle
i        satırın başına ekle
a        imlecten sonra textin sonuna ekle
a        satirin sonuna ekle 
o        imlecin altına yeni bir satir yap ve text ekle 
o        imlecin üstüne yeni bir satir yap ve text ekle
s        imlecin altındaki harfi sil 
s        tüm satiri sil
cc       mevcut satiri sil ve insert moda geç
cw       kelimeyi sil ve insert moda geç (change word)
shift-r  kelimeyi olduğu yerde değiştir. (windows'taki insert)

```

## Birden fazla dosyayla çalışma 

```
C-ws       mevcut pencereyi yatay olaral bol (alternatif :split)
 
C-wv       mevcut pencereyi dikey olarak bol (alternatif :vsplit)
C-ww       sonraki pencereye zıpla 
```
```
C-warrow   mevcut pencereden sol/sag/yukari/asagi (ok tuslari) yondeki pencereye zıpla
C-wq       mevcut pencereyi kapat
```
```
C-w#<      mevcut pencereyi sagdan # kadar yeniden boyutlandir (default 1) 
C-w#>      mevcut pencereyi saga # kadar yeniden boyutlandir (default 1) 
:res #     yatay bölünmüş pencereyi # kadar yeniden boyutlandır
```
```
C-         mevcut pencereyi en sola taşı 
C-wj       mevcut pencereyi en alta taşı         
C-wk       mevcut pencereyi en üste taşı         
C-wl       mevcut pencereyi en sağa taşı
```

```
$ vim -o3 f1.txt f2.txt f3.txt      dosyaları alt üst aynı pencerede aç (horizontally split)
$ vim -o3 f1.txt f2.txt f3.txt      dosyaları yan yana aynı pencerede aç(vertically split)

$ vim f1.txt f2.txt f3.txt          dosyaların her birini aç ama aynı anda sadece birini gör, birbirleri arasında :next ve :prev ile geçiş yap, :n dosyaadı ile yeni dosya ekle

```
### tabları kullanma ###

```
$ vim -p f1.txt f2.txt                 f1.txt ve f2.txt dosyalarını tab şeklinde aç

:tabedit dosyaadı   belirtilen dosyayı yeni bir tabda düzenle
:tabfind dosyaadı   dosyayı yeni bir tabda aç ve düzenle

```
```
:tabn       sonraki tab, normal modda gt, 3gt üçüncü tab, insert modda C-pgdn
:tabp       önceki tab, normal modda gt, insert modda C-pgup
:tabfirst   ilk taba git
:tablast    son taba git

```
```
:tabm {i}           mevcut tabı i+1 inci taba taşı. ör: :tabm 0 mevcut tabı ilk tab yap, :tabm  mevcut tabı son tab yap

```
```
:tabclose i   i numaralı tabı kapat
:tabclose     mevcut tabı kapat
:tabonly      diğer tüm tabları kapat

```
```
:tabs               tabları listele
```

## Kaydetme

birden fazla hareketi kaydetmek için oldukça kullanışlı. vim 26 registara sahip (a-z),
1. q ile kaydetmeyi başlat ve kaydetmek istedigin bir register seç. örnek: qa
2. kaydetme modundan esc ile cik.
3. kaydedilen değişikliği @<reg> şeklinde uygula. örnek: @a<enter>
        
```
q[a-z]   kaydetmeye basla, hareketler dahil hersey kaydedilecek
@[a-z]   kaydedilen hareketleri baslat
```


## Komutları tekrar etme

**operatör [sayı] hareket** veya **[sayı] operator hareket**

```
c3w      veya 3cw, 3 kelime değiştir (cw cw cw)
4j       jjjj 
2w       w w,  iki sonraki kelimenin başına git
2dd      2 satırı sil

```


## Düzenleme 

```
x        imlecin altındaki karakteri sil
X        imlecten önceki karakteri sil 
dw       sonraki kelimeyi sil 
dW       sonraki kelimeye kadar sil 
d^       satir basina kadar sil
d$       satir sonuna kadar sil 
D        satir sonuna kadar sil d$ ile ayni 
dd       tüm satiri sil
dib      parantez blogundaki icerigi sil (ör: fonksiyon argumanlari)

```

```
C-n      metinde daha önce geçmiş kelimeyi tamamla
C-p      metinde daha önce geçmiş kelimeyi tamamla
 
tab      anahtar kelime tamamlama (supertab uzantisi)
r<c>     <c> karakterini degistir

```

```
*        imlecin altındaki kelimeden sonraki kelimeleri ara
f<c>     mevcut imlec pozisyonundan <c> karakterini bul ör: 3f<c> satırda <c> karakterinin 3. kez görüldüğü yere git
'.       son duzenlenen satira zıpla
g;       son duzenlenen pozisyona geri zıpla 

```
```
:ab slm selam         insert modda 'slm'<space> yazıldığında 'selam' ile değiştir.

```

```
:g/^#/d  # ile başlayan tüm satırları sil
:g/^$/d  tüm boş satırları sil
```

### bul ve değiştir

```
:s/eski/yeni      mevcut satırda ilk 'eski'nin görüldüğü yeri 'yeni' ile değiştir
:s/eski/yeni/g    mevcut satırdaki tüm 'eski'leri 'yeni' ile değiştir
:s/eski/yeni/gc   mevcut satırdaki tüm 'eski'leri 'yeni' ile değiştir ama öncesinde onay iste

:#,#s/old/new/g   # ve # satırları (dahil) arasındaki 'eski'leri 'yeni' ile değiştir
:%s/eski/yeni/g   mevcut dosyadaki tüm 'eski'leri 'yeni' ile değiştir
:%s/eski/yeni/gc  mevcut dosyadaki tüm 'eski'leri 'yeni' ile değiştir ama öncesinde onay iste

```

## Bazı sık kullanılanlar 

```
yyp     alt satıra kopyala
yyp     üst satıra kopyala
ddp     alt satırla üst satırı yer değiştir
ea      kelimenin sonuna ekle
xp      yanyana iki harfi yerdeğiştir         ör: microsotf ->  microsoft 
dgg     imleçin bulunduğu yerden dosyanın başına kadar sil
```

## Yapılandırma

### .vimrc dosyası

.vimrc dosyası vim'in çalışma anında ayarlarını tanımlar. sistemin kullandığı bir .vimrc ve herbir kullanıcının
home dizininde birer .vimrc vardır. home dizinindeki .vimrc, sistem .vimrc'yi override eder. 
eğer .vimrc home dizininde yoksa, `vim .vimrc` ile oluşturabilirsiniz. bkz: [default .vimrc içeriği](https://gist.github.com/anonymous/c966c0757f62b451bffa)

### mapping 

mapping ile uzun komutları kısa komutlara dönüştürebiliriz.
mapleri kalıcı olarak kullanamk için .vimrc dosyasına
eklememiz gerekir.

 üç temel mod için 3 temel mapping çeşidi vardır;

- normal modda çalışabilicek **nmap**
- insert modda çalışabilicek **imap**
- visual modda çalışabilecek **vmap**

genel formül: 
> map kısayol uzunKomutlar

```
nmap m <C-d>        "normal moddayken, m tuşuna ctrl-d komutlarını (yarım sayfa alta) atamış olduk
imap jk <ESC>       "insert moddayken, jk basıldığında ESC basılmış gibi, normal moda geç
```
daha fazla özel karakter ismi için:
```
:h key-notation
```
ama bu komutlar daha önce maplenmiş diğer komutları çakışabileceğinden,
 mümkün mertebe komutları no-recursive yapmak iyi bir uygulamadır. 

Seçeceğimiz kısayolun bir başka map tarafından kullanılıp kullanılmadığını öğrenmek için:
```
:verbose map kısayol 
```

aşağıda _o_ yani alt satıra in ve insert moda geç, komutunu 4 kere tekrarlayacığını umduğumuz bu komut
sonsuz döngü neden olur. _o_ _4o_'yu, _4o_ diğer bir _4o_'yu çağırmaya çalışacaktır.

```
nmap o 4o 
```
mapleri no-recursive  için de komutun başına *nore* getirilir.

- normal mod için **nnoremap**
- insert mod için **inoremap**
- visual mod için **vnoremap**

bu komut beklediğimiz gibi çalışır, normal moddayken _o_'ya bastığımızda 4 satır alta inip insert 
moda geçer.

```
nnoremap o 4o
```

mapleri dosya tipine göre özelleştirebiliriz: 

```
autocmd filetype cpp nnoremap <f5> :w <bar> !clear && clang++-6.0 
        \ -wshadow
        \ -wnon-virtual-dtor
        \ -wpedantic 
        \ -wold-style-cast
        \ -woverloaded-virtual 
        \ -wconversion 
        \ -std=c++1z -o2 %  && ./a.out <CR>
```
 
yukarıdaki örnekte f5 sağındaki tüm komutları çalıştırır, ve yalnızca `.cpp` uzantılı dosyalar için çalışacaktır.

sırasıyla:

1. autocmd komutu filetype event'ini çağırır ve dosya tipi cpp ise map çalıştırılabilir
2. :w ile dosyayı kaydeder
3. `<bar>` diğer komutları bağlamada kullanılır
4. !clear bir bash komutu olan _clear_ çalıştırılır
5. komut uzun olduğundan, bir alt satırdan devam etmek için alttaki satırın başına `\` ekledik
6. clang flagleriyle derlemeyi çalıştırıp `<CR>` yani enter tuşuna basmış olduk

#### leader değişkeni
_leader_ seçtiğimiz bir tuşu maplerde kullanabiliriz.

```
let mapleader = "-"
```
leader olarak '-' karakterini seçtim.

 
```
nnoremap <leader>ve :vsplit $myvimrc<cr>
```
eğer .vimrc'yi düzenlemek istersem normal modda '-ve' karakterlerine basmam gerekecek


bütün mapleri görmek için:
```
:map
```

Daha fazla bilgi:
```
:help mapping
```
## Uzantı ekleme

Vim'e uzantı eklemenin en kolay yolu bir paket yöneticisi kurmak. Birden fazla paket yöneticisi mevcut:

- [Pathogen](https://github.com/tpope/vim-pathogen)
- [Vim8 paketler özelliği](http://vimhelp.appspot.com/repeat.txt.html#packages)
- [NeoBundle](https://github.com/Shougo/neobundle.vim)
- [vim-plug](https://github.com/junegunn/vim-plug)
- [dein.vim](https://github.com/Shougo/dein.vim)
- [Vundle](https://github.com/VundleVim/Vundle.vim)

### Vundle ile uzantı ekleme

Vundle (Vim bundle) Vim için tasarlanmış bir eklenti yöneticisidir. Eklenti yüklemenize, güncellemenize, kullanılmayan eklentileri kaldırmanıza izin verir.

#### kurulum

```
$ git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim 
```
ve .vimrc dosyasının başına şunları ekleyin :

```vims
set nocompatible         
filetype off             

set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()

" ----> Uzantılar Buraya <-----

call vundle#end()        
filetype plugin indent on  
```

Vundle ile uzantı eklemek içim .vimrc dosyasındaki:

```
call vundle#begin()
```
ve 

```
call vundle#end() 
```
satırları arasına, uzantıya göre;

- github'taki bir uzantıyı eklemeniz için:
`Plugin 'GithubKullanıcıAdı/RepoAdı'`   Ör: `Plugin 'tpope/vim-fugitive'`
    
- [vimscipt](http://vim-scripts.org/vim/scripts.html) şeklindeki Vim uzantılarını eklemek için:
`Plugin 'uzantıAdı'`   Ör: `Plugin 'L9'`

- Github'ta tutulmayan git repoları için:
  Ör: `Plugin 'git://git.wincent.com/command-t.git'`

- Bilgisayardaki bir git reposu için (mesela kendi uzantını geliştiriyorsundur):
  Ör: `Plugin 'file:///home/theUser/path/to/plugin'`

şekillerinde eklememiz gerekiyor.

#### uzantıyı yükleme

Son adımda uzantıyı yüklemek için:
```
Vim'de
:PluginInstall

shell'de
$vim +PluginInstall +qall
```

#### uzantılar hakkında bilgi

```
:PluginList                 uzantıları listele
:PluginInstall              uzantıları yükle
:PluginUpdate               uzantıları güncelle
:PluginSearch <abc>         <abc> uzantısını ara
:PluginClean                kullanılmayan uzantıları kaldır
```
### Bazı uzantılar

* [NERDTree](https://github.com/scrooloose/nerdtree) dosya şistemi kaşifi
* [YouCompleteMe](https://github.com/Valloric/YouCompleteMe) kod tamamlama motoru
* [Surround](https://github.com/tpope/vim-surround) sözcükleri köşeli, süslü, normal parantezlere almak için
* [Fugitive](https://github.com/tpope/vim-fugitive) Vim içerisinde hızlıca Git komutlarını uygulamak için
* [vim-commentary](https://github.com/tpope/vim-commentary) şeyleri hızlıca yorum satırını dönüştürmek için 
* [ctrlp](https://github.com/ctrlpvim/ctrlp.vim) Vim içeride hızlıca diğer dosyaları açmak için
* [vim-airline](https://github.com/vim-airline/vim-airline)

## Linkler 

### kopya kağıtları

* http://www.worldtimzone.com/res/vi.html
* http://www.fprintf.net/vimCheatSheet.html
* https://wiki.archlinux.org/index.php/Vim
* http://www.fprintf.net/vimCheatSheet.html
* https://devhints.io/vimscript

### kitaplar
* Practical Vim: Edit Text at the Speed of Though - Drew Neil
* Modern Vim - Drew Neil
* Learning Vi and Vim Editors - Arnold Robbins, Elbert Hannah
* The VimL Primer: Edit Like a Pro with Vim Plugins and Scripts - Benjamin Klein
* [A Byte of Vim](https://vim.swaroopch.com/) (Online Kitap)

### makaleler 

* Vim notları: https://www.emrah.com/notlar/vim_notlari.txt
* 7 Etkili metin düzenleme alışkanlığı: http://www.moolenaar.net/habits.html
* 11 yıl sonra Vim: http://statico.github.com/vim.html
* Vim'e, eve dönüş: http://stevelosh.com/blog/2010/09/coming-home-to-vim 

### tavsiye ve teknikler 

* [vimcasts.org](http://vimcasts.org/) Video-casts on vim
* [usevim.com](http://usevim.com/) Eklenti tanitimlari ve tavsiyeler
* [vimregex.com](http://vimregex.com/) Vim'in regex motoru hakkinda bilgiler 
* [Stackoverflow](http://stackoverflow.com/questions/1218390/what-is-your-most-productive-shortcut-with-vim) Kullanışlı vim kisayollari 
* [r/vim](https://www.reddit.com/r/vim/) Vim subreddit
* [vimrcfu](https://vimrcfu.com/) *.vimrc* ve mapping tavsiyeleri

### siteler 

* [Vim.org](https://www.vim.org) Vim - heryerde bulunan editor
* [vimawesome.com](https://www.vimawesome.com) Vim uzantıları
* [vimdoc.sourceforge.net](http://vimdoc.sourceforge.net/htmldoc/vimfaq.html) Vim Sık Sorulan Sorular
* [vimgolf.com](https://vimgolf.com) Vim alıştırmaları

<sup>1</sup> *Practical Vim: Edit Text at the Speed of Though* kitabından

### Licence

 <a href="http://www.wtfpl.net/"><img
       src="http://www.wtfpl.net/wp-content/uploads/2012/12/wtfpl-badge-4.png"
       width="80" height="15" alt="WTFPL" /></a>
