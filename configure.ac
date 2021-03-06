AC_PREREQ([2.69])
AC_INIT([igetnonce], [1.0], [https://github.com/s0uthwest/igetnonce/issues])

AM_INIT_AUTOMAKE([foreign])

AC_CONFIG_SRCDIR([igetnonce/all.h])
AC_CONFIG_HEADERS([config.h])

# Checks for programs.
AC_PROG_CC
CFLAGS+=" -std=c11"
AC_PROG_INSTALL
AC_PROG_LIBTOOL
AC_CONFIG_MACRO_DIRS([m4])

# Version bump
CFLAGS+=" -D IGETNONCE_VERSION_COUNT=\\\"$(git rev-list --count HEAD | tr -d '\n')\\\""
CFLAGS+=" -D IGETNONCE_VERSION_SHA=\\\"$(git rev-parse HEAD | tr -d '\n')\\\""

# Checks for libraries.
PKG_CHECK_MODULES(libimobiledevice, libimobiledevice-1.0 >= 1.2.1)
PKG_CHECK_MODULES(libirecovery, libirecovery >= 0.2.0)
PKG_CHECK_MODULES(libusbmuxd, libusbmuxd >= 0.29.1)
PKG_CHECK_MODULES(openssl, openssl >= 0.9.8)

# Checks for header files.
AC_CHECK_HEADERS([stdint.h stdlib.h string.h unistd.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_TYPE_INT32_T
AC_TYPE_INT64_T
AC_TYPE_SIZE_T
AC_TYPE_UINT32_T
AC_TYPE_UINT64_T

# Checks the platform.
AC_MSG_CHECKING([whether to enable WIN32 specific flags])
case "$host_os" in
*mingw*)
        win32=true
        AC_MSG_RESULT([yes])
	AC_CHECK_TOOL(WINDRES, windres)
  ;;
*)
        win32=false
        AC_MSG_RESULT([no])
  ;;
esac
AM_CONDITIONAL(WIN32, test x$win32 = xtrue)

# Checks for library functions.
AC_FUNC_ERROR_AT_LINE
AC_FUNC_FSEEKO
AC_FUNC_MALLOC
AC_CHECK_FUNCS([memset strdup strrchr])

AC_OUTPUT([
Makefile
igetnonce/Makefile
])
