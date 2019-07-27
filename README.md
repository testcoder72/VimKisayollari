<p align="center"><img width="100" src="https://upload.wikimedia.org/wikipedia/commons/9/9f/Vimlogo.svg" alt="Vim logo"></p>

 <p align="center"> Vim metin editörü için bir alternatif öğrenim kılavuzu </p>

* [Vim'den Çıkış](vim'den-çıkış)
* [Vim Nedir?](#vim-nedir?)
    * [Vim'in Tarihi](#vim'in-tarihi)
    * [Vim Forkları ve Neovim](#vim-forkları-ve-neovim)
* [Dosya oluşturma](#dosya-oluşturma)
* [Vim modları](#vim-modları)
* [Genel](#genel)
* [Hareketler](#hareketler)
* [Insert moda geçme](#insert-moda-geçme)
* [Birden Fazla Dosyayla Çalışma](#birden-fazla-dosyayla-çalışma)
    * [Tabları kullanma](#tabları-kullanma)
* [Kaydetme](#kaydetme)
    * [Birden fazla komutu kaydederek tekrar etme](#birden-fazla-komutu-kaydederek-tekrar-etme)
* [Düzenleme](#düzenleme)
    * [Bul ve Değiştir](#bul-ve-değiştir)
* [Bazı sık kullanılanlar](#Bazı-sık-kullanılanlar) 
* [Kişiselleştirme](#Kişiselleştirme)
    * [Dotfiles ve .vimrc dosyası](#dotfiles-ve-.vimrc-dosyası)
    * [Mapping](#mapping)
    * [Uzantı ekleme](#uzantı-ekleme) 
        * [vim-plug ile uzantı ekleme](#vim-plug-ile-uzantı-ekleme)
* [Bazı uzantıların (eksik) listesi](#Bazı-uzantıların-(eksik)-listesi)
* [Linkler](#linkler)
* [Vim'i kaynak koddan build etme](#Vim'i-kaynak-koddan-build-etme)

### [Vim'den Çıkış](https://stackoverflow.blog/wp-content/uploads/2017/05/country_stuck_vim-1-2-1024x1024.png)

```
<esc> :q! <enter> 
```

### Vim nedir? 

Vim, etkili biçimde metin düzenlemek için, çok iyi yapılandırılabilir bir metin editorüdür.

Vim kullanıcılarının elinden tutmak için tasarlanmış bir editör değildir. Bir araçtır, kullanılması
 öğrenilmelidir. Vim kelime işlemci değildir.

#### Vim'in Tarihi <sup>1</sup>

**ed** Unix'in orijinal text editörüydü. Video ekranların yaygın olmadığı bir zamanda yazılmıştı. Kaynak kod
genelde sarılmış bir kağıda yazılır ve teletype terminalde düzenlenirdi. Terminala girilen komutlar işlenmesi
 için anabilgisayara gönderilir ve her bir komutun çıktısı yazdırılırdı. O günlerde terminal ile anabilgisayar
 arasındaki bağlantı yavaştı, hatta o kadar ki hızlı yazan biri ağı, işlenecebilecekten daha fazla komut
göndererek doldurabilirdi. Bu bağlamda **ed**'in kısa komutlar sunması hayli önemliydi. Mesela *p* mevcut 
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

#### Vim Forkları ve Neovim

[Neovim](https://neovim.io/) bir Vim fork'udur ve kendini Vim'e katkıda bulunmak isteyenlere daha açık hale getirmek için oluşturulmuş bir Vim uzantısı olarak tanımlar. 


### Dosya oluşturma

```
$ vim <enter>
$ vim dosyaAdı
$ vim dizin/dosyaAdı 
```

### Vim modları

Vim, kullanıcının içeriğe odaklanması için farklı modlar sunar.

* normal mod: vim normal olarak bu modda başlar. esc ile bu moda geçilir. `:h Normal-mode`:tropical_fish:
* insert mod: editöre text bu modla eklenir. [insert komutları](insert-moda-geçme)nın biriyle bu moda geçilir.  `:h Insert-mode`:tropical_fish:
* replace mod: text'leri olduğu yerde değiştirmek için kullanılır ve normal moddan `R` ile geçilir. :h  Replace-mode`:tropical_fish:
* görsel mod: text üzerinde belli alanları seçmek için kullanılır. v ile karakter bazında, V ile satır bazında, C-v ile block bazında görsel moda geçilir.  `:h Visual-mode`:tropical_fish:
* komut modu: normal moda geçtikten sonra : ile geçilir. komut girilmesini sağlar. Her bir komuttan sonra `<enter>` basılmalıdır. `:h Cmdline-mode`:tropical_fish: ör. `:h ctrl-r <enter>`

### Genel

```
$ vimtutor          vim resmi öğretici metni

:h user-manual
:h help-summary     Dökümantasyonun kullanımı hakkında
:h konu             konu hakkında yardım. Ör: `:h python` Ctrl-] linke tıkla, Ctrl-T geri gel

:q                  kapat (quit)
:w                  kaydet/write
:saveas dosyaadı    farklı kaydet
:wa[!]              yaz/kaydet bütün pencereler (write all) [zorla]
:wq                 kaydet ve çık
:wqa                bütün tabları kaydet ve çık (write, quit all) bkz: [tabları kullanma](#tablari-kullanma)
:x                  güncelle ve çık
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
"<reg>y          seçili bölgeyi registera kopyala (a-z den register) 
c                seçili bölgeyi kes
"<reg>p          registera yapistir (a-z den register) 
P                yapıştır, satırın üstüne
.                son komutu tekrarla
```

```
:term    Vim'den ayrilmadan terminali baslat  `:h terminal`
:!<cmd>  Vim'den ayrılmadan shell'den <cmd> komutunu çalıştır ör: `!g++ -Wall -std=c++14 main.cpp`, `!ruby %`
:sh      shell'e git, `exit` ile tekrar Vim'e dön
$C-z      Vim'i arka plana gonder ($fg geri getirir)
```

### Hareketler

`:h motion`:tropical_fish: 
```
                                k
h        imleç sola             ^
j        imleç alta        h <     > l
l        imleç sağa             v
k        imleç yukarı           j
```

```
0        satır başına
$        satır sonu
```

```
w        sonraki kelimenin başına zıpla (işaretlemelerin ayrı bir kelime olduğu varsayılır)
e        sonraki kelimenin sonuna zıpla
b        kelimenin başına zıpla
```

```
H        ekranin başına zıpla (high)
M        ekranin ortasina zıpla (middle)
L        ekranin altına zıpla (low)
```

```
C-b      tam ekran boyu kadar yukarı git (page up)
C-f      tam ekran boyu kadar aşağı git  (page down)
C-d      yarım ekran aşağı
C-u      yarım ekran yukarı
```

`:h scroll-cursor`:tropical_fish:  
```
z<enter> imlecin bulunduğu yeri ekranın en üstüne taşı ve imleci ilk karakterin altına koy
zt       yukarıdakine benzer ama imleci olduğu yerde bırak

z-       imlecin bulunduğu yeri ekranın en altına taşı ve imleci ilk karakterin altına koy
zb       yukarıdakine benzer ama imleci olduğu yerde bırak

z.       imlecin bulunduğu yeri ekranın ortasına taşı ve imleci ilk karakterin altına koy
zz       yukarıdakine benzer ama imleci olduğu yerde bırak
```

```
w        sonraki kelimenin başına zıpla (işaretlemelerin ayrı bir kelime olduğu varsayılır)
e        sonraki kelimenin sonuna zıpla
ge       önceki kelimenin sonuna zıpla
b        kelimenin başına zıpla
^        boşluk olmayan ilk karakter
gg       dosyanin en üstü
G        dosyanin en altı
+        sonraki satır başına
-        önceki satır başına
.        son komutu tekrarla
```
 
```                                                                                            v           v
E        kelimenin sonuna zıpla (işaretlemelerin ayrı bir kelime olduğu varsayılmaz) Ör: e (abcd)   E (abcd)
W        kelimenin başına zıpla 
B        geriye dogru kelimenin başına zıpla (isaretleme yok)
#G       # numaralı satıra git ör: 38G
#gg      #G ile aynı
```

Daha genel olarak<sup>2<sup>:
```
                gg
                 ?
                C-b
                 H
                 {
                 k
^ F T ( b ge h       l w e ) t f $
                 j
                 }
                 L
                C-f
                 /
                 G
```

### Insert moda geçme ##

```
                           /~~~~~~~~~~~~\
                           |command mode|
                           \~~~~~~~~~~~~/
                           |           |
                           ^ :/        v Esc Esc
                           |           |
 /~~~~~~~~~~~~\----Esc---->/~~~~~~~~~~~\<---Esc------/~~~~~~~~~~~\
 |replace mode|            |normal mode|             |insert mode|
 \~~~~~~~~~~~~/<----R------\~~~~~~~~~~~/--aAiIoOsS-->\~~~~~~~~~~~/
                           |           |
                           v vV        ^ Esc
                           |           |
                           /~~~~~~~~~~~\
                           |visual mode|
                           \~~~~~~~~~~~/

```
``` 
i        imleçten öncesine text ekle
I        satırın başına ekle
a        imleçten sonra text ekle
A        satirin sonuna ekle 
o        imlecin altına yeni bir satir yap ve text ekle 
O        imlecin üstüne yeni bir satir yap ve text ekle
s        imlecin altındaki harfi sil 
S        tüm satiri sil
cc       mevcut satiri sil ve insert moda geç
cw       kelimeyi sil ve insert moda geç (change word)

S-r      select mod'a gir, metni olduğu yerde değiştir
```

### Birden fazla dosyayla çalışma 

`:h usr_08.txt`:tropical_fish:  

```
C-ws       mevcut pencereyi yatay olaral böl (alternatif :split)
C-wv       mevcut pencereyi dikey olarak böl (alternatif :vsplit)
C-ww       sonraki pencereye zıpla 
```

```
C-w h      mevcut pancereden sağa geç
C-w j      mevcut pencereden aşağı geç
C-w k      mevcut penceden yukarı geç
C-w l      mevcut pencereden sola geç
C-w t      en üst soldaki pencereye geç
C-w b      en aşağı sağdaki pencereye geç
```
```
C-wq       mevcut pencereyi kapat
:close     yukarıdakiyle aynı
:only      mevcut bölme hariç diğerlerini kapat
```
```
C-w#<      mevcut pencereyi sağdan # kadar yeniden boyutlandir (default 1) 
C-w#>      mevcut pencereyi sağa # kadar yeniden boyutlandir (default 1) 
:res #     yatay bölünmüş pencereyi # kadar yeniden boyutlandır
```
`:h window-moving`:tropical_fish:
```
C-wH       mevcut pencereyi en sola taşı 
C-wJ       mevcut pencereyi en alta taşı         
C-wK       mevcut pencereyi en üste taşı         
C-wL       mevcut pencereyi en sağa taşı
```

```
$vim --help               Vim parametrelerini listele `h vim-arguments`:tropical_fish:

$ vim -O2 f1.txt f2.txt   Vim'i `-O[N]` parametresiyle aç, dikey bölünmüş f1.txt ve f2.txt dosyaları
$ vim -o2 f1.txt f2.txt   yukarıdaki gibi ama yatay bölünmüş
$ vim -P2 f1.txt f2.txt   yukarıdaki gibi ama tab sayfalarıyla

$ vim f1.txt f2.txt       dosyları aç ama yalnızca birini göster (:next ve :prev ile geçiş yap)
```

#### tabları kullanma

`:h tabpage`:tropical_fish:

```
:tabedit dosyaadı   belirtilen dosyayı yeni bir tabda düzenle
:tabfind dosyaadı   dosyayı yeni bir tabda aç ve düzenle
```
```
:tabn       sonraki tab
:tabp       önceki tab
:tabfirst   ilk taba git
:tablast    son taba git
```
```
:tabm {i}           mevcut tabı i+1 inci taba taşı
```
```
:tabclose i   i numaralı tabı kapat
:tabclose     mevcut tabı kapat
:tabonly      diğer tüm tabları kapat
```
```
:tabs               tabları listele
```

### Komutları tekrar etme

**operatör [sayı] hareket** veya **[sayı] operator hareket**

```
c3w      veya 3cw, 3 kelime değiştir (cw cw cw)
4j       jjjj 
2w       w w,  iki sonraki kelimenin başına git
2dd      2 satırı sil
```
#### Birden fazla komutu kaydederek tekrar etme

`:h recording`:tropical_fish:  

Birden fazla hareketi kaydetmek için oldukça kullanışlı. Vim 26 registara sahip (a-z), 26 farklı clipboard gibi!
1. q ile kaydetmeyi başlat ve kaydetmek istedigin bir register seç. örnek: qa
2. kaydetme modundan esc ile cik.
3. kaydedilen değişikliği @<reg> şeklinde uygula. örnek: @a<enter>
        
```
q[a-z]   kaydetmeye başla, hareketler dahil herşey kaydedilecek
@[a-z]   kaydedilen hareketleri başlat
```

### Düzenleme 

```
x        imlecin altındaki karakteri sil
X        imleçten önceki karakteri sil 
dw       sonraki kelimeyi sil 
dW       sonraki kelimeye kadar sil 
d^       satır başına kadar sil
d$       satır sonuna kadar sil 
D        satır sonuna kadar sil d$ ile aynı
dd       tüm satırı sil
dib      parantez blogundaki içeriği sil (ör: fonksiyon argumanları)
```

```
C-n      metinde daha önce geçmiş kelimeyi tamamla
C-p      metinde daha önce geçmiş kelimeyi tamamla
 
tab      anahtar kelime tamamlama (supertab uzantisi)
r<c>     <c> karakterini degistir
```

```
*        imlecin altındaki kelimeden sonraki kelimeleri ara
f<c>     mevcut imleç pozisyonundan <c> karakterini bul ör: 3f<c> satırda <c> karakterinin 3. kez görüldüğü yere git
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

#### bul ve değiştir

`:h substitute`:tropical_fish:  
```
:s/eski/yeni      mevcut satırda ilk 'eski'nin görüldüğü yeri 'yeni' ile değiştir
:s/eski/yeni/g    mevcut satırdaki tüm 'eski'leri 'yeni' ile değiştir
:s/eski/yeni/gc   mevcut satırdaki tüm 'eski'leri 'yeni' ile değiştir ama öncesinde onay iste

:#,#s/old/new/g   # ve # satırları (dahil) arasındaki 'eski'leri 'yeni' ile değiştir
:%s/eski/yeni/g   mevcut dosyadaki tüm 'eski'leri 'yeni' ile değiştir
:%s/eski/yeni/gc  mevcut dosyadaki tüm 'eski'leri 'yeni' ile değiştir ama öncesinde onay iste
```

### Bazı sık kullanılanlar 

```
yyp     alt satıra kopyala
yyP     üst satıra kopyala
ddp     alt satırla üst satırı yer değiştir
ea      kelimenin sonuna ekle
xp      yanyana iki harfi yerdeğiştir         ör: microsotf ->  microsoft 
dgg     imleçin bulunduğu yerden dosyanın başına kadar sil
```

### Kişiselleştirme

#### dotfiles ve .vimrc dosyası

`:h vimrc-intro`:tropical_fish:  
`:options`:tropical_fish:  

Unix tabanlı işletim sistemlerinde, sistem araçlarının büyük kısmı C programıdır ve bu programlar bazı parametrelerini dosyaya yazılmış komutlardan alır. Dotfile yani 
nokta ile başlayan dosyalar bu komutları verir ve programların çalışma anında ayarlarını tanımlar. Bu dosyaların ilginç ortaya çıkış hikayesini [burdan](https://plus.google.com/101960720994009339267/posts/R58WgWwN9jp) okuyabilirsiniz.
Noktalı dosyalar pratikte bir sistemden ötekine geçerken kullanışlıdır çünkü sistemi büyük ölçüde en baştan konfigure etmenizi önler. Noktalı dosyaları bir versiyon kontrol sisteminde tutmak iyi bir uygulamadır ve pek çok kullanıcı public şekilde bu repo'ları paylaşır.  

 `.bashrc`, `.profile`, `.vimrc` noktalı dosyalara örnektir.

.vimrc dosyası Vim'in çalışma anında ayarlarını tanımlar. Sistemin kullandığı bir .vimrc ve herbir kullanıcının
*home* dizininde birer .vimrc bulunur. home dizinindeki .vimrc, sistem .vimrc'yi override eder. 
eğer .vimrc home dizininde yoksa `vim .vimrc` ile oluşturabilirsiniz. bkz: [default .vimrc içeriği](https://gist.github.com/anonymous/c966c0757f62b451bffa)

#### mapping 

`:h mapping`:tropical_fish:  

mapping ile uzun komutları kısa komutlara dönüştürebiliriz.
mapleri kalıcı olarak kullanamak için .vimrc dosyasına
eklememiz gerekir.

 üç temel mod için 3 temel mapping çeşidi bulunur:

- normal modda çalışabilicek **nmap**
- insert modda çalışabilicek **imap**
- visual modda çalışabilecek **xmap**

genel formül: 
> map kısayol uzunKomutlar

```
nmap m <C-d>        "normal moddayken, m tuşuna ctrl-d komutlarını (yarım sayfa alta) atamış olduk
imap jk <ESC>       "insert moddayken, jk basıldığında ESC basılmış gibi, normal moda geç
```
Bazı özel karakterler:

`:h key-notation`:tropical_fish:   

| Karakter | Anlamı |
|:---------|-------:|
| `<Esc>` | Esc(ape) |
| `<CR>`  | Enter |
| `<Enter>` | Enter |
| `<Tab>` | Tab |
| `<S-Tab>` | Shift + Tab |
| `<M-d>` | Alt + d |
| `<A-d>` | Alt + d |
| `<Space>` | Space |
| `<BS>`  | Backspace |
| `<Del>` | Delete
| `<S-p>` | Shift + p |


Oluşturduğumuz kısayollar daha önce maplenmiş diğer komutları çakışabileceğinden, komutları mümkün olduğunca no-recursive yapmak iyi bir uygulamadır. 

Seçeceğimiz kısayolun bir başka map tarafından kullanılıp kullanılmadığını öğrenmek için:
```
:verbose map kısayol 
```

aşağıda _o_ yani alt satıra in ve insert moda geç, komutunu 4 kere tekrarlayacığını umduğumuz bu komut
sonsuz döngüye neden olur. _o_ _4o_'yu, _4o_ diğer bir _4o_'yu çağırmaya çalışacaktır.

'nmap o 4o`

mapleri no-recursive için komutun başına *nore* getirilir.

- normal mod için **nnoremap**
- insert mod için **inoremap**
- visual mod için **xnoremap**

bu komut beklediğimiz gibi çalışır, normal moddayken _o_'ya bastığımızda 4 satır alta inip insert 
moda geçer.

```
nnoremap o 4o
```

mapleri dosya tipine göre özelleştirebiliriz: 

```
autocmd FileType cpp nnoremap <f5> :w <bar> !clang++ -stdlib=libc++ -fsyntax-only -std=c++1z % <cr>
autocmd FileType d nnoremap <f8> :call DTest()<cr>
autocmd FileType text nnoremap <C-s> :w <cr>
```

##### leader değişkeni

`:h leader`:tropical_fish:

Bir _leader_ karakteri seçim, map'lerde önek olarak kullanabiliriz.
`let mapleader ="-"` `-` karakterini _leader_ olarak seçtim.
`nnoremap <leader>ve :vsplit $MYVIMRC<cr>` şeklinde bir map tanımından sonra, .vimrc dosyamı düzenlemek
istediğimde, normal modda, `-ve` karakterilerine basmam gerekecek.  
 
bütün mapleri görmek için, `:map`

#### Uzantı ekleme

Vim'e uzantı eklemenin en kolay yolu bir paket yöneticisi kurmak. Birden fazla paket yöneticisi mevcut:

- [Pathogen](https://github.com/tpope/vim-pathogen)
- [Vim8 paketler özelliği](http://vimhelp.appspot.com/repeat.txt.html#packages)
- [NeoBundle](https://github.com/Shougo/neobundle.vim)
- [vim-plug](https://github.com/junegunn/vim-plug)
- [dein.vim](https://github.com/Shougo/dein.vim)
- [minpac](https://github.com/k-takata/minpac/)
- [VAM](https://github.com/MarcWeber/vim-addon-manager)
- [Vundle](https://github.com/VundleVim/Vundle.vim)

##### vim-plug ile uzantı ekleme

vim-plug, Vim için tasarlanmış bir eklenti yöneticisidir. Eklenti yüklemenize, güncellemenize, kullanılmayan eklentileri kaldırmanıza izin verir.

```bash
$ curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
komutunu çalıştırıın ve .vimrc dosyasına şunları ekleyin :

```vims
call plug#begin()
" uzantilar
call plug#end()
```
`call plug#begin()` ve `call plug#end()` vim-plug komutları arasına uzantınızı ekleyin. Vim uzantılarının pek 
çoğu Github üzerınde tutuluyor ve maintain ediliyor. 

Mesela https://github.com/tpope/vim-sensible linkinde tutulan uzantıyı

```vims
call plug#begin()
Plug 'https://github.com/tpope/vim-sensible'
call plug#end()
```
veya

```vims
call plug#begin()
Plug 'tpope/vim-sensible'
call plug#end()
```
şeklinde koyduktan sonra 

`:PlugInstall`

komutuyla yükleyebilirsiniz.

### Kendi uzantınızı yazma
`:h write-plugin`:tropical_fish:   
`:h plugin`:tropical_fish:   

Kendi uzantınızı yazabilirsiniz! Bir Vim uzantısı vimscript dilinde yazılmış bir programdır. Genel olarak aşağıdaki bölümlerden oluşur.

```
MyAwesomePlugin/
.
├── autoload   Dosya tipine göre otomatik yüklenen fonksiyonlar
├── doc        Dökümantasyon dosyası
├── ftdetect   Dosya tipinin algılanması
├── ftplugin   Belli bir dosya tipi için yazılmış uzantı
├── plugin     Uzantı dosyası
├── syntax     Sözdizimini renklendirme dosyası
└── after     
└── indent    
└── compiler   

```

#### Hello World uzantısı
Uzantıyı içeren klasörü `runtimepath`'e ekleyin:

```
set runtimepath+=/path/to/helloworld
```
```
helloworld/
.
├── autoload
│   └── greet.vim
├── plugin
    └── greet.vim
```

```VimScript
" plugin/greet.vim
if exists('g:loaded_greet')
	finish
endif
let g:loaded_greet = 1

command! Greet call greet#hello_world()
```
```VimScript
" autoload/greet.vim
function! greet#hello_world() abort
	echo "Hello World!!"
endfunction
```

Ve bitti, komut modunda `:Greet` ile deneyebilirsiniz.

#### Bazı uzantıların (eksik) listesi

###### Yeni başlayanlar için
* [vim-sensible](https://github.com/tpope/vim-sensible)

###### Kod tamamlama ve Dil istemcisi
* [coc.nvim](https://github.com/neoclide/coc.nvim)
* [LanguageCliient-neovim](https://github.com/autozimu/LanguageClient-neovim)
* [vim-lsc](https://github.com/natebosch/vim-lsc)
* [YouCompleteMe](https://github.com/Valloric/YouCompleteMe)
* [deoplete.vim](https://github.com/Shougo/deoplete.nvim)
* [Neocomplete](https://github.com/Shougo/neocomplete.vim)
* [ncm2](https://github.com/ncm2/ncm2)
* [VimCompletesMe](https://github.com/ajh17/VimCompletesMe)
* [completor.vim](https://github.com/maralla/completor.vim)
* [vim-mucomplete](https://github.com/lifepillar/vim-mucomplete)

###### Dil sunucuları listesi
* [Language Servers](https://langserver.org/):fire:

###### Lint ve sözdizimi kontrolü
* [syntastic](https://github.com/vim-syntastic/syntastic)
* [ALE](https://github.com/w0rp/ale)
* [neomake](https://github.com/neomake/neomake)

###### Snippet
* [Snimate](https://github.com/garbas/vim-snipmate)
* [ultisnips](https://github.com/SirVer/ultisnips)
* [vim-snippets](https://github.com/honza/vim-snippets)
* [neosnippet.vim](https://github.com/Shougo/neosnippet.vim)
* [vim-minisnip](https://github.com/joereynolds/vim-minisnip)

###### Programlama Dili
* [vim-polyglot](https://github.com/sheerun/vim-polyglot)
* [vim-go](https://github.com/fatih/vim-go)
* [rust.vim](https://github.com/rust-lang/rust.vim)
* [vim-cpp-enhanced-highlight](https://github.com/octol/vim-cpp-enhanced-highlight)

###### GUI-like
* [NERDTree](https://github.com/scrooloose/nerdtree)
* [promptline](https://github.com/edkolev/promptline.vim)
* [vim-airline](https://github.com/vim-airline/vim-airline)
* [powerline](https://github.com/powerline/powerline)
* [lightline](https://github.com/itchyny/lightline.vim)

###### Tema ve Renkler
* [vimcolors.com](https://vimcolors.com/)
* [rainglow.io](https://rainglow.io)
* [awesome-vim-colorschemes](https://github.com/rafi/awesome-vim-colorschemes)
* [vim-devicons](https://github.com/ryanoasis/vim-devicons)
* [nerd-fonts](https://github.com/ryanoasis/nerd-fonts)

###### Kullanımı kolaylaştıran uzantılar
* [Surround](https://github.com/tpope/vim-surround)
* [Fugitive](https://github.com/tpope/vim-fugitive)
* [vim-commentary](https://github.com/tpope/vim-commentary)
* [ctrlp](https://github.com/ctrlpvim/ctrlp.vim)
* [vim-ctrlspace](https://github.com/vim-ctrlspace/vim-ctrlspace)
* [vim-capslock](https://github.com/tpope/vim-capslock)
* [vim-repeat](https://github.com/tpope/vim-repeat)
* [NrrwRgn](https://github.com/chrisbra/NrrwRgn)
* [vim-obsession](https://github.com/tpope/vim-obsession)
* [vim-gutentags](https://github.com/ludovicchabant/vim-gutentags)

### Linkler 

#### siteler 

* [Vim.org](https://www.vim.org)
* [Vim Repo](https://github.com/vim/vim)
* [gvim appimages](https://github.com/vim/vim-appimage/releases)
* [neovim.io](https://neovim.io/)
* [neovim nightly builds](https://github.com/neovim/neovim/releases/tag/nightly)
* [vimawesome.com](https://www.vimawesome.com) Vim uzantıları
* [dotfiles.github.io](https://dotfiles.github.io)
* [yet another dotfile manager](https://yadm.io)

#### kitaplar

* Practical Vim: Edit Text at the Speed of Though<sup>1</sup> - Drew Neil
* Modern Vim - Drew Neil
* Learning Vi and Vim Editors - Arnold Robbins, Elbert Hannah
* The VimL Primer: Edit Like a Pro with Vim Plugins and Scripts - Benjamin Klein
* Mastering Vim: Build a software development environment with Vim and Neovim<sup>2</sup> - Ruslan Osipov
* [A Byte of Vim](https://vim.swaroopch.com/) (Online Kitap)

#### kopya kağıtları

* http://www.worldtimzone.com/res/vi.html
* http://www.fprintf.net/vimCheatSheet.html
* https://wiki.archlinux.org/index.php/Vim
* http://www.fprintf.net/vimCheatSheet.html
* https://devhints.io/vimscript


### Vim'i kaynak koddan build etme

Eğer Unix tabanlı bir işletim sistemi kullanıyorsanız Vim veya Vi büyük ihtimalle kuruludur ama Vim bazı uzantıları
kullanmak için default olarak etkinleştirilmemiş özelliklerine ihtiyaç duyar. Bunun için Vim'i kaynak kodundan build
etmek gerekir. 

Hangi özelliklerin etkinleştirildiği dağıtıma göre değişiyor, kontrol etmek için:
`:version`

Git ile repo'yu indirin:

`$ git clone --depth=1 https://github.com/vim/vim.git && cd vim`

build'e başlamadan önce configure adımını gerçekleştirmemiz gerekiyor, etkinleştireceğiniz özelliklere göre
ihtiyaç duyduğunuz kütüphaneler değişiklik gösterecektir.

`./configure --help`

Benim bu adım için kullandığım parametreler:
```shell
$ sudo ./configure --enable-fail-if-missing \
--disable-darwin \
--disable-smack \
--disable-selinux \
--enable-luainterp=yes \
--with-python3-command=python3interp \
--enable-python3interp=yes \
--with-python3-config-dir=/usr/lib/python3.5/config-3.5m-x86_64-linux-gnu \
--enable-cscope \
--disable-netbeans \
--enable-terminal \
--enable-autoservername \
--enable-multibyte \
--disable-rightleft \
--disable-arabic \
--disable-farsi \
--enable-fontset \
--enable-gui=no \
--enable-gtk2-check=no \
--enable-gtk3-check=no \
--enable-athena-check=no \
--enable-nextaw-check=no \
--enable-carbon-check=no \
--disable-gtktest \
--with-compiledby=p1v0t
```
ihtiyaçlarınıza göre sizinkiler farklı olabilir. Bu adımın sonunda build için gerekli dosyalar üretiliyor.
GNU make build aracıyla:

`$ sudo make -j 8`

`-j` parametresi build için kaç tane core adayacımızı söylüyor, daha yüksek kullanırsanız build daha hızlı olacaktır 
ama bu süre boyuncu bilgisayarınız diğer işler için yavaşlayabilir. Bu adımın sonunda çalıştırılabilir dosyalar 
(executable) üretilecektir. Bunları root'un erişebileceği yerlere kopyalamak için:

`$ sudo make install`

Vim'in nereye yükleneceğini *configure* adımında  `prefix` parametresiyle belirleyebilirsiniz. Varsayılan olarak 
`/usr/local` olacaktır. Vim'in nerde olduğunu
`$ which vim`

ile kontrol edebilirsiniz.

Repo'yu silmeyin, son özellikleri deneyimlemek için pull yapıp yukaridaki komutları baştan uygulayın,
*make* yalnizca değişen dosyaları derleyeceğinden build fazla zaman almayacaktır.

-----
Eğer bu belgenin faydalı olduğunu düşünüyorsan star bırakabilirsin ve Twitter'da beni (twitter beni bir bot olarak işaretlemeden önce) takip edebilirsin! [@adembubudak](https://twitter.com/adembudak_)

### Lisans 

<a href="http://www.wtfpl.net/"><img
       src="http://www.wtfpl.net/wp-content/uploads/2012/12/wtfpl-badge-4.png"
       width="80" height="15" alt="WTFPL" /></a>
