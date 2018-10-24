GNU libiconv with UTF-8-MAC support (Port from Apple's libiconv)
======================================================================

  * Copyright (c) 2018-2019 SATOH Fumiyasu @ OSS Technology Corp., Japan
  * License: GNU General Public License Version 3 (iconv program and docs),
             GNU Library General Public License Version 2 (libraries)
  * Development home: <https://github.com/fumiyas/libiconv-utf8mac>
  * Author's home: <https://fumiyas.github.io/>

Works
======================================================================

* Base source: GNU libiconv 1.16 
* UTF-8-MAC support: Apple libiconv-51.200.6 (utf8mac.h)
* My works:
    * Port UTF-8-MAC support to Linux, Solaris, AIX 
    * Support surrogate pairs

Building libiconv program and libraries from the Git repository
======================================================================

On Debian or Ubuntu system:

```console
$ sudo apt install gcc make autoconf automake gperf gettext groff gnulib git
...
$ git clone https://github.com/fumiyas/libiconv-utf8mac.git
...
$ cd libiconv-utf8mac
$ make -f Makefile.utf8mac autogen
...
$ ./configure
...
$ make
...
$ sudo make install
...
$ /usr/local/bin/iconv -l |grep UTF-8-MAC
UTF-8-MAC UTF8-MAC
```

Make a libiconv source tar ball
======================================================================

```console
$ make -f Makefile.utf8mac dist
...
```

Note
======================================================================

UTF-8-MAC is a NFD-like normalization form, not the NFD!!!!

| Original      | UTF-8-MAC             | NFD           |
| ------------- | --------------------- | ------------- |
| 福 (U+FA1B)   | ←                    | 福 (U+798F)   |
| 神 (U+FA19)   | ←                    | 神 (U+795E)   |
| づ (U+3065)   | づ (U+3064 U+3099)    | ←            |
| け (U+3051)   | ←                    | ←            |

TODO
======================================================================

* Add UTF-8-NOMAC encoding (NFC-like normalization form)
