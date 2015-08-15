# Maintainer: Alucryd <alucryd at gmail dot com>
# Contributor: Sebastian Lenz <sebastian@archusers.de>

pkgname=gnome-shell-extension-alternative-status-menu-git
pkgver=20120501
pkgrel=1
pkgdesc="A GNOME Shell extension to customize power options 
in the status menu."
arch=('i686' 'x86_64')
url="http://live.gnome.org/GnomeShell/Extensions"
license=('GPL' 'LGPL')
depends=('gnome-shell-extension-common-git')
makedepends=('git' 'gnome-common' 'intltool' 'gettext')
conflicts=('gnome-shell-extensions-git' 'gnome-shell-extension-alternative-status-menu')
install='gschemas.install'

_gitroot="git://git.gnome.org/gnome-shell-extensions"
_gitname="gnome-shell-extensions"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."
  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone -b gnome-3-4 $_gitroot
    cd $_gitname
  fi
  msg "GIT checkout done or server timeout"
  msg "Starting make..."
  cd ${srcdir}/${_gitname}
  ./autogen.sh --prefix=/usr --enable-extensions="alternative-status-menu"
}

package() {
  cd ${srcdir}/${_gitname}
  make DESTDIR=${pkgdir} install
  rm -rf $pkgdir/usr/share/locale
}

