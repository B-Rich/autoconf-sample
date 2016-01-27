# The desciption of how to use autoconf by use a hello-world example

```
$ cat hello.c
```

```
#include <stdio.h>

int main(void)
{
    printf("hello world!\n");
    return 0;
}
```

```
$ autoscan
$ ls
autoscan.log  configure.scan  hello.c

$ cp configure.scan configure.ac
$ ls
autoscan.log  configure.ac  configure.scan  hello.c
```

```
$ cat configure.ac
```

```
#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([hello], [1.0], [bug-autoconf@gnu.org])
AM_INIT_AUTOMAKE([-Wall -Werror foreign])
AC_CONFIG_SRCDIR([hello.c])
AC_CONFIG_HEADERS([config.h])

# Checks for programs.
AC_PROG_CC

# Checks for libraries.

# Checks for header files.

# Checks for typedefs, structures, and compiler characteristics.

# Checks for library functions.

AC_OUTPUT(Makefile)
```

```
$ aclocal
$ ls
aclocal.m4  autom4te.cache  autoscan.log  configure.ac  configure.scan  hello.c

$ autoconf
$ ls
aclocal.m4  autom4te.cache  autoscan.log  configure  configure.ac  configure.scan  hello.c


$ autoheader
$ ls
aclocal.m4  autom4te.cache  autoscan.log  config.h.in  configure  configure.ac  configure.scan  hello.c

$ cat Makefile.am
```

```
AUTOMAKE_OPTIONS=foreign
bin_PROGRAMS=hello
hello_SOURCES=hello.c
```

```
$ automake --add-missing
```

```
configure.ac:6: installing `./install-sh'
configure.ac:6: installing `./missing'
Makefile.am: installing `./depcomp
```

```
$ ./configure
$ make
$ ./hello
```
