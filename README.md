### dart runtime libs

This repo contains binaries and the one header file needed to embed the [dart][dartlang] runtime in a C / C++ app.  Currently only includes OS X binaries build with libc++ / i386.

Here are google's [checkout][checkout] and [build][build] instructions, although I built these with the dart.xcodeproj that is generated after the `gclient sync` command.

### steps to rebuild dart static binaries for cinder


Mac OS X (32-bit):

1. Checkout dart's svn repo following [these instructions][checkout] (I ran into problems with the git instructions…).
* Run glient sync. You need google's depot_tools for this, you can find that with the above link.
* Last step generates a dart/dart.xcodeproj file, open it up. It's really a workspace containaing all sorts of stuff.
* Open the project settings for dart-runtime.xcodeproj, swicth the 'C++ Standard Library' to 'libc++'.  Leave the C++ dialect set to compiler default - the code doesn't build (as of this writing) when set to C++11.
* open up dart-runtime.xcodeproj / Source / platform / globals.h and go to the section where they bodly re-#define memcpy (line 431 as of this writing), comment that out since we need it to build with libc++.
* *.a binaries (and snapshot_gen.bin) should be in dart/xcodebuild/Debug (or Release).

[dartlang]: http://www.dartlang.org/
[checkout]: https://code.google.com/p/dart/wiki/GettingTheSource
[build]: https://code.google.com/p/dart/wiki/Building#Building_everything