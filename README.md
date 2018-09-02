# Vim Kısayolları

> Vim shortcuts in Turkish language.

<img alt="PRs Welcome" src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg" />

## Vim nedir? 

Vim etkili biçimde metin düzenlemek için çok iyi yapılandırılabilir bir metin editorüdür.

##  Vim ne değildir? 

Vim kullanıcılarının elinden tutmak için tasarlanmış bir editör değildir. Bir araçtır, kullanılması
 öğrenilmelidir. Vim kelime işlemci değildir.

## [Vim'den Çıkış](https://stackoverflow.blog/wp-content/uploads/2017/05/country_stuck_vim-1-2-1024x1024.png)

```
<esc> :q! <enter> 

```
* [Dosya oluşturma](#dosya-oluşturma)
* [Vim modları](#vim-modlari)
* [Genel](#genel)
* [Hareketler](#hareketler)
* [Insert moda geçme](#insert-moda-geçme)
* [Birden Fazla Dosyayla Çalışma](#birden-fazla-dosyayla-çalişma)
	* [Tabları kullanma](#tablari-kullanma)
* [Kaydetme](#kaydetme)
* [Komutlari tekrar etme](#komutlari-tekrar-etme)
* [Düzenleme](#düzenleme)
	* [Bul ve Değiştir](#bul-ve-değiştir)
* [Sık kullanılanlar](#sik-kullanilanlar)
* [Yapılandırma](#yapilandirma)
	* [vimrc dosyası](#vimrc-dosyasi)
	* [Mapping](#mapping)
* [Vundle ile uzantı ekleme](#vundle-ile-uzanti-ekleme)
	1. [Kurulum](#kurulum)
	2. [Uzantıyı yükleme](#uzantiyi-yükleme)
	3. [Uzantılar hakkında bilgi](#uzantilar-hakkinda-bilgi)
* [Linkler](#linkler)

## Dosya oluşturma

```
$ vim <enter>
$ vim dosyaAdı
$ vim dizin/dosyaAdı 

```

## Vim modları

```
vim, kullanıcının içeriğe odaklanması için farklı modlar sunar.

normal mod: vim normal olarak bu modda başlar. esc ile bu moda geçilir.
insert mod: editöre text bu modla eklenir. [insert komutları](insert-moda-geçme)nın biriyle bu moda geçilir.
görsel mod: text üzerinde belli alanları seçmek için kullanılır. v ile karakter bazında, v ile satır bazında, c-v ile block bazında görsel moda geçilir.
komut modu: normal moda geçtikten sonra : ile geçilir. komut girilmesini sağlar. her bir komuttan sonra <enter> basılmalıdır. ör. :h ctrl-r <enter>

```
## genel

```
$ vimtutor          vim resmi öğretici metni
:h konu             belirtilen konu hakkında detaylı yardım dosyasını aç, yardım dosyası içindeki hyperlinke tıklamak için imlec linkin altıdayken c-], geri c-[

:q                  kapat
:w                  kaydet/write
:saveas dosyaadı    farklı kaydet
:wa[!]              yaz/kaydet butun pencereler [zorla]
:wq                 kaydet ve çık
:wqa		    bütün tabları kaydet ve çık (write, quit all) bkz: [tabları kullanma](#tablari-kullanma)
:x                  yaz ve çık, wq ile aynı
:q!                 dosya değismişse ve değişiklik kaydedilmeyecekse kapatmaya zorla

```

```
u        	geri al, ör: 4u
c-r      	ileri al
u        	satırdaki tüm değisikliği geri al

s=seconds, m=minute, h=hour, d=day
:earlier #m     dosyayı # dakika önceki haline döndür ör: :earlier 2m  veya :ea 3d
:later #m 	dosyayı # dakika sonraki haline döndür ör: :later 7s  veya  :lat 9h

```

```
y        	seçili bölgeyi kopyala (yank)
yy       	bütün satırı kopyala
p        	yapıstır, satırın altına (paste)
"<reg>y  	seçili bolgeyi registera koplaya (a-z den register) 
c        	seçili bolgeyi kes
"<reg>p  	registera yapistir (a-z den register) 
p        	yapıştır, satırın üstüne
. 		son komutu tekrarla

```

```
:!<cmd>  vim'den ayrılmadan shell'den <cmd> komutunu calistir ör: `!g++ -wall -std=c++14 main.cpp`, `!ruby%`
:sh      shell'e git, exit ile tekrar vim'e dön
c-z      vim'i arka plana gonder (fg geri getirir)

```

## hareketler

```

			        k
h        imlec sola             ^
j        imlec alta        h <     > l
l        imlec saga             v
k        imlec yukarı           j

```

```
0        satır başına
$ 	 satır sonu
<home>   satır başı
<end>	 satır sonu 
```

```
w        sonraki kelimenin başına zıpla (işaretlemelerin ayrı bir kelime olduğu varsayılır)
e        sonraki kelimenin sonuna zıpla
b        kelimenin başına zıpla
```

```
h        ekranin başına zıpla (high)
m        ekranin ortasina zıpla (middle)
l        ekranin altina zıpla (low)
```

```
c-b      tam ekran boyu kadar yukarı git (page up)
c-f      tam ekran boyu kadar aşağı git  (page down)
c-d      yarım ekran aşağı
c-u      yarım ekran yukarı
```

```
zt       imlecin bulunduğu yeri ekranın üstüne getir
z<enter> zt ile aynı
zb 	 imlecin bulunduğu yeri ekranın altına getir
z-	 zb ile aynı
z.       imlecin bulunduğu yeri ekranın ortasına getir
zz 	 z. ile aynı
```
```
%        eşleşen paranteze zıpla
( 	 önceki cümle
) 	 sonraki cümle
{ 	 önceki paragraf
}        sonraki paragraf
[{       mevcut kod blogunun basina zıpla 
]}       mevcut kod blogunun sonuna zıpla 
gd       degisken deklerasyonuna zıpla 

```

```
w        sonraki kelimenin başına zıpla (işaretlemelerin ayrı bir kelime olduğu varsayılır)
e        sonraki kelimenin sonuna zıpla
ge 	 önceki kelimenin sonuna zıpla
b        kelimenin başına zıpla
^        ilk boş olmayan karakter
gg       dosyanin en ustu
g        dosyanin en alti
+ 	 sonraki satır başına
- 	 önceki satır başına
. 	 son komutu tekrarla

```
 
```
e        kelimenin sonuna zıpla (isaretlemelerin kelime olduğu varsayılmaz)
w        kelimenin basina zıpla 
b        geriye dogru kelimenin basina zıpla (isaretleme yok)
#g       # numaralı satıra git ör: 38g
#gg      #g ile aynı

```

## insert moda geçme ##

```
/~~~~~~~~~~\<---esc-----/~~~~~~~~~~\
|normal mod|            |insert mod|
\~~~~~~~~~~/--aaiioo--->\~~~~~~~~~~/
```

```
i        imlecten öncesine text ekle
i        satırın başına ekle
a        imlecten sonra textin sonuna ekle
a        satirin sonuna ekle 
o        imlecin altina yeni bir satir yap ve text ekle 
o        imlecin ustune yeni bir satir yap ve text ekle
s        imlecin altindaki harfi sil 
s        tum satiri sil
cc       mevcut satiri sil
cw       kelimeyi sil
shift-r  kelimeyi olduğu yerde değiştir. (windows'taki insert)

```

## birden fazla dosyayla çalışma 

```
c-ws     	mevcut pencereyi yatay olaral bol (alternatif :split)
 
c-wv     	mevcut pencereyi dikey olarak bol (alternatif :vsplit)
c-ww     	sonraki pencereye zıpla 
```
```
c-warrow 	mevcut pencereden sol/sag/yukari/asagi (ok tuslari) yondeki pencereye zıpla
c-wq		mevcut pencereyi kapat
```
```
c-w#<    	mevcut pencereyi sagdan # kadar yeniden boyutlandir (default 1) 
c-w#>    	mevcut pencereyi saga # kadar yeniden boyutlandir (default 1) 
:res #		yatay bölünmüş pencereyi # kadar yeniden boyutlandır
```
```
c-wh		mevcut pencereyi en sola taşı 
c-wj		mevcut pencereyi en alta taşı 	
c-wk		mevcut pencereyi en üste taşı 	
c-wl 		mevcut pencereyi en sağa taşı
```

```
$ vim -o3 f1.txt f2.txt f3.txt      dosyaları alt üst aynı pencerede aç (horizontally split)
$ vim -o3 f1.txt f2.txt f3.txt      dosyaları yan yana aynı pencerede aç(vertically split)

$ vim f1.txt f2.txt f3.txt          dosyaların her birini aç ama aynı anda sadece birini gör, birbirleri arasında :next ve :prev ile geçiş yap, :n dosyaadı ile yeni dosya ekle

```
### tabları kullanma ###

```
$ vim -p f1.txt f2.txt 		f1.txt ve f2.txt dosyalarını tab şeklinde aç

:tabedit dosyaadı   belirtilen dosyayı yeni bir tabda düzenle
:tabfind dosyaadı   dosyayı yeni bir tabda aç ve düzenle

```
```
:tabn               sonraki tab, normal modda gt, 3gt üçüncü tab, insert modda c-pgdn
:tabp               önceki tab, normal modda gt, insert modda c-pgup
:tabfirst           ilk taba git
:tablast            son taba git

```
```
:tabm {i}           mevcut tabı i+1 inci taba taşı. ör: :tabm 0 mevcut tabı ilk tab yap, :tabm  mevcut tabı son tab yap

```
```
:tabclose i         i numaralı tabı kapat
:tabclose           mevcut tabı kapat
:tabonly            diğer tüm tabları kapat

```
```
:tabs               tabları listele
```

## kaydetme

birden fazla hareketi kaydetmek için oldukça kullanışlı. vim 26 registara sahip (a-z),
1. q ile kaydetmeyi başlat ve kaydetmek istedigin bir register seç. örnek: qa
2. kaydetme modundan esc ile cik.
3. kaydedilen değişikliği @<reg> şeklinde uygula. örnek: @a<enter>
	
```
q[a-z]   kaydetmeye basla, hareketler dahil hersey kaydedilecek
@[a-z]   kaydedilen hareketleri baslat
```


## komutları tekrar etme

**operatör [sayı] hareket** veya **[sayı] operator hareket**

```
c3w 	 veya 3cw, 3 kelime değiştir (cw cw cw)
4j       jjjj 
2w       w w,  iki sonraki kelimenin başına git
2dd 	 2 satırı sil

```


## düzenleme 

```
x        imlecin altindaki karakteri sil
x        imlecten onceki karakteri sil 
dw       sonraki kelimeyi sil 
dw       sonraki kelimeye kadar sil 
d^       satir basina kadar sil
d$       satir sonuna kadar sil 
d        satir sonuna kadar sil d$ ile ayni 
dd       tum satiri sil
dib      parantez blogundaki icerigi sil (ör: fonksiyon argumanlari)

```

```
c-n      metinde daha önce geçmiş kelimeyi tamamla
c-p      metinde daha önce geçmiş kelimeyi tamamla
 
tab      anahtar kelime tamamlama (supertab uzantisi)
r<c>     <c> karakterini degistir

```

```
*        imlecin altindaki kelimeden sonraki kelimeleri ara
f<c>     mevcut imlec pozisyonundan <c> karakterini bul ör: 3f<c> satırda <c> karakterinin 3. kez görüldüğü yere git
'.       son duzenlenen satira zıpla
g;       son duzenlenen pozisyona geri zıpla 

```
```
:ab slm selam	 insert modda 'slm'<space> yazıldığında 'selam' ile değiştir.

```

```
u        seçimi küçük harfe çevir (visual mod)
u        seçimi büyük harfe çevir (visual mod)

```

```
:g/^#/d  # ile başlayan tüm satırları sil
:g/^$/d  tum boş satirlari sil
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

## bazı sık kullanılanlar 

```
yyp     alt satıra kopyala
yyp     üst satıra kopyala
ddp 	alt satırla üst satırı yer değiştir
ea      kelimenin sonuna ekle
xp 	yanyana iki harfi yerdeğiştir	 ör: microsotf ->  microsoft 
dgg     imleçin bulunduğu yerden dosyanın başına kadar sil
```

## yapılandırma

### .vimrc dosyası

.vimrc dosyası vim'in çalışma anında ayarlarını tanımlar. sistemin kullandığı bir .vimrc ve herbir kullanıcının
home dizininde birer .vimrc vardır. home dizinindeki .vimrc sistem .vimrc'yi override eder. 
eğer .vimrc home dizininde yoksa, `vim .vimrc` ile oluşturabilirsiniz. bkz: [default .vimrc içeriği](https://gist.github.com/anonymous/c966c0757f62b451bffa)

### mapping 

mapping ile uzun komutları kısa komutlara dönüştürebiliriz.
mapleri kalıcı olarak kullanamk için .vimrc dosyasına
eklememiz gerekir.

 üç temel mod için 3 temel mapping çeşidi vardır. 

normal modda çalışabilicek nmap
insert modda çalışabilicek imap
visual modda çalışabilecek vmap

genel formül: 
> map kısayol uzunKomutlar

aşağıda m tuşuna ctrl-d komutlarını (yarım sayfa alta) atamış olduk

```
nmap m <C-d>  
```

ama bu komutlar daha önce maplenmiş diğer komutları çakışabileceğinden,
 mümkün mertebe komutları no-recursive yapmak iyi bir uygulamadır. 

aşağıda _o_ yani alt satıra in ve insert moda geç, komutunu 4 kere tekrarlayacığını umduğumuz bu komut
sonsuz döngü neden olur. _o_ _4o_'yu, _4o_ diğer bir _4o_'yu çağırmaya çalışcaktır.

```
nmap o 4o 
```
mapleri no-recursive  için de komutun başına *nore* getirilir.

normal mod için nnoremap
insert mod için inoremap
visual mod için vnoremap

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

## Vundle ile uzantı ekleme

Vundle (Vim bundle) Vim için tasarlanmış bir eklenti yöneticisidir. Eklenti yüklemenize, güncellemenize, kullanılmayan eklentileri kaldırmanıza izin verir.

### Kurulum

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
```Plugin 'GithubKullanıcıAdı/RepoAdı' ``` Ör: ```Plugin 'tpope/vim-fugitive'```
    
- [vimscipt](http://vim-scripts.org/vim/scripts.html) şeklindeki Vim uzantılarını eklemek için:
```Plugin 'uzantıAdı' ```		Ör: ```Plugin 'L9'```

- Github'ta tutulmayan git repoları için:
  Ör: ```Plugin 'git://git.wincent.com/command-t.git'```

- Bilgisayardaki bir git reposu için (mesela kendi uzantını geliştiriyorsundur):
  Ör: ```Plugin 'file:///home/adem/path/to/plugin'```

şekillerinde eklememiz gerekiyor.

### Uzantıyı yükleme

Son adımda uzantıyı yüklemek için:
```
Vim'de
:PluginInstall

shell'de
$vim +PluginInstall +qall
```

### Uzantılar hakkında bilgi

```
:PluginList			uzantıyıları listele
:PluginInstall			uzantıları yükle
:PluginInstall! 		uzantıları güncelle
:PluginSearch <abc>		<abc> uzantısını ara
:PluginClean 			kullanılmayan uzantıları kaldır

```

## Linkler 

### Kopya kağıtları

* http://www.worldtimzone.com/res/vi.html
* http://www.fprintf.net/vimCheatSheet.html
* https://wiki.archlinux.org/index.php/Vim
* http://www.fprintf.net/vimCheatSheet.html
* https://devhints.io/vimscript

### Makaleler 

* Vim notları: https://www.emrah.com/notlar/vim_notlari.txt
* Etkili 7 metin düzenleme alışkanlığı: http://www.moolenaar.net/habits.html
* 11 yıl sonra Vim: http://statico.github.com/vim.html
* Vim'e, eve dönüş: http://stevelosh.com/blog/2010/09/coming-home-to-vim 

### Tavsiye ve Teknikler 

* [vimcasts.org](http://vimcasts.org/) Video-casts on vim
* [usevim.com](http://usevim.com/) Eklenti tanitimlari ve tavsiyeler
* [vimregex.com](http://vimregex.com/) Vim'in regex motoru hakkinda bilgiler 
* [Stackoverflow](http://stackoverflow.com/questions/1218390/what-is-your-most-productive-shortcut-with-vim) Kullanışlı vim kisayollari 
* [r/vim](https://www.reddit.com/r/vim/)
* Practical Vim - Edit Text at the Speed of Though - Kitap

### Siteler 

* Vim - heryerde bulunan editor: https://www.vim.org/
* Vim uzantıları: https://vimawesome.com/
* Belirtilen alıştırmaları en kısa vim komutu kullanarak tamamlama https://vimgolf.com/

### Bazı Uzantılar

* NERDTree
* NERDCommenter
* Ctrl-P
* easytags
* unimpard
* YouCompleteMe

### Licence

 <a href="http://www.wtfpl.net/"><img
       src="http://www.wtfpl.net/wp-content/uploads/2012/12/wtfpl-badge-4.png"
       width="80" height="15" alt="WTFPL" /></a>
