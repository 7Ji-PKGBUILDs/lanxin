# Maintainer: Guoxin "7Ji" Pu <pugokushin at gmail dot com>

pkgname=lanxin
pkgver=7.36.41.106940_6940
pkgrel=1
pkgdesc="An all-scene intelligent security collaboration platform"
arch=('x86_64' 'aarch64' 'loong64' 'mips64el')
url="https://service.lanxin.cn"
license=('proprietary')
options=(!strip !debug)
_deb_prefix='https://package.lanxin.cn/client/linux/lanxin-'
_deb_suffix="-uos_Official_${pkgver}.deb"
source_x86_64=("${_deb_prefix}x64${_deb_suffix}")
source_aarch64=("${_deb_prefix}aarch64${_deb_suffix}")
source_loong64=("${_deb_prefix}loongarch64${_deb_suffix}")
source_mips64el=("${_deb_prefix}mips64el${_deb_suffix}")
noextract=(lanxin-{x64,aarch64,loongarch64,mips64el}"${_deb_suffix}")

sha256sums_x86_64=(
    '2b5d1ee7592f63cce303c2c225d2c17954f27455288e71ad2ce17455357a3537'
)
sha256sums_aarch64=(
    '3f39dd665d1e3309146a1c9b60dba8da808fdc22543f8f02321507187c7481bc'
)
sha256sums_loong64=(
    '96a388adb026c20aa87543b6fd2877891486e3d8fcdb1fe656388870976a9d9c'
)
sha256sums_mips64el=(
    '8b943b05c99f00658f019b9592b1d6469eb78b7de6ab615144ad1b2858f6aa44'
)

prepare() {
    bsdtar -xOf *.deb ./data.tar.xz |
        xz -cd > data.tar
}

package() {
    tar -C "${pkgdir}" --no-same-owner -xf data.tar ./opt ./usr/share
    cd "${pkgdir}"
    mv opt/apps/cn.lanxin/files opt/lanxin
    mv opt/apps/cn.lanxin/entries/icons usr/share/
    sed -i 's|/opt/apps/cn\.lanxin/files|/opt/lanxin|' usr/share/applications/cn.lanxin.desktop
    rm -rf opt/apps opt/lanxin/bin/lib/lib{gmodule-2.0,jpeg}.so*
}
