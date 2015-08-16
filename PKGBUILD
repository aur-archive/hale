# Contributor: MCMic <come.bernigaud@laposte.net>

pkgname=hale
pkgver=0.6.4
pkgrel=1
pkgdesc="A Role Playing Game (RPG) with a turn based, tactical combat system. A lengthy campaign is included, with easy support for the creation of additional content."
arch=('i686' 'x86_64')
url="http://sourceforge.net/projects/hale/"
license=('GPL')
depends=('java-runtime>=6' 'lwjgl')
makedepends=()
conflicts=()
source=("http://sourceforge.net/projects/hale/files/hale-${pkgver}.zip/download")
md5sums=('5b747cfd7800bb17018682af3eb2c22c')

package() {
    cd $srcdir/

    # Making directory structure
    mkdir -p $pkgdir/opt/
    mkdir -p $pkgdir/usr/bin/

    # Packaging datas
    cp -r $srcdir/hale/ $pkgdir/opt/

    # Adding a binary
    echo -e "#!/bin/sh\ncd /opt/hale/ && sh hale.sh" > $pkgdir/usr/bin/hale

    # Replacing libs by system ones
    rm -r $pkgdir/opt/hale/lib/native
    ln -s /usr/share/lwjgl/native $pkgdir/opt/hale/lib/native
    rm -r $pkgdir/opt/hale/lib/lwjgl.jar
    ln -s /usr/share/lwjgl/jar/lwjgl.jar $pkgdir/opt/hale/lib/lwjgl.jar

    # Removing useless things
    rm $pkgdir/opt/hale/hale.exe
    rm -r $pkgdir/opt/hale/src

    # Setting rights and owners
    chown -R root:games $pkgdir/opt/hale
    chmod -R g+rw $pkgdir/opt/hale
    chown -R root:games $pkgdir/usr/bin/hale
    chmod g+rx $pkgdir/usr/bin/hale
}
