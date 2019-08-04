# Arch Linux Packages

**Arch Linux packages** are xz-compressed tar archives that are built and installed using commands provided by the `pacman` package on Arch Linux. ALPs are the package format used by Arch Linux derivatives (like Manjaro Linux) along with the “independent” distributions, Frugalware Linux and KaOS, which also use the pacman package manager, so this information should be applicable to packaging on these distributions too.

### ALP Contents

ALPs have the following contents:

```sh
$INSTALLED_FILES
.BUILDINFO
.INSTALL
.MTREE
.PKGINFO
```

where `$INSTALLED_FILES` are, of course, the installed files of the package with its respective file structure. For example, for the `broadcom-wl` package the `$INSTALLED_FILES` have the directory structure:

```sh
usr/
 - lib/
   - modprobe.d/
     - broadcom-wl.conf
   - modules/
     - extramodules-4.4-ARCH/
       - wl.ko.gz
 - share/
   - licenses/
     - broadcom-wl/
       - LICENSE
```

The package metadata (which is used by pacman when it installs new packages to check for file conflicts and such) is stored in the four hidden files (that is, those with . in their filename) in the package’s top-level directory.

### PKGBUILD Structure

ALPs are built from PKGBUILDs using the `makepkg` command that comes bundled with the pacman package manager. They are the easiest packages to build, in my opinion. PKGBUILDs have the following general format (for more details see the [PKGBUILD(5)](https://fusion809.github.io/man/PKGBUILD.5.html) man page):

```sh
# ~ Maintainer/Contributor name and email ~
pkgname=      # The package's name.
pkgver=       # The upstream package version, e.g., 1.5.0 for Atom 1.5.0.
pkgrel=       # The PKGBUILD revision number.
pkgdesc=      # The PKGBUILD's description.
arch=         # The architecture(s) on which the package is to be built.
url=          # The website of the package.
license=      # The legal license of the package.
depends=      # Runtime dependencies.
makedepends=  # Build dependencies.
optdepends=   # Optional dependencies.
provides=     # What the package provides.
conflicts=    # The package conflicts.
source=       # The source files required; also includes patches.
sha256sums=   # SHA256 sums of the source files.
md5sums=      # MD5 sums of the source files. Usually used INSTEAD of sha256sums.
install=      # Install files.

prepare() {   # Prepare the sources. Most commonly you will find sed functions
}             # and patches being applied here.

build() {     # Perform any compiling of the source code that may be necessary.
}             # You may also see configure scripts being run here.

package() {   # This will actually build the package. If more than one package is
}             # built from the one PKGBUILD then more than one package() function is provided.
```

the `sha256sums` can be replaced with `sha512sums` and sometimes GPG signatures are used also. For example, the Linux kernel PKGBUILD, in the core pacman repository, uses GPG and sha256sums to check package integrity and validity. The variable definition lines (that is, the `pkgname` line through to `install` line) provide mostly the package’s metadata and security checks (as well as variables that can be used in the following functions), while the `prepare(),` `build()` and `package()` functions are responsible for the actual building of the package. The `install` line defines the `.install` file that contains pre-, peri- and post-install checks and functions that need to be executed for the package. Here is an example PKGBUILD I have used to build gVim 7.4.1525:

```sh
# Maintainer: Brenton Horne <brentonhorne77 at gmail dot com>
# Contributor: Peter Mattern <pmattern at arcor dot de>

_pkgname=vim
pkgname="gvim"
pkgver=7.4.1525
pkgrel=1
pkgdesc="Vim the editor. CLI version and GTK2 GUI providing majority of features."
arch=("i686" "x86_64")
url="http://www.vim.org"
license=("custom:vim")
depends=("gtk2" "hicolor-icon-theme" "gtk-update-icon-cache" "desktop-file-utils")
optdepends=("lua: Lua interpreter" "perl: Perl interpreter" "python: Python 3 interpreter"
            "python2: Python 2 interpreter" "ruby: Ruby interpreter")
makedepends=("lua" "python" "python2" "ruby")
provides=("gvim" "xxd" "vim-runtime")
conflicts=("vim-minimal-git" "vim-git"
           "vim-minimal" "vim" "vim-python3" "gvim" "gvim-python3")
source=("https://github.com/vim/vim/archive/v$pkgver.tar.gz"
        "gvim.desktop")
sha256sums=('SKIP'
            'c346da4725b2db6f7b58c5b72bdf9e7efbba2a3275e97c17db48689e4de674ca')
install=gvim.install

prepare() {

    # set global configuration files to /etc/[g]vimrc
    sed -i 's|^.*\(#define SYS_.*VIMRC_FILE.*"\) .*$|\1|' ${srcdir}/${_pkgname}-${pkgver}/src/feature.h

}

build() {

    cd "${srcdir}/${_pkgname}-${pkgver}"
    ./configure \
      --enable-fail-if-missing \
      --with-compiledby='Arch Linux AUR' \
      --prefix=/usr \
      --enable-gui=gtk2 \
      --with-features=huge \
      --enable-cscope \
      --enable-multibyte \
      --enable-perlinterp=dynamic \
      --enable-pythoninterp=dynamic \
      --enable-python3interp=dynamic \
      --enable-rubyinterp=dynamic \
      --enable-luainterp=dynamic
    make

}

package() {

    # actual installation
    cd "${srcdir}/${_pkgname}-${pkgver}"
    make DESTDIR=$pkgdir install

    # desktop entry file and corresponding icon
    install -D -m644 ../gvim.desktop      $pkgdir/usr/share/applications/gvim.desktop
    install -D -m644 runtime/vim48x48.png $pkgdir/usr/share/icons/hicolor/48x48/apps/gvim.png

    # remove ex/view and man pages (normally provided by package 'vi' on Arch Linux)
    cd $pkgdir/usr/bin ; rm ex view
    find $pkgdir/usr/share/man -type d -name 'man1' 2>/dev/null | \
      while read _mandir; do
        cd ${_mandir}
        rm -f ex.1 view.1
      done

    # add license
    install -D -m644 ${srcdir}/${_pkgname}-${pkgver}/runtime/doc/uganda.txt \
      $pkgdir/usr/share/licenses/$pkgname/LICENSE
}
```

`prepare()` is used to _prepare_ the source, which means if the source is compressed (like a gz-compressed tar archive) the `prepare()` function will exact its contents so that they are available for the `build()` and `package()` functions. `build()` is used to build, or compile, the source, that is if this needs to be done (for example, some PKGBUILDs actually build ALPs from Debian or RPM packages, so no source code compiling is required). `package()` is what builds a package from either the compiled source (that is, the source after the `build()` function is run) or the prepared pre-compiled sources (that is, the contents of Debian/RPM binaries).

The `package()` function is essentially where the objective of the game is to move all the files you wish to be in the end package from the products (whether it be compiled source code, or unpacked Debian package contents) of the `build()` function into the `$pkgdir` directory. The `$pkgdir` directory is meant to have the same internal file system structure as where the package will place its installed files, if installed on one’s file system. For example, GTK themes are usually installed to `/usr/share/themes` so this is an example `package()` function for such cases (this one is specifically taken from the `osx-el-capitan-theme` PKGBUILD):

```sh
package() {
  mkdir -p "$pkgdir/usr/share/themes/"
  cp -a "$srcdir/${_pkgname}-${pkgver}/OS X El Capitan" "$pkgdir/usr/share/themes/"
}
```

see the package’s contents are moved to `${pkgdir}/usr/share/themes/OS X El Capitan`.

### Building ALPs

To build an ALP you run:

```sh
user $  makepkg
```

from within the same directory, as the PKGBUILD you intend to build is located. You may not have the package’s build dependencies pre-installed so this command may return an error stating that you have missing build dependencies. To fix this (assuming all the dependencies are in the presently-enabled pacman repositories) by installing all required build dependencies prior to the build, run:

```sh
user $  makepkg -s
```
