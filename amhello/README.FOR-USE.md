# The desciption of how to use automake by use a amhello example

```
$ cat src/main.c
```

```
#include <config.h>
#include <stdio.h>

int main(void)
{
    puts("Hello World!");
    puts("This is "PACKAGE_STRING".");
    return 0;
}
```

```
$ autoscan
$ ls
autoscan.log  configure.scan  src
$ cp configure.scan configure.ac
$ cat configure.ac
```

```
#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

#AC_PREREQ([2.69])
AC_INIT([amhello], [1.0], [bug-automake@gnu.org])
AM_INIT_AUTOMAKE([-Wall -Werror foreign])
AC_PROG_CC
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_FILES(
 Makefile
 src/Makefile
)
AC_OUTPUT
```

```
$ cat README.md
```

```
This is a demonstration package for GNU Automake.
Type 'info Automake' to read the Automake manual.
```

```
$ cat src/Makefile.am
```

```
bin_PROGRAMS = hello
hello_SOURCES = main.c
```

```
$ cat Makefile.am
```

```
SUBDIRS = src
dist_doc_DATA = README.md
```

```
$ autoreconf --install
```

```
configure.ac:7: installing './compile'
configure.ac:6: installing './install-sh'
configure.ac:6: installing './missing'
src/Makefile.am: installing './depcomp'
```

```
$ ./configure
$ make
$ ./src/hello
```

```
Hello World!
This is amhello 1.0.
```
