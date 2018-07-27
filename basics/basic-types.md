# Temel Veri Türleri

D dilinde platformdan **bağımsız** olarak her zaman aynı
boyutta olan temel veri türleri vardır. Tek istisna, mümkün 
olan en geniş aralıkta kayan noktalı sayılarda(floating point)
sağlayan `real` veri türüdür. `Int` (tam sayı) veri türünün boyutu,
uygulamanın 32 bit veya 64 bite derlenmesinden etkilenmez ve her
zaman aynıdır.

| tür                           | boyut
|-------------------------------|------------
|`bool`                         | 8-bit
|`byte`, `ubyte`, `char`        | 8-bit
|`short`, `ushort`, `wchar`     | 16-bit
|`int`, `uint`, `dchar`         | 32-bit
|`long`, `ulong`                | 64-bit

#### Kayan Noktalı Sayı Türleri:

| tür     | boyut
|---------|--------------------------------------------------
|`float`  | 32-bit
|`double` | 64-bit
|`real`   | >= 64-bit (genellikle 64-bit, Intel x86 da 80-bit)

`u` öneki `unsigned` (işaretsiz) tür anlamına gelir.
`char` UTF-8 karakterine çevirilirken, `wchar` UTF-16 karakter dizisinde ve `dchar`
UTF32 karakter dizisinde kullanılır.

Farklı türdeki değişkenler arasındaki tür dönüşümleri veri kaybı olmadığı sürece
izin verilir. Ancak, kayan noktalı sayılarda (örneğin `double` veri türünden
`float` veri türüne) dönüşümlere izin verilir. 

Başka veri türüne dönüşümü `cast(TÜR) değişken` ile zorunlu kılabilirsiniz.
Fakat bu özellik dikkatlice kullanılmalıdır. `cast` ifadesi tür yapısını
bozabilir.

Özel anahtar kelime `auto`, bir değişken oluşturur ve değişkenin türü
ifadenin sağ tarafından (right hand side) çıkarım yapılarak belirlenir.
`auto yaş = 19;` ifadesinde `yaş` değişkenini `int` türünde olmasını
sağlayacaktır. Fakat değişkenin türü, türü belirtilmiş diğer
değişkenler gibi derleme zamanında (compile-time) belirlenir
ve sonradan değiştirilemez. 

### Tür Nitelikleri

Tüm veri türlerinin ilk değerini gösteren `.init` niteliği vardır. 
Bütün tam sayılar için `0` ve kayan noktalı sayılar için ise `nan` sayı değil
(*not a number*) başlangıç değeridir.

Tam sayı ve kayan noktalı sayılarda, atanabilecek en yüksek değeri gösteren
`.max` niteliği vardır. Tam sayılar, atanabilecek en küçük değeri ifade eden
`.min` niteliğine sahipken kayan noktalı sayılarda 0'dan farklı en küçük değeri
ifade eden `.min_normal` niteliğine sahiptir.

Kayan noktalı sayılar ayrıca `.nan` (NaN değeri), `.infinity` (sonsuz değeri), `.dig`
(hassasiyetteki ondalık rakam sayısı), `.mant_dig` (mantissadaki bit sayısı)
gibi daha bir çok niteliğe sahiptir.

Her türün ayrıca türün okunaklı ismini döndüren `.stringof` niteliği vardır.

### D Dilinde İndeksler

İndeksler genellikle `size_t` takma adına sahiptir. Bu tür erişilebilir
hafızadaki bütün ofsetleri temsil edebilecek büyüklüktedir.
32 bit mimari için `uint`, 64 bit mimari içinse `ulong` veri türünün takma adıdır.

### Assert İfadeleri

`assert`, debug modunda çalışarak koşulları doğrular ve koşul sağlanmadığında
`AssertionError` ile programı durdurur.

Bu yüzdendir ki `assert(0)` erişelemez kodu işaretlemek için kullanılır.

### Geniş Kapsamlı

#### Temel Kaynaklar

- [Atama](http://ddili.org/ders/d/atama_ve_sira.html)
- [Değişkenler](http://ddili.org/ders/d/degiskenler.html)
- [Aritmetik](http://ddili.org/ders/d/aritmetik_islemler.html)
- [Kesirli Sayılar](http://ddili.org/ders/d/kesirli_sayilar.html)
- [_D Programlama Dilinde_ Temel Türler](http://ddili.org/ders/d/temel_turler.html)

#### İleri Seviye Kaynaklar

- [D dilindeki bütün veri türlerine genel bakış](https://dlang.org/spec/type.html)
- [`auto` ve `typeof`](http://ddili.org/ders/d/auto.html)
- [Nitelikler](http://www.ddili.org/ders/d/nitelikler.html)
- [Assert İfadeleri](http://www.ddili.org/ders/d/assert.html)

## {SourceCode}

```d
import std.stdio : writeln;

void main()
{
    // Büyük sayılar okunabilirliği
    // artırmak için "_"
    // ile ayrılabilir.
    int b = 7_000_000;
    short c = cast(short) b; // dönüşüm gereklidir
    uint d = b; // Uygun
    int g;
    assert(g == 0);

    auto f = 3.1415f; // f, float olduğunu belirtir.

    // typeid(DEĞİŞKEN) ifadenin tür bilgisini döndürür
    writeln("f nin türü = ", typeid(f));
    double pi = f; // Uygun
    // kayan noktalı sayı türleri için
    // daha küçük kayan noktalı sayılara
    // dönüşüme izin verilir.
    float daha_küçük = pi;

    // Tür niteliklerine erişim
    assert(int.init == 0);
    assert(int.sizeof == 4);
    assert(bool.max == 1);
    writeln(int.min, " ", int.max);
    writeln(int.stringof); // int
}
```
