# D'ye Hoş geldiniz

Etkileşimli D Programlama Dili turuna hoş geldiniz.

{{#dmanmobile}}

Bu tur, doğrudan __doğal makine kodu__na derlenen __güçlü__ ve __etkileyici__ D dilinin bir tanıtımıdır.

{{/dmanmobile}}

### D Nedir?

D _onlarca yıllık derleyici yazma tecrübesi_nin birikimiyle oluşmuş çok sayıda [eşsiz özelliğe](http://dlang.org/overview.html) sahip bir dildir:

{{#dmandesktop}}

- ileri düzey modelleme gücü için _yüksek seviye olanaklar_
- _yüksek performans_, derlemeli dil
- statik tür tanımlaması (static typing)
- işletim sistemi arayüzüne ve donanımına doğrudan erişim
- inanılmaz hızlı derleme süresi
- güvenli bellek yönetimi (SafeD)
- _kolay anlaşılır_, _düzenlenebilir_ kod
- kolay öğrenilebilir (C benzeri sözdizimi, Java ve diğer dillere benzer)
- C ABI (application binary interface) ile uyumlu
- kısıtlı C++ ABI uyumluluğu
- çoklu-paradigma (imperative (emirli), yapısal, nesne tabanlı, generic (türden bağımsız), fonksiyonel programlama, purity (saflık) ve hatta assembly)
- dile gömülü hata yakalama (contracts (sözleşmeler), unittest (birim testleri))

... ve daha birçok [özellik](http://dlang.org/overview.html).

{{/dmandesktop}}

### Tur Hakkında

Her bölüm düzenlenebilen kod örnekleri içerir. Bu sayede D dilinin özelliklerini tarayıcınızda deneyebilirsiniz. Çalıştır düğmesine basarak (veya `Ctrl-Enter` ile) programı derleyip çalıştırabilirsiniz.

Sayfalar arasında geçiş yapmak için sayfadaki "`<` önceki" and "sonraki `>`" linklerini veya sağ/sol ok tuşlarını kullanabilir yada menüden direk istediğiniz bir bölüme atlayabilirsiniz.

### Katkıda Bulun

Bu tur [açık kaynak kodludur](https://github.com/dlang-tour) ve turu daha da iyileştirmek yapmak için katkıda bulunmaktan çekinmeyin.

## {SourceCode}

```d
import std.stdio;
import std.algorithm;
import std.range;

void main()
{
    // Hadi başlayalım!
    writeln("Merhaba Dünya!");
    
    // Tecrübeli programcılar için bir örnek:
    // Üç diziyi yeni bellek ayırmadan
    // birbiri içinde sırala
    int[] arr1 = [4, 9, 7];
    int[] arr2 = [5, 2, 1, 10];
    int[] arr3 = [6, 8, 3];
    sort(chain(arr1, arr2, arr3));
    writefln("%s\n%s\n%s\n", arr1, arr2, arr3);
    // Bu örnekle ilgili daha fazla öğrenmek
    // için "D'nin Cevherleri" kategorisinden
    // "Range algoritmaları" sayfasına
	// bakabilirsiniz
}
```
