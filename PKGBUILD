# Maintainer: peace4all <markspost at rocketmail dot com>
pkgname=rhythmbox-webmenu-git
pkgver=20130201
pkgrel=1
pkgdesc="Rhythmbox 3 third party plugin WebMenu"
url="https://github.com/afrancoto/WebMenu"
arch=('i686' 'x86_64')
license=('GPL3')
makedepends=('git')
depends=('rhythmbox>=2.9')
install=$pkgname.install
conflicts=('rhythmbox-webmenu')

_gitroot="https://github.com/afrancoto/WebMenu.git"
_gitname="WebMenu"

build () {
  cd ${srcdir}
  msg "Connecting to the GIT server..."
  if [[ -d ${srcdir}/${_gitname} ]] ; then
    cd ${_gitname}
    git pull origin
    msg "The local files are updated..."
  else
    git clone ${_gitroot} ${_gitname}
    cd ${_gitname}
  fi
  msg "GIT checkout done."
}

package() {
  cd "${srcdir}/${_gitname}"
  mkdir -p "$pkgdir/usr/lib/rhythmbox/plugins/$_gitname"
  mv README.md README
  cp -R {*.py,*.plugin,README} "$pkgdir/usr/lib/rhythmbox/plugins/$_gitname/"

  mkdir -p "$pkgdir/usr/share/glib-2.0/schemas/"
  cp -R *.gschema.xml "$pkgdir/usr/share/glib-2.0/schemas/"
}
