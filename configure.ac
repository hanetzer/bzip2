#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([bzip2], [1.0.6-r10], [Julian Seward <jseward@bzip.org>])
BZIP2_LT_CURRENT=1
BZIP2_LT_REVISION=6
BZIP2_LT_AGE=0
AC_CONFIG_SRCDIR([bzlib.h])
AC_CONFIG_AUX_DIR([build-aux])
AC_CONFIG_MACRO_DIR([m4])

AM_INIT_AUTOMAKE([1.15 foreign subdir-objects -Wall])

# Checks for programs.
AC_PROG_AWK
AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_LN_S
AC_PROG_MAKE_SET
AM_PROG_AR
LT_INIT
LT_LANG([Windows Resource])
AX_REQUIRE_DEFINED([PKG_INSTALLDIR])
PKG_INSTALLDIR

# Checks for libraries.

# Checks for header files.

# Checks for typedefs, structures, and compiler characteristics.

# Check for system features.
AC_SYS_LARGEFILE

AX_APPEND_COMPILE_FLAGS([-Wall], [CFLAGS])

AX_APPEND_COMPILE_FLAGS([-Winline], [CFLAGS])

AX_APPEND_COMPILE_FLAGS([-Wfno-strength-reduce], [CFLAGS])

# Checks for library functions.

# Check for windows specific needs
AS_CASE([x$host],
	[x*-*-cygwin*|x*-*-mingw*], [
	AC_CHECK_PROGS([WINDRES], [windres $host-windres])
	use_version_rc=true
	]
)

AM_CONDITIONAL(USE_VERSION_RC, test x$use_version_rc = xtrue)

# Handle static bzip2/bzip2recover logic
AC_ARG_ENABLE([static-bzip2],
	AS_HELP_STRING([--enable-static-bzip2], [build bzip2/bzip2recover statically [default=no]]),
	[],[enable_static_bzip2=yes])
AM_CONDITIONAL(STATIC_BZIP2, test x$enable_static_bzip2 = xyes)

# Write the output.
AC_SUBST([BZIP2_LT_CURRENT])
AC_SUBST([BZIP2_LT_REVISION])
AC_SUBST([BZIP2_LT_AGE])
AC_CONFIG_FILES([Makefile bzip2.pc])
AC_OUTPUT
