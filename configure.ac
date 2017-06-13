#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([flatpak-image-runtime], [0.0.0], [BUG-REPORT-ADDRESS])

AM_INIT_AUTOMAKE([-Wno-portability subdir-objects foreign])

AC_ARG_WITH(systemdunitdir,
  [AC_HELP_STRING([--with-systemdunitdir], [systemd unt directory])],
  [systemd_unitdir="${withval}"], [systemd_unitdir=${libdir}/systemd/system])

AC_ARG_WITH(domain,
  [AC_HELP_STRING([--with-domain], [       fake flatpak runtime domain in ID])],
  [_DOMAIN_="${withval}"], [_DOMAIN_="org.example"])

AC_ARG_WITH(arch,
  [AC_HELP_STRING([--with-arch], [        fake flatpak runtime architecture])],
  [_ARCH_="${withval}"], [_ARCH_=$(uname -m)])

AC_ARG_WITH(branch,
  [AC_HELP_STRING([--with-branch],        [fake runtime branch])],
  [_BRANCH_="${withval}"], [_BRANCH_="standard"])

AC_ARG_WITH(remote,
  [AC_HELP_STRING([--with-remote],        [fake runtime remote])],
  [_REMOTE_="${withval}"], [_REMOTE_="refkit"])

AC_SUBST([_DOMAIN_])
AC_SUBST([_ARCH_])
AC_SUBST([_BRANCH_])
AC_SUBST([_REMOTE_])

AC_OUTPUT([Makefile])

echo "Pseudo flatpak runtime configuration"
echo "*  systemd unitdir: $systemd_unitdir"
echo "*            <org>: $_DOMAIN_"
echo "*           <arch>: $_ARCH_"
echo "*         <branch>: $_BRANCH_"
echo "*         <branch>: $_REMOTE_"
