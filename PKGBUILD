# $Id$
# Maintainer : Robert Boles <lakeconnection@outlook.com>
# A.K.A. Homeless

pkgname=ryzom-client
pkgver=2.1.0
pkgrel=5
pkgdesc="Ryzom Official Client - Science-fantasy MMORPG - FREE TO PLAY"
arch=('i686' 'x86_64')
url=('http://www.ryzom.com/')
license=('AGPL3' 'CCPL:by-sa')
install=ryzom.install
makedepends=('p7zip' 'rsync')
provides=('ryzom')
source=('https://sourceforge.net/projects/ryzom/files/ryzom_client.7z'
	'ryzom.install')
md5sums=('dd4d093e041fa86579a30ea2514484fb'
	'c7a8165263f76846615798967a7fdbe6')
noextract=("ryzom_client.7z")

if [[ $CARCH == i686 ]]; then
    depends=('libgl' 'libxxf86vm' 'libxrandr' 'libpulse')
else
    depends=('lib32-libgl' 'lib32-libxxf86vm' 'lib32-libxrandr' 'lib32-libpulse')
fi

build() {
   : #echo 'Hello, world!'
}

package() {
    cd "$srcdir"

    7zr x -o"${pkgdir}"/opt ryzom_client.7z
    rsync -rtzv --progress --stats www.ryzom.com::ryzom  "${pkgdir}"/opt/ryzom/
    rm -rf "${pkgdir}"/opt/ryzom/{examples,unpack}
    chown -R root:games "${pkgdir}"/opt/ryzom
    chmod -R g+w "${pkgdir}"/opt/ryzom
    chmod 755 "${pkgdir}"/opt
}
