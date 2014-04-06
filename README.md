makefile
========

Here are some example makefiles.

I get tired of remaking makefiles all the time, so I have a few generic makefiles for small projects.
I frequently layout my projects as follows:

```
|--README.md
|--makefile
|--src
|  |-- main.c
|  |-- functions.h
|  |-- functions.c
```
Where src will hold all of my source files. My makefiles then make an object directory called "obj" and a binary directory called "bin". I also like to have release and debug objects because I use macros for testing and debugging.

When I run ```make debug``` my project expands to this:
```
|--README.md
|--makefile
|--src
|  |-- main.c
|  |-- functions.h
|  |-- functions.c
|--obj
|  |-- main_debug.o
|  |-- functions_debug.o
|--bin
|  |-- example
```

Where bin/example_debug is my binary and my object files can be found in obj.
