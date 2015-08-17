pkgname=vba-m-gtk-svn
pkgver=1196
pkgrel=1
pkgdesc="Gameboy Advance Emulator combining features of all VBA forks - GTK GUI - SVN version"
arch=(i686 x86_64)
url="http://vba-m.ngemu.com"
license=('GPL')
depends=('gtkmm' 'sdl' 'glibmm' 'libpng' 'zlib' 'cairo' 'mesa' 'gtkglext' 'gtkglextmm' 'libxv' 'hicolor-icon-theme' 'desktop-file-utils')
makedepends=('cmake' 'pkgconfig' 'nasm' 'subversion' 'ffmpeg-compat')
conflicts=('vba-m-gtk')
install='vba-m-gtk-svn.install'
source=("vbam::svn+https://vbam.svn.sourceforge.net/svnroot/vbam/trunk")
sha256sums=('SKIP')


pkgver() {
  cd "$SRCDEST"/vbam

  svnversion | tr -d [A-z]
}

build() {
	cd "${srcdir}"/vbam
 
	export PKG_CONFIG_PATH=/usr/lib/ffmpeg-compat/pkgconfig/:$PKG_CONFIG_PATH	

	cmake -DCMAKE_CXX_FLAGS=" -fpermissive" -DCMAKE_INSTALL_PREFIX="/usr" -DDATA_INSTALL_DIR:PATH="share/vbam/gtk" -DENABLE_LINK=OFF ../vbam
	make
}

package() {
	cd "${srcdir}"/vbam
	make DESTDIR=${pkgdir} install
}
