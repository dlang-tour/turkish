# Import Deyimi ve Modüller

D dilinde basit bir _Merhaba Dünya_ programı için, `import` a ihtiyacınız vardır.
`import` deyimi belirtilen **modül**deki bütün public işlevleri ve türleri erişilebilir kılar. 

[Phobos](https://dlang.org/phobos/) adlı standart kütüphane,
`std` **paketi** altında bulunur
ve bu modüller `import std.MODULE` şeklinde gösterilir.

Ayrıca `import` deyimiyle modüldeki belirli sembolleri çağırabilirsiniz.
Bu yazdığınız D kodlarının daha hızlı derlenmesine olanak sağlar.

    import std.stdio: writeln, writefln;

Bir `import` deyimi kaynak kodun en üst satırında bulunmak zorunda değildir.
İşlevlerin içerisinde veya başka bir kapsam (scope) içerisinde kullanılabilir.

## {SourceCode}

```d
void main()
{
    import std.stdio;
    // veya import std.stdio: writeln;
    writeln("Merhaba Dünya!");
}
```
