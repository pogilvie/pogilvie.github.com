---
title:  "My Solution to running Ruby on a M1 Mac"
description: "story of trying to get ruby to run on an M1 Mac"
pubDate: Aug 12 2021
---

### Problem

Trying to use the Jekyll microblogging framework results in errors show below on Apple Silicon Macs (M1 processor)

```
LoadError - dlopen(/Library/Ruby/Gems/2.6.0/gems/ffi-1.15.4/lib/ffi_c.bundle, 0x0009): missing compatible arch in /Library/Ruby/Gems/2.6.0/gems/ffi-1.15.4/lib/ffi_c.bundle
```

This happens even through the ffi_c library is arm64 and the version of ffi_c is up to date. 

```
-> file /Library/Ruby/Gems/2.6.0/gems/ffi-1.15.4/lib/ffi_c.bundle
/Library/Ruby/Gems/2.6.0/gems/ffi-1.15.4/lib/ffi_c.bundle: Mach-O 64-bit bundle arm64
```

The root of the issue seems to be that the Ruby runtime system encodes a *single* binary architecture configuration at build time and cannot accomodate Apple's concept of a universal binary, which contains both an X86_64 binary and an Arm64 binary.  Apple built and shipped a univeral binary but had to choose one or the other in their Ruby build configuration and chose X86_64.  Since Apple has announed it will discontinue shipping Ruby with future versions of the OS no fix will ever appear from Apple.  It's probably for the best because support from the Ruby community for the concept of a universal binary is probably not going to happen either.

All of this is well explained by [Martin Albrech](https://betterprogramming.pub/ruby-on-apple-silicon-m1-macs-fb159849b2f5)

### Solution

```
-> brew install ruby
```

Make sure to update your path to find the new Ruby at */opt/homebrew/opt/ruby/bin*.

```
-> which ruby
/opt/homebrew/opt/ruby/bin/ruby
-> ruby --version
ruby 3.0.2p107 (2021-07-07 revision 0db68f0233) [arm64-darwin20]
```

Make sure the bundler is coming from the homebrew installation.

```
-> which bundle
/opt/homebrew/opt/ruby/bin/bundle
```

Then update the project.

```
-> bundle update
-> bundle exec jekyll serve
```

