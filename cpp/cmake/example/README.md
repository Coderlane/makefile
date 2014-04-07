CMake
=====

Using CMake is pretty easy! In this project I have two CMakeLists.txt files.
One in the root of my project which specifies details about the whole project.
Another CMakeLists.txt file can be found in the src directory. That file specifies
details about the source in that directory. My project structure looks like this:

```
|--README.md
|--CMakeLists.txt
|--src
|  |-- CMakeLists.txt
|  |-- main.cpp
```

Again in this project I like to have a debug version and a release version.
CMake makes this easy for me. I can simply specify the CMAKE_BUILD_TYPE.
CMake has a few tools to do that. You can use ccmake the ncurses based command
line interface to cmake. You can also use cmake-gui a Qt graphical user interface
to work with cmake. Or you can simply pass arguements to cmake. Here I'll do just that.
I'll setup a debug directory and configure cmake for a debug build.

```
cd $(PROJECT_ROOT_DIRECTORY)        #Change to the project's root.
mkdir debug                         # Make a directory to work in.
cd debug                            # CD into it.
ccmake .. -DCMAKE_BUILD_TYPE=Debug  # Let CMake build our makefile.
make                                # Build the project!
```

Checkout www.cmake.org for more details. This is only the surface!
