# Lesson 0 - Setup

## Starting with C

We will be starting our journey with the [C Programming Language](https://en.wikipedia.org/wiki/C_(programming_language)). C is a *compiled* language, this means that we write code in C and then a compiler turns that into binary machine code to run directly by a computer. The of course means that you will need to get a C compiler. For this course we will be using MinGW, (the Minimalist GNU for Window compiler.) This compiler can compile both C and C++ as well as a few other languages.

To down MinGW:
- go to [MSYS2](https://www.msys2.org/) and download the installer.
- open MSYS2 (64-bit) and type
    > ```pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain```

- Add the path to your MinGW-w64 bin folder to the Windows PATH environment variable by using the following steps:
    - In the Windows search bar, type Settings to open your Windows Settings.
Search for Edit environment variables for your account.
    - In your User variables, select the Path variable and then select Edit.
    - Select New and add the MinGW-w64 destination folder you recorded during the installation process to the list. If you used the default settings above, then this will be the path: C:\msys64\ucrt64\bin.
    - Select OK to save the updated PATH. You will need to reopen any console windows for the new PATH location to be available.

- now validation your installation by running in powershell:
    > ```gcc --version```

    > ```g++ --version```

    > ```gdb --version```

## Writing you first program

We will be using Visual Studio Code for this. Download for that is easy. Be sure to download the **C/C++ Extension** by Microsoft.

in powershell navigate to your coding directory (whatever you choose) and do
> ```mkdir hello_world```

> ```cd hello_world```

> ```code .```

this will bring up VSCode. From here you make a new file named **hello_world.c** and type
```C
#include <stdio.h> /* Includes the standard I/O header */

int main(void) {
    // printf is the C function for printing a formatted string, %s mean we insert another string into the format, in this case the string "World!"
    printf("Hello, %s\n", "World!");
    return 0;
}
```

now from the terminal in the hello_world directory run

> ```gcc .\hello_world.c -o hello_world```

this command tells gcc to compile you C code and output an executable named hello_world. Run it by executing

> ```.\hello_world.exe```

you will get 

> ```Hello World!```

as output

## Downloading Git

to share and manage code we will be using Git. to download it go to https://git-scm.com/download/win and download the **64-bit Git for Windows Setup**

validate installation with 

> ```git --version```

once you do this create a gilhub account
