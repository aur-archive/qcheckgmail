# Contributer: giacomogiorgianni@gmail.com 

pkgname=qcheckgmail
code=qCheckGMail
name=mhogomchungu-$code-7928ece
pkgver=1.2.7
pkgrel=1
pkgdesc="is yet another KDE application that uses gmail atom feed to report if a user has new email in their gmail accounts"
arch=('i686' 'x86_64')
url="http://mhogomchungu.github.io/qCheckGMail/"
license=('GPL')
categories=()

if [ "${CARCH}" = 'x86_64' ]; then
  depends=('kdebase-runtime' 'gcc-libs-multilib')

elif [ "${CARCH}" = 'i686' ]; then
  depends=('kdebase-runtime' 'gcc-libs')
fi

makedepends=()
options=(!emptydirs)
#source=("http://kde-apps.org/CONTENT/content-files/148606-$name-$pkgver.tar.bz2")
#source=("https://codeload.github.com/mhogomchungu/qCheckGMail/legacy.tar.gz/$pkgver")
source=("https://github.com/mhogomchungu/$code/releases/download/$pkgver/$code-$pkgver.tar.bz2")

md5sums=('71d1de52388b8a47c42d54fe6d0d2087')
install=${code}.install

package() {
   cd $srcdir/$code-$pkgver
    if [ -d build ] ; then
        rm build/* -rf
    else
        mkdir build
    fi
    cd build
    sed -i '65s|${LIBKWALLETBACKEND}|${LIBKWALLETBACKEND} /lib/libQtGui.so.4 /lib/libQtNetwork.so.4 /lib/libQtCore.so.4|g' $srcdir/$code-$pkgver/CMakeLists.txt
   cmake -DCMAKE_INSTALL_PREFIX=/usr .. && make clean
  make DESTDIR="$pkgdir" install
#install -dm 755 $pkgdir/usr/share/apps/katepart/syntax
#cp $srcdir/$pkgname-$pkgver/txl.xml $pkgdir/usr/share/apps/katepart/syntax
}

#package() {
#  cd ${srcdir}/$name-$pkgver/build
#  make DESTDIR=$pkgdir install
#}
