## Windows compilation

We recommend using MinGW32 to compile radare for Windows. The 32-bit Windows builds distributed on the radare homepage are generated from a GNU/Linux system using MinGW32. They are tested with Wine.

The following is an example of compiling with MinGW32. The 'i486-mingw32-gcc' compiler option may need to be changed for your system:

    $ CC=i486-mingw32-gcc ./configure --enable-w32 --without-gui
    $ make
    $ make w32dist
    $ zip -r w32-build.zip w32-build

This generates a native, 32-bit console application for Windows.

Cygwin is another possibility; however, issues relating to Cygwin libraries can make debugging difficult in case of problems.
