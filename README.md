# winmake
Batch Makefile for Windows

# Setting up makelist.bat
`call "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" %1` should be changed to point to `vcvarsall.bat` in your version of Visual Studio

`OUTDIR` is the directory where the executable will be saved

`APP` is the file name for the executable

`BINDIR` is where the unlinked binary blobs will be stored (`make clean` will delete everything in this folder)

`LIBDIR` is the directory where the libs are stored. Note: the libs must be in an `x86` or `x64` folder inside the `LIBDIR` folder

`LIBS` is the list of libs to include at link time

`*_SRC` is the root directroy (where the C/C++ files are) for source `*`.

`*_OBJ` is the list of C/C++ files in `*_SRC` that should be compiled for source `*`.

`*_INC` is a list of include directories for source `*`.

`SOURCES` is the list of sources (the `*` in `*_SRC`, `*_OBJ`, `*_INC`) to compile. This is not a list of C/C++ files.

Example:

```
set OUTDIR=out
set APP=app.exe
set BINDIR=bin
set LIBDIR=lib
set LIBS=lib1.lib lib2.lib

set SOURCES=target1 target2 target3

set target1_SRC=../external_folder
set target1_OBJ=external_cpp.cpp
set target1_INC=../external_folder/include ../external_folder/include/asdfghjkl

set target2_SRC=src/some/other/folders
set target2_OBJ=gl3w.c imgui_impl_sdl_gl3.cpp
set target2_INC=include include/qwerty

set target3_SRC=src C:\absolute\directory
set target3_OBJ=main.cpp other_main.cpp another.cpp
set target3_INC=include ../external_folder
```

# Running

To compile an x86 release ``C:\your\project\folder> make release x86``

To compile an x64 release ``C:\your\project\folder> make release x64``

To compile an x86 debug ``C:\your\project\folder> make debug x86``

To compile an x64 debug ``C:\your\project\folder> make debug x64``

To clean out the object folder ``C:\your\project\folder> make clean``