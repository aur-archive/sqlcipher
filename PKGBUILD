#Special regards to fauno
pkgname=sqlcipher
pkgver=3.2.0
pkgrel=1
pkgdesc="SQLite extension that provides transparent 256-bit AES encryption of database files"
arch=('i686' 'x86_64')
url="http://sqlcipher.net/"
license=('BSD')
makedepends=('tcl' 'openssl' 'sqlite3' 'git')
source=($pkgname-$pkgver::git+https://github.com/sqlcipher/sqlcipher#tag=v${pkgver})
sha1sums=('SKIP')
sha256sums=('SKIP')

pkgver() {
    echo $pkgver
}

build() {
    cd $srcdir/$pkgname-$pkgver
    ./configure --prefix=/usr \
        --disable-tcl \
        --enable-tempstore=yes \
        CFLAGS="$CFLAGS -DSQLITE_HAS_CODEC" LDFLAGS="-lcrypto"
    make
}

package() {
    cd $srcdir/$pkgname-$pkgver

    make DESTDIR="$pkgdir/" install
    install -D -m 0644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
} 
