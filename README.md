# objcheck

`objcheck` tests Objective-C and Objective-C++ code against both Clang and GCC automatically.

## Why `objcheck`?

Currently, the major Objective-C compilers, Clang and GCC, are not totally compatible at code level. If wanting to check compiler compatibility for our Objective-C code base, we have to compile it twice.

It is tedious to write Makefile or another project configuration file for each code base. To address this issue, `objcheck` automatically tests your code base against both Clang and GCC without any project configuration file.

`objcheck` intends to check small code base because `objcheck` doesn't rely on any external project configuration, unsuitable for large and complex projects.

## System Requirements

`objcheck` itself is implemented in POSIX shell. Besides a shell, you need

* GCC with GObjC
* Clang
* GNUstep

`objcheck` will check these dependencies, emitting an error message if one is not installed on your system.

We tested `objcheck` on Ubuntu 18.04 LTS. It should work on other Unix-like OSes as well.

## Supported File Formats

`objcheck` supports the following file extensions:

* *.m* for Objective-C source
* *.mm* for Objective-C++ source
* *.c* for C source
* *.cpp*, *.cxx* or *.cc* for C++ source

They are possible languages used in Objective-C projects.

## Usage

Just copy `objcheck` to a valid **$PATH** like **$HOME**/bin to use it.

Check against single Objective-C file:

```
$ objcheck path/to/file.m
```

Check against several files:

```
$ objcheck path/to/*.m
```

Check for a static library:

```
$ objcheck static path/to/*.m
```

Check for a dynamic library:

```
$ objcheck dynamic path/to/*.m
```

Show help info:

```
$ objcheck help
```

## Environment Variables

You can adjust the behavior of `objcheck` with the following environment variables:

* **GCC** to set GCC compiler
* **GPP** to set G++ compiler
* **CLANG** to set Clang compiler
* **CLANGPP** to set Clang++ compiler
* **OUT_FILE** to set the name of a temporary output file
* **GNUSTEP_INCLUDE** to set the include path of GNUstep
* **GNUSTEP_LIB** to set the lib path of GNUstep
* **CFLAGS** to set custom include paths and compiler flags for C
* **CXXFLAGS** to set custom include paths and compiler flags for C++
* **LDFLAGS** to set custom lib paths
* **LIBS** to set custom library linkages

All environment variables are optional, set with sensible default values.

## License

Copyright 2019, Michael Chen; licensed under [MIT](https://opensource.org/licenses/MIT).
