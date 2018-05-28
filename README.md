# Vim Kısayolları

Vim shortcuts in Turkish language.

## Vim nedir? 

Vim etkili biçimde metin düzenlemek için çok iyi yapılandırılabilir bir metin editorüdür.

##  Vim ne değildir? 

Vim kullanıcılarının elinden tutmak için tasarlanmış bir editör değildir. Bir araçtır, kullanılması öğrenilmelidir. Vim kelime işlemci değildir.

## [Vim'den Çıkış](https://stackoverflow.blog/wp-content/uploads/2017/05/country_stuck_vim-1-2-1024x1024.png)

```
<esc> :q! <enter> 

```
* [Dosya oluşturma](#dosya-oluşturma)
* [Vim modları](#vim-modlari)
* [Genel](#genel)
* [Hareketler](#hareketler)
* [Insert moda geçme](#insert-moda-geçme)
* [Windows](#windows)
	* [Tabları kullanma](#tablari-kullanma)
* [Kaydetme](#kaydetme)
* [Komutlari tekrar etme](#komutlari-tekrar-etme)
* [Düzenleme](#düzenleme)
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
Vim, kullanıcının içeriğe odaklanması için farklı modlar sunar.

Normal mod: Vim normal olarak bu modda başlar. ESC ile bu moda geçilir.
Insert mod: Editöre text bu modla eklenir. [İnsert komutları](insert-moda-geçme)nın biriyle bu moda geçilir.
Görsel mod: Text üzerinde belli alanları seçmek için kullanılır. v ile karakter bazında, V ile satır bazında, C-V ile block bazında görsel moda geçilir.
Komut modu: Normal moda geçtikten sonra : ile geçilir. Komut girilmesini sağlar. Her bir komuttan sonra <enter> basılmalıdır. Ör. :h CTRL-R <enter>

```
## Genel

```
$ vimtutor          vim resmi öğretici metni
:h konu             belirtilen konu hakkında detaylı yardım dosyasını aç, yardım dosyası içindeki hyperlinke tıklamak için imlec linkin altıdayken C-], geri C-[

:q                  kapat
:w                  kaydet/write
:saveas dosyaAdı    farklı kaydet
:wa[!]              yaz/kaydet butun pencereler [zorla]
:wq                 kaydet ve çık
:wqa		    bütün tabları kaydet ve çık (write, quit all) bkz: [Tabları kullanma](#tablari-kullanma)
:x                  yaz ve çık, wq ile aynı
:q!                 dosya değismişse ve değişiklik kaydedilmeyecekse kapatmaya zorla

```

```
u        	Geri al, Ör: 4u
C-r      	İleri al
U        	Satırdaki tüm değisikliği geri al

s=seconds, m=minute, h=hour, d=day
:earlier #m     Dosyayı # dakika önceki haline döndür Ör: :earlier 2m  veya :ea 3d
:later #m 	Dosyayı # dakika sonraki haline döndür Ör: :later 7s  veya  :lat 9h

```

```
y        	Seçili bölgeyi kopyala (yank)
yy       	Bütün satırı kopyala
p        	Yapıstır, satırın altına (paste)
"<reg>y  	Seçili bolgeyi registera koplaya (a-z den register) 
c        	Seçili bolgeyi kes
"<reg>p  	Registera yapistir (a-z den register) 
P        	Yapıştır, satırın üstüne
. 		Son komutu tekrarla

```

```
:!<cmd>  Vim'den ayrılmadan shell'den <cmd> komutunu calistir Ör: !g++ -Wall -std=c++14 main.cpp
:sh      Shell'e git, exit ile tekrar Vim'e dön
C-z      Vim'i arka plana gonder (fg tekrar geri getirir)

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
$ 	 satır sonu
<Home>   satır başı
<End>	 satır sonu 
```

```
w        sonraki kelimenin başına zıpla (işaretlemelerin ayrı bir kelime olduğu varsayılır)
e        sonraki kelimenin sonuna zıpla
b        kelimenin başına zıpla
```

```
H        Ekranin başına zıpla (High)
M        Ekranin ortasina zıpla (Middle)
L        Ekranin altina zıpla (Low)
```

```
C-b      Bir tam ekran yukari git (page up)
C-f      Bir tam ekran asagi git  (page down)
C-d      Bir yarim ekran asagi git
C-u      Bir yarim ekran yukari git
```

```
zt       İmlecin bulunduğu yeri ekranın üstüne getir
z<enter> zt ile aynı
zb 	 İmlecin bulunduğu yeri ekranın altına getir
z-	 zb ile aynı
z.       İmlecin bulunduğu yeri ekranın ortasına getir
zz 	 z. ile aynı
```
```
%        eslenen paranteze zipla
( 	 önceki cümle
) 	 sonraki cümle
{ 	 önceki paragraf
}        sonraki paragraf
[{       mevcut kod blogunun basina zipla 
]}       mevcut kod blogunun sonuna zipla 
gd       degisken deklerasyonuna zipla 

```

```
w        sonraki kelimenin başına zıpla (işaretlemelerin ayrı bir kelime olduğu varsayılır)
e        sonraki kelimenin sonuna zıpla
ge 	 önceki kelimenin sonuna zıpla
b        kelimenin başına zıpla
^        ilk bos olmayan karakter
gg       dosyanin en ustu
G        dosyanin en alti
+ 	 sonraki satır başına
- 	 önceki satır başına
. 	 son komutu tekrarla

```
 
```
E        Kelimenin sonuna zipla (isaretlemelerin kelime olduğu varsayılmaz)
W        Kelimenin basina zipla 
B        Geriye dogru kelimenin basina zipla (isaretleme yok)
#G       # numaralı satıra git Ör: 38G
#gg      #G ile aynı

```

## Insert moda geçme ##

```
i        İmlecten öncesine text ekle
I        Satırın başına ekle
a        İmlecten sonra textin sonuna ekle
A        Satirin sonuna ekle 
o        İmlecin altina yeni bir satir yap ve text ekle 
O        İmlecin ustune yeni bir satir yap ve text ekle
s        İmlecin altindaki harfi sil 
S        Tum satiri sil
cc       Mevcut satiri sil
cw       Kelimeyi sil
Shift-r  Kelimeyi olduğu yerde değiştir. (Windows'taki insert)

```

## Windows ##

```
C-ws     	Mevcut pencereyi yatay olaral bol (alternatif :split)
C-wv     	Mevcut pencereyi dikey olarak bol (alternatif :vsplit)
C-ww     	Sonraki pencereye zipla 
C-wq		Mevcut pencereyi kapat
C-wARROW 	Mevcut pencereden sol/sag/yukari/asagi (ok tuslari) yondeki pencereye zipla
C-w#<    	Mevcut pencereyi sagdan # kadar yeniden boyutlandir (default 1) 
C-w#>    	Mevcut pencereyi saga # kadar yeniden boyutlandir (default 1) 
:res #		Yatay bölünmüş pencereyi # kadar yeniden boyutlandır
C-wH		Mevcut pencereyi en sola taşı 
C-wJ		Mevcut pencereyi en alta taşı 	
C-wK		Mevcut pencereyi en üste taşı 	
C-wL 		Mevcut pencereyi en sağa taşı
```

```
$ vim -o3 f1.txt f2.txt f3.txt      Dosyaları yan yana aynı pencerede aç (horizontally split)
$ vim -O3 f1.txt f2.txt f3.txt      Dosyaları alt üst aynı pencerede aç (vertically split)

$ vim f1.txt f2.txt f3.txt          Dosyaların her birini aç ama aynı anda sadece birini gör, birbirleri arasında :next ve :prev ile geçiş yap, :n dosyaAdı ile yeni dosya ekle

```
### Tabları kullanma ###

```
$ vim -p f1.txt f2.txt 		f1.txt ve f2.txt dosyalarını tab şeklinde aç

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

## Kaydetme

Vim 26 registara sahip (a-z), kaydetmek istedigin bir tanesini sec. Kaydetme modundan ESC ile cik
```
q[a-z]   Kaydetmeye basla, Hareketler dahil hersey kaydedilecek
@[a-z]   Kaydedilen hareketleri baslat
```


## Komutları tekrar etme

**operatör [sayı] hareket** veya **[sayı] operator hareket**

```
c3w 	 veya 3cw, 3 kelime değiştir (cw cw cw)
4j       jjjj 
2W       W W,  iki sonraki kelimenin başına git
2dd 	 2 satırı sil

```


## Düzenleme 

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
*        imlecin altindaki kelimeden sonraki kelimeleri ara
f<c>     mevcut imlec pozisyonundan <c> karakterini bul Ör: 3f<c> satırda <c> karakterinin 3. kez görüldüğü yere git
'.       son duzenlenen satira zipla
g;       son duzenlenen pozisyona geri zipla 

```

```
:s/xxx/yyy/    xxx'i yyy'nin ilk görüldüğü yerde değiştir
:s/xxx/yyy/g   xxx'i yyy'nin goruldugu yerde değiştir, tumcede (global)
:s/xxx/yyy/gc  xxx'i yyy'nin goruldugu yerde değiştir ama onay iste, tumcede
:%s/xxx/yyy/g  xxx'i yyy'nin goruldugu yerde değiştir, tum dosyada

```

```
:ab slm selam	 insert modda 'slm'<space> yazıldığında 'selam' ile değiştir.

```

```
u        Seçimi küçük harfe çevir (visual mod)
U        Seçimi büyük harfe çevir (visual mod)

```

```
:g/^#/d  # ile baslayan tum satirlari sil
:g/^$/d  Tum bos satirlari sil
```

## Sık kullanılanlar 

```
yyp     Alt satıra kopyala
yyP     Üst satıra kopyala
ddp 	Alt satırla üst satırı yer değiştir
ea      Kelimenin sonuna ekle
xp 	Yanyana iki harfi yerdeğiştir	 Ör: Microsotf ->  Microsoft 
dgg     İmleçin bulunduğu yerden dosyanın başına kadar sil
```

## Yapılandırma

### .vimrc dosyası

.vimrc dosyası Vim'in çalışma anında ayarlarını tanımlar. Sistemin kullandığı bir .vimrc ve herbir kullanıcının
HOME dizininde birer .vimrc vardır. HOME dizinindeki .vimrc sistem .vimrc'yi override eder. 
Eğer .vimrc HOME dizininde yoksa, `vim .vimrc` ile oluşturabilirsiniz. Bkz: [Default .vimrc içeriği](https://gist.github.com/anonymous/c966c0757f62b451bffa)

### Mapping 

mapping ile klavye kısayolu atayabilir, Vim'in default davranışlarını değiştirebilirsin.

```
:map Y y$
```
Yukarıdaki komut Y komutunun davranışını override eder. Y önceden bütün satırı kopyalarken, yy ile aynı, 
şimdi imlecin bulunduğu yerden satır sonuna kadarki kısmı kopyalar.

```
:imap jj <Esc>
```
Bu komut insert moddayken jj'ye bastığımızda, <Esc> basılmış olarak algılar ve normal moda geçerir.

```
:map		normal,görsel ve komut modundaki mapping'leri listele
:map! 		insert ve komut modundaki mapping'leri listele

:nmap 		normal mod mapping'lerini listele
:vmap	 	görsel mod mapping'lerini listele	
:imap		insert mod mapping'lerini listele
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
* Practical Vim - Edit Text at the Speed of Though - Kitap

### Siteler 

* Vim - heryerde bulunan editor: https://www.vim.org/
* Vim uzantıları: https://vimawesome.com/
* Belirtilen alıştırmaları en kısa vim komutu kullanarak tamamlama https://vimgolf.com/

### Uzantılar

* NERDTree
* NERDCommenter
* Ctrl-P
* easytags
* unimpard
* supertab
* tagbar
* omnicomplete (C++)
