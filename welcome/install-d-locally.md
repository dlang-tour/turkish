# D Kurulumu

D dili resmi internet sitesinden [dlang.org](https://dlang.org) 
tavsiye edilen **DMD** (Digital Mars D) derleyicisinin en güncel halini
[indirebilir](http://dlang.org/download.html) ve yükleyebilirsiniz:

### Windows

* [Kurulum Dosyası](http://downloads.dlang.org/releases/2.x/{{latest-release}}/dmd-{{latest-release}}.exe)
* yada: [Arşiv](http://downloads.dlang.org/releases/2.x/{{latest-release}}/dmd.{{latest-release}}.windows.7z)
* [chocolatey](https://chocolatey.org/packages/dmd) kullanarak: `choco install dmd`

### macOS

* `.dmg` [paketi](http://downloads.dlang.org/releases/2.x/{{latest-release}}/dmd.{{latest-release}}.dmg)
* yada: [Arşiv](http://downloads.dlang.org/releases/2.x/{{latest-release}}/dmd.{{latest-release}}.osx.tar.xz)
* [Homebrew](http://brew.sh) kullanarak: `brew install dmd`

### Linux / FreeBSD / macOS

DMD'yi hızlıca kullanıcı dizinine yüklemek için `curl -fsS https://dlang.org/install.sh | bash -s dmd` komutunu çalıştırınız.

Çeşitli dağıtımlar için sağlanan paketler:

* [ArchLinux](https://wiki.archlinux.org/index.php/D_(programming_language))
* [Debian/Ubuntu](http://d-apt.sourceforge.net).
* [Fedora/CentOS](http://dlang.org/download.html#dmd)
* [Gentoo](https://wiki.gentoo.org/wiki/Dlang)
* [OpenSuse](http://dlang.org/download.html#dmd)

### Diğer Derleyiciler

Kendi arayüzünü kullanan tavsiye edilen DMD derleyicisinin dışında, [dlang.org](https://dlang.org) adresinden de indirebileceğiniz iki adet derleyici daha bulunmaktadır:

* GCC arayüzünü kullanan [**GDC**](http://gdcproject.org/downloads)
* LLVM arayüzünü kullnanan [**LDC**](https://github.com/ldc-developers/ldc#installation)

GDC ve LDC, DMD ön arayüzünün en son haliyle her zaman aynı olmayabiliyor.
Fakat diğer platformlar için (örn ARM) daha iyi iyileştirmeler sağlayabiliyor.

[Daha fazla bilgi](https://wiki.dlang.org/Compilers) için göz atın.
