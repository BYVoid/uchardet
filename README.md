# uchardet

[uchardet](https://github.com/BYVoid/uchardet) is an encoding detector library, which takes a sequence of bytes in an unknown character encoding without any additional information, and attempts to determine the encoding of the text. Returned encoding names are [iconv](https://www.gnu.org/software/libiconv/)-compatible.

uchardet started as a C language binding of the original C++ implementation of the universal charset detection library by Mozilla. It can now detect more charsets, and more reliably than the original implementation.

The original code of universalchardet is available at http://lxr.mozilla.org/seamonkey/source/extensions/universalchardet/

Techniques used by universalchardet are described at http://www.mozilla.org/projects/intl/UniversalCharsetDetection.html

## Supported Languages/Encodings

  * International (Unicode)
    * UTF-8
    * UTF-16BE / UTF-16LE
    * UTF-32BE / UTF-32LE / X-ISO-10646-UCS-4-34121 / X-ISO-10646-UCS-4-21431
  * Bulgarian
    * ISO-8859-5
    * WINDOWS-1251
  * Chinese
    * ISO-2022-CN
    * BIG5
    * EUC-TW
    * GB18030
    * HZ-GB-2312
  * English
    * ASCII
  * Esperanto
    * ISO-8859-3
  * French
    * ISO-8859-1
    * ISO-8859-15
    * WINDOWS-1252
  * German
    * ISO-8859-1
    * WINDOWS-1252
  * Greek
    * ISO-8859-7
    * WINDOWS-1253
  * Hebrew
    * ISO-8859-8
    * WINDOWS-1255
  * Hungarian:
    * ISO-8859-2
    * WINDOWS-1250
  * Japanese
    * ISO-2022-JP
    * SHIFT_JIS
    * EUC-JP
  * Korean
    * ISO-2022-KR
    * EUC-KR
  * Russian
    * ISO-8859-5
    * KOI8-R
    * WINDOWS-1251
    * MAC-CYRILLIC
    * IBM866
    * IBM855
  * Thai
    * TIS-620
    * ISO-8859-11
  * Turkish:
    * ISO-8859-3
    * ISO-8859-9
  * Others
    * WINDOWS-1252

## Installation

### Debian/Ubuntu/Mint

    apt-get install uchardet libuchardet-dev

### Mageia

    urpmi libuchardet libuchardet-devel

### Mac

    brew install uchardet

### Build from source

    cmake .
    make
    make install

## Usage

### Command Line

```
uchardet Command Line Tool
Version 0.0.5

Authors: BYVoid, Jehan
Bug Report: https://github.com/BYVoid/uchardet/issues

Usage:
 uchardet [Options] [File]...

Options:
 -v, --version         Print version and build information.
 -h, --help            Print this help.
 ```
### Library

See [uchardet.h](https://github.com/BYVoid/uchardet/blob/master/src/uchardet.h)

## Related Projects

  * [python-chardet](https://github.com/chardet/chardet) Python port
  * [ruby-rchardet](http://rubyforge.org/projects/chardet/) Ruby port
  * [juniversalchardet](http://code.google.com/p/juniversalchardet/) Java port of universalchardet
  * [jchardet](http://jchardet.sourceforge.net/) Java port of chardet
  * [nuniversalchardet](http://code.google.com/p/nuniversalchardet/) C# port of universalchardet
  * [nchardet](http://www.conceptdevelopment.net/Localization/NCharDet/) C# port of chardet
  * [uchardet-enhanced](https://bitbucket.org/medoc/uchardet-enhanced) A fork of mozilla universalchardet
  * [rust-uchardet](https://github.com/emk/rust-uchardet) Rust language binding of uchardet
  * [libchardet](https://ftp.oops.org/pub/oops/libchardet/) Another C/C++ API wrapping Mozilla code.

## License

[Mozilla Public License Version 1.1](http://www.mozilla.org/MPL/1.1/)
