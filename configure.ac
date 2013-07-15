AC_PREREQ([2.60])
AC_INIT([edcltool], [0.1], [andrew@ncrmnt.org])
AM_INIT_AUTOMAKE([foreign -Wall -Werror])
AC_CONFIG_HEADERS([config.h])
AC_C_INLINE

# Checks for programs.
AC_PROG_CC
AM_PROG_CC_C_O

AC_MSG_NOTICE([ *** MADE IN USSR WITH LOVE *** ])
sleep 1

# Checks for libraries.

# Checks for header files.
AC_CHECK_HEADERS([fcntl.h stdint.h stdlib.h string.h sys/ioctl.h sys/time.h termios.h unistd.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_C_INLINE
AC_TYPE_SIZE_T
AC_TYPE_UINT16_T

# Checks for library functions.
AC_FUNC_ERROR_AT_LINE
AC_FUNC_MALLOC
AC_CHECK_FUNCS([bzero gettimeofday memset strchr strdup strncasecmp strtoul])

AC_CONFIG_FILES([Makefile
                 src/Makefile])

found_lua=no

PKG_CHECK_MODULES([lua], [lua>=5.1],
  found_lua=yes
  have_lua=yes
  ,
  have_lua=no
)

PKG_CHECK_MODULES([lua52], [lua5.2],
  found_lua=yes
  have_lua52=yes
  ,
  have_lua52=no
)

PKG_CHECK_MODULES([lua51], [lua5.1],
  found_lua=yes;
  have_lua51=yes
  ,
  have_lua51=no
)

if test $found_lua = no; then
    AC_MSG_ERROR([Couldn't find any lua of use. Sorry])
fi

if test $have_lua = yes; then
   LUA_CFLAGS=$lua_CFLAGS
   LUA_LIBS=$lua_LIBS
   AC_MSG_NOTICE([Compiling against default lua installation])
else if test $have_lua52 = yes; then
   LUA_CFLAGS=$lua52_CFLAGS
   LUA_LIBS=$lua52_LIBS
   AC_MSG_NOTICE([Compiling against lua52])
else if test $have_lua51 = yes; then
   LUA_CFLAGS=$lua51_CFLAGS
   LUA_LIBS=$lua51_LIBS
   AC_MSG_NOTICE([Conmpiling against lua51])
fi
fi
fi

AC_SUBST([LUA_LIBS])
AC_SUBST([LUA_CFLAGS])

AC_OUTPUT