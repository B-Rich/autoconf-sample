AC_INIT([Hello], dnl package
        [1.0], dnl version
        [bug-hello@example.org], dnl bug-report
        [], dnl tarname
        [http://www.example.org/]) # url
AC_DEFINE([HELLO_WORLD], dnl variable
          ["Hello, World\n"], dnl value
          [Greetings string.]) # description
AC_LANG_CONFTEST([AC_LANG_PROGRAM(
                  [[const char hw[] = "Hello, World\n";]], dnl global variable
dnl main program
[[fputs (hw, stdout);]])])
gcc -E -dD conftest.c
