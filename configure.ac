AC_INIT([solarc-firefox-theme], [49.20160920], [https://github.com/apheleia/solarc-firefox-theme/issues], [solarc-firefox-theme], [https://github.com/apheleia/solarc-firefox-theme])
AM_INIT_AUTOMAKE([-Wno-portability no-dist-gzip dist-xz foreign subdir-objects tar-ustar])
AC_PREFIX_DEFAULT(/usr/local)
AM_SILENT_RULES([yes])
AC_CONFIG_MACRO_DIR([m4])
AC_PROG_MKDIR_P


ARC_ENABLE([LIGHT],         [light],         [SolArc Light Firefox],     [disable])
ARC_ENABLE([DARKER],        [darker],        [SolArc Darker Firefox],    [disable])
ARC_ENABLE([DARK],          [dark],          [SolArc Dark Firefox],      [disable])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT

AC_MSG_RESULT([
        solarc-firefox-theme $VERSION
        ========

        prefix:                 ${prefix}
        exec_prefix:            ${exec_prefix}
        datarootdir:            ${datarootdir}
])
