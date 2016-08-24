# Bellek Yönetimi

D bir sistem programlama dilidir ve bu sayede belleği elle yönetebilirsiniz.
Fakat elle bellek yönetimi oldukça hataya eğilimlidir bu yüzden 
D varsayılan olarak kullanılmayan belleği temizlemek için *çöp toplayıcı (garbage collector)* kullanır.

D, C dilinde olduğu gibi `T*` şeklinde işaretçiler sağlar

    int a;
    int* b = &a; // b, a değişkeninin adresini tutar.
    auto c = &a; // c, bir int* ve a değişkeninin adresini tutar.

Yığında yeni bir bellek alanı `new` ifadesi ile oluşturulabilir. Bu `new` ifadesi yönetilen bellek alanının 
adresini gösteren bir işaretçi döndürür:

    int* a = new int;

a değişkeni tarafından gösterilen bellek alanı, program içerisindeki hiçbir değişken tarafından gösterilmediğinde
çöp toplayıcı bu bellek alanını temizler

D ayrıca işaretçi aritmetiğini destekler. Fakat @safe ile işaretlenmiş kodlar hariç.

    void main() @safe {
        int a = 5;
        int* p = &a;
        int* c = p + 5; // hata
    }

Aksi belirtilmedikçe varsayılan nitelik `@system` dir.
D dilinde bellek sızıntılarını önleyen `@safe` niteliği vardır.
`@safe` kod sadece diğer `@safe` ve `@trusted` işlevleri çağırabilir.
`@trusted` işlevler elle onaylanmış işlevlerdir. SafeD dünyası ile temel düşük-seviye dünyası arasında köprü kurar.

### Derinlemesine

* [SafeD](https://dlang.org/safed.html)

## {SourceCode}

```d
import std.stdio;

void safeFun() @safe
{
    writeln("Merhaba Dünya");
    // Çöp toplayıcı ile
    // bellek alanı oluşturmak güvenli
    int* p = new int;
}

void unsafeFun()
{
    int* p = new int;
    int* fiddling = p + 5;
}

void main()
{
    safeFun();
    unsafeFun();
}
```
