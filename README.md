### dart runtime libs

This repo contains binaries and the one header file needed to embed the [dart][dartlang] runtime in a C / C++ app.  Currently only includes OS X binaries build with libc++ / i386.

Here are google's [checkout][checkout] and [build][build] instructions, although I built these with the dart.xcodeproj that is generated after the `gclient sync` command.

### steps to rebuild dart static binaries for cinder


Mac OS X (32-bit):


__Directions for building with git-svn:__

(which is my personal experience when following the [official instructions][checkout])

Install depot tools:

```
cd <directory where you want the depot_tools to live>
svn co http://src.chromium.org/svn/trunk/tools/depot_tools
export PATH=$PATH:`pwd`//depot_tools
```

Get source with gclient and git svn:
 
```
svn ls https://dart.googlecode.com/svn/branches/bleeding_edge/
mkdir dart-git
cd dart-git
gclient config https://dart.googlecode.com/svn/branches/bleeding_edge/deps/all.deps
git svn clone -rHEAD https://dart.googlecode.com/svn/branches/bleeding_edge/dart dart
gclient sync
gclient runhooks
```

Open Xcode project at dart/runtime/dart-runtime.xcodeproj. Build target 'All', .a binaries will be in dart/xcodebuild/Debug.

To generate the library snapshop binary, run the followinng from xcodebuild/Debug:

```
./gen_snapshot --snapshot=snapshot_gen.bin
```


[dartlang]: http://www.dartlang.org/
[checkout]: https://code.google.com/p/dart/wiki/GettingTheSource
[build]: https://code.google.com/p/dart/wiki/Building#Building_everything