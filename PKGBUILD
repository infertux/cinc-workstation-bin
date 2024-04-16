# Maintainer: Simon Stridsberg <aur@devsn.se>
# Maintainer: Cedric Felizard <cedric@felizard.fr>

pkgname=cinc-workstation-bin
pkgver=24.2.1058
pkgrel=1
pkgdesc="The Cinc installation package includes everything you need to start converging your machines."
arch=('x86_64')
url="https://cinc.sh/download/"
license=('Apache')
depends=(libxcrypt-compat)
conflicts=(chef chef-solo chef-dk chef-client cinc)
source=("http://downloads.cinc.sh/files/stable/cinc-workstation/${pkgver}/ubuntu/22.04/cinc-workstation_${pkgver}-1_amd64.deb")
sha256sums=('e3578f5f75b825a6db5af681052f8d090d4ea9fff3efae4b4f5e76198f387b12')

package() {
  cd "$srcdir"
  bsdtar -xf data.tar.xz -C "$pkgdir"

  # link executables
  binaries="cinc cinc-apply cinc-auditor cinc-cli cinc-client cinc-shell cinc-solo cookstyle kitchen knife ohai"

  mkdir -p $pkgdir/usr/bin

  for binary in $binaries; do
    ln -s /opt/cinc-workstation/bin/$binary $pkgdir/usr/bin/ || error_exit "Cannot link $binary to /usr/bin"
  done
  chown -Rh 0:0 $pkgdir
  chmod 755 $pkgdir/opt
}
