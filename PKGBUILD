# Maintainer: archlinux.info:tdy
# Contributor: Mikołaj Chwalisz <m.chwalisz@gmail.com>

pkgname=vitables
pkgver=3.0.0
pkgrel=1
pkgdesc="A GUI browser and editor for PyTables/HDF5 files"
arch=(any)
url=http://vitables.org
license=(GPL3)
depends=('python-pyqt5' 'python-qtpy' 'python-pytables')
makedepends=('python-sphinx')
source=(
    "https://downloads.sourceforge.net/$pkgname/ViTables-$pkgver.tar.gz"
    "vitables.desktop"
    "vitables.svg"
)
sha256sums=('f391f698f3602420f922fc761b28168bbb93993d392c171d97f1d4ba37680180'
            'dd793f85d81591edd837a5fb94642dbf3ba488c69c605cbc2c87f74baea8676c'
            '0be6fdeb2c1f40fe2c478b0a6b9f99bad170d69f1210300d736bb98a5b9edcd8')

build() {
  cd $srcdir/ViTables-$pkgver
  sed -e "s/'PyQt5 (>=5.5.1)', //g" -i setup.py
  sed '/PyQt5/d' requirements.txt
  python setup.py build
}

package() {
  cd $srcdir/ViTables-$pkgver
  python setup.py install --root="$pkgdir" --optimize=1
  install -d $pkgdir/usr/share/{applications,pixmaps}
  install -m644 $srcdir/vitables.desktop $pkgdir/usr/share/applications/
  install -m644 $srcdir/vitables.svg $pkgdir/usr/share/pixmaps/
}
