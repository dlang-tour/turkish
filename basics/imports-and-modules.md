# Import ve Modül Sistemi

{{#img-right}}turtle.svg{{/img-right}}

D dilinin ana tasarım amacı tutarlı olmak ve uç durumlardan uzak durmaktır.
Bu durum [_turtles all the way down_](https://en.wikipedia.org/wiki/Turtles_all_the_way_down) olarak söylenir.
Bu durumun iyi bir örneği ise `import` ifadesidir. 

## Import

D dilindeki basit bir merhaba dünya uygulaması için, `import` gereklidir.
`import` ifadesi verilen `modül`deki herkese açık tüm (public) işlev (function) ve türleri
kullanılabilir/erişilebilir kılar.

### The turtles start falling down

Bir `import` ifadesi kaynak kodun en üst satırında bulunmak zorunda __değil__. 
Yerel bir şekilde işlevlerin ya da kapsamların içerisinde kullanılabilir.
Bir sonraki bölümde bunun D dilindeki neredeyse bütün kavramlarda uygulandığını göreceksiniz.
D dili nedensizce kısıtlamalar uygulamaz.

### Seçici Import
Herkesçe kabul edilen kütüphane, [Phobos](https://dlang.org/phobos/),
`std` paketinin içindedir ve modüllere `import std.MODÜL` şeklinde erişilir.

Ayrıca `import` ifadesi modülün içinden belirli sembolleri seçmek için de kullanılabilir.

    import std.stdio : writeln, writefln;

Seçici import, okunabilirliği arttırmak ve bir sembolün nereden geldiğini
göstermek için kullanılabilir. Ayrıca farklı modüllerdeki aynı isme sahip
semboller arasındaki çakışmayı engellemek için kullanılabilir.

### Dizin ve Dosyalarla Eşleşme

D'nin modül sistemi - diğer sistemlere kıyasla - tamamen dosya bazlıdır. 
Örneğin, 'benim.kedim' her zaman `benim` klasörü içerisindeki `kedim.d` dosyasını gösterir.
`benim` klasörü şu anki çalışma dizini içerisinde veya tanımlanmış dizinlerden
(dmd derleyicisine `-I` argümanı ile tanımlanır) birinde bulunmalıdır.
Son olarak, büyük modülleri bir çok ufak dosyaya bölmek için `kedim.d` dosyası
yerine `kedim/` klasörü kullanılabilir.
D derleyicisi bu durumda `benim/kedim.d` dosyası yerine `benim/kedim/package.d` dosyasını
yükleyecektir.

`package.d` için gelenek (zorunlu değil), aynı dizindeki diğer modülleri `public`
olarak import etmektir. 

## {SourceCode}

```d
void main()
{
    import std.stdio;
    // veya import std.stdio : writeln;
    writeln("Merhaba Dünya!");
}
```
