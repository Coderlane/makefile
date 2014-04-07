makefile
========

I've included a few example projects in this repo. Some use straight makefiles and some use CMake to generate makefiles.

Make
----

I get tired of remaking makefiles all the time, so I have a few generic makefiles for small projects.
I frequently layout my projects as follows:

```
|-- README.md
|-- makefile
|-- src
|   |-- main.c
|   |-- functions.h
|   |-- functions.c
```
Where src will hold all of my source files. My makefiles then make an object directory called "obj" and a binary directory called "bin". I also like to have release and debug objects because I use macros for testing and debugging.

When I run ```make debug``` my project expands to this:
```
|-- README.md
|-- makefile
|-- src
|   |-- main.c
|   |-- functions.h
|   |-- functions.c
|-- obj
|   |-- main_debug.o
|   |-- functions_debug.o
|-- bin
|   |-- example_debug
```

Where bin/example_debug is my binary and my object files can be found in obj.

CMake
-----

I layout my CMake projects in a simmilar manner. Typically it'll look like this:

```
|-- README.md
|-- CMakeLists.txt
|-- src
|   |-- CMakeLists.txt
|   |-- main.c
|   |-- functions.h
|   |-- functions.c
```

The src directory still holds all of my source files. However, when I go to build my project I must setup another directory. I'll make a directory called debug and one called release.

```
|-- README.md
|-- CMakeLists.txt
|-- src
|   |-- CMakeLists.txt
|   |-- main.c
|   |-- functions.h
|   |-- functions.c
|-- debug
|-- release
```

In these directories I'll configure CMake to build a debug binary and a release binary. To do that I'll either use cmake, ccmake an ncurses cli for cmake, or cmake-gui a Qt gui for cmake.

