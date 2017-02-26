#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([flatpak-image-runtime], [0.0.0], [BUG-REPORT-ADDRESS])

AM_INIT_AUTOMAKE([-Wno-portability subdir-objects foreign])

AC_ARG_WITH(systemdunitdir,
  [AC_HELP_STRING([--with-systemdunitdir], [systemd unt directory])],
  [systemd_unitdir="${withval}"], [systemd_unitdir=${libdir}/systemd/system])

AC_ARG_WITH(org,
  [AC_HELP_STRING([--with-org], [           flatpak runtime 'organization'])],
  [_ORG_="${withval}"], [_ORG_="iot.refkit"])

AC_ARG_WITH(arch,
  [AC_HELP_STRING([--with-arch], [          flatpak runtime architecture])],
  [_ARCH_="${withval}"], [_ARCH_=$(uname -m)])

AC_ARG_WITH(current,
  [AC_HELP_STRING([--with-current],        [fake runtime for current])],
  [_CURRENT_="${withval}"], [_CURRENT_="current"])

AC_ARG_WITH(distro-version,
  [AC_HELP_STRING([--with-distro-version], [fake runtime for distro version])],
  [_DISTRO_VERSION_="${withval}"], [_DISTRO_VERSION_="0.0.0"])

AC_ARG_WITH(image-version,
  [AC_HELP_STRING([--with-image-version], [ fake runtime for image version])],
  [_IMAGE_VERSION_="${withval}"], [])

AC_ARG_WITH(build-version,
  [AC_HELP_STRING([--with-build-version], [ fake runtime for build version])],
  [BUILD_VERSION="${withval}"], [])

AM_CONDITIONAL([IMAGE_RUNTIME], [test -n "$_IMAGE_VERSION_"])
AM_CONDITIONAL([BUILD_RUNTIME], [test -n "$_BUILD_VERSION_"])

AC_SUBST([_ORG_])
AC_SUBST([_ARCH_])
AC_SUBST([_CURRENT_])
AC_SUBST([_DISTRO_VERSION_])
AC_SUBST([_IMAGE_VERSION_])
AC_SUBST([_BUILD_VERSION_])
AC_SUBST([IMAGE_RUNTIME])
AC_SUBST([BUILD_RUNTIME])

AC_OUTPUT([Makefile])

echo "Pseudo flatpak runtime configuration"
echo "*  systemd unitdir: $systemd_unitdir"
echo "*            <org>: $_ORG_"
echo "*           <arch>: $_ARCH_"
echo "*  current version: ${_CURRENT_}"
echo "*   distro version: ${_DISTRO_VERSION_:-none}"
echo "*    image version: ${_IMAGE_VERSION_:-none}"
echo "*    build version: ${_BUILD_VERSION_:-none}"

