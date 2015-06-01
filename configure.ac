
AC_INIT([test], [0.0.1], [kannan@vijayan.ca])
AC_CANONICAL_SYSTEM
AM_INIT_AUTOMAKE([-Wall -Werror foreign subdir-objects])

AC_PROG_CXX
AC_LANG([C++])

AC_ARG_ENABLE(debug, [  --enable-debug       Enable debugging.])
AC_ARG_ENABLE(spew, [  --enable-spew        Enable spew.])
AC_ARG_ENABLE(warnerr, [  --enable-warnerr        Enable warnings-as-errors.])

AC_CHECK_HEADER([some_header.h],
                [AC_DEFINE([HAVE_SOME_HEADER], [1],
                    [Define to 1 if <some_header.h> is available])],
                [AC_MSG_ERROR([<some_header.h> not found])])

AC_CHECK_LIB([somelib], [somelibfunc],
                [AC_DEFINE([HAVE_LIBSOMELIB], [1],
                    [Define to 1 if libsomelib is available])
                 LIBS="$LIBS -lsomelib"],
                [AC_MSG_ERROR([libsomelib not found])])

# Check for mmap function
# AC_FUNC_MMAP

AC_CONFIG_HEADERS([config.h])

AC_CONFIG_FILES([
    Makefile
    src/Makefile
    src/test/Makefile
])

# Set architecture word bit-size and byte-size
case "$target_cpu" in
    i*86)
        AC_DEFINE([ARCH_BITS_32], [],
                    [Define if 32-bit arch.])
        ;;
    x86_64)
        AC_DEFINE([ARCH_BITS_64], [],
                    [Define if 64-bit arch.])
        ;;
esac

# Set ENABLE_DEBUG define.
if test "$enable_debug" = "yes"; then
    AC_DEFINE([ENABLE_DEBUG], [],
                [Define to enable debugging.])
    AC_DEFINE([ENABLE_SPEW], [],
                [Define to enable spew.])
fi

if test "$enable_spew" = "yes"; then
    AC_DEFINE([ENABLE_SPEW], [],
                [Define to enable spew.])
fi

AM_CONDITIONAL(DEBUG, test x"$enable_debug" = x"yes")
AM_CONDITIONAL(SPEW, test x"$enable_spew" = x"yes")
AM_CONDITIONAL(WARNERR, test x"$enable_warnerr" = x"yes")

AC_OUTPUT
