pkgname=foldersync-bin
_product_name=foldersync-desktop
pkgver=2.11.0
pkgrel=1
epoch=1
pkgdesc='folder-synchronization-software (binary release)'
arch=(x86_64 aarch64)
url='https://foldersync.io/desktop'
license=('unknown')
depends=(rsync)
optdepends=()
_product_logo="tacit-dynamics-aps-foldersync-desktop"
provides=("${pkgname%-bin}=$pkgver" 'foldersync')
conflicts=("${pkgname%-bin}")

if [ "$CARCH" = x86_64 ]; then
  source_x86_64=("https://github.com/tacitdynamics/foldersync-desktop-production/releases/download/${pkgver}/foldersync-desktop-${pkgver}-linux-amd64.tar.gz")
elif [ "$CARCH" = aarch64 ]; then
  source_aarch64=("https://github.com/tacitdynamics/foldersync-desktop-production/releases/download/${pkgver}/foldersync-desktop-${pkgver}-linux-aarch64.tar.gz")
fi

sha256sums_x86_64=('7c6b822a3ab8f6e67bcbf38910e7521ca03ec2567a837b2ce23a2861b8708879')
sha256sums_aarch64=()


package() {
rsync -rP ${srcdir}/ ${pkgdir}

	for _size in 16x16 32x32 44x44 64x64 128x128 150x150 256x256 512x512 1024x1024; do
	[ -e "${size/x*/}.png" ] || continue
		install -Dm0644 "$pkgdir/$_product_name-$pkgver/$_product_logo/${size/x*/}.png" "/usr/share/icons/hicolor/$size/apps/$_product_logo.png"
	done
}
