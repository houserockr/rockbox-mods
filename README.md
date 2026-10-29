# rockbox-mods
personal mods to rockbox

## packets
sudo pacman -S --needed \
base-devel git wget curl perl python texinfo gmp mpfr libmpc isl libusb freetype2

## toolchain
1. clone repo

2. create dir for toolchain

   $ sudo mkdir /opt/rbtc
   $ sudo chown $USER:$USER /opt/rbtc
   $ cd <rb-repo>
   $ ./tools/rockboxdev.sh --prefix=/opt/rbtc
   $ export PATH=/opt/rbtc/bin:$PATH

## patch and build f/w
3. patch f/w to use menu button as back

   $ cd <rb-repo>
   $ patch -p1 < ipod6g-menu-back.patch

4. build f/w

   $ cd <rb-repo>
   $ mkdir build && cd build
   $ ./tools/rockboxdev.sh --prefix=/opt/rbtc
   $ make -j $(nproc)
   $ make zip

5. install f/w

   $ unzip -o rockbox.zip -d /run/media/$USER/IPOD

## further mods
6. fonts (optional)

TTF fonts can be converted using the convttf tool which is part of rb.
Requires freetype2

   $ cd <rb-repo>
   $ make -C tools convttf
   $ cd tools
   $ ./convttf -p 22 -c 1 xyz.ttf
   $ cp 22-xyz.fnt /run/media/$USER/IPOD/.rockbox/fonts/




