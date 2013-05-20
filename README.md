### dart runtime libs

This repo contains binaries and the one header file needed to embed the [dart][dartlang] runtime in a C / C++ app.  Currently only includes OS X binaries build with libc++ / i386.

Here are google's [checkout][checkout] and [build][build] instructions, although I built these with the dart.xcodeproj that is generated after the `gclient sync` command.

TODO: add specific rebuild instructions

[dartlang]: http://www.dartlang.org/
[checkout]: https://code.google.com/p/dart/wiki/GettingTheSource
[build]: https://code.google.com/p/dart/wiki/Building#Building_everything