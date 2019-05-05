# Intel E3 1200 EDAC driver, patched to work with Pentium G5400

This is a **PoC** and **highly experimental** extension to the `ie31200_edac`
kernel module to test support for the Intel Pentium Gold G5400.

## License and Disclaimer

This code, as anything Kernel-related, is licensed under GNU GPL v2.0.
See the [LICENSE](LICENSE) file.

Building and installing custom kernel modules is dangerous. I'm not responsible
for any damage this will do to your infrastructure. You have been warned.

## Installation from source

```
cd src
make
sudo insmod ie31200_edac_mod.ko
```

If you're running a newer kernel which automatically loads the `skl_uncore`
module for the host bridge, you may have to unbind it from the PCI device first:

```
echo '0000:00:00.0' | sudo tee /sys/bus/pci/drivers/skl_uncore/unbind
```

## Debian package

`dpkg-dev` and `debhelper` need to be installed.

```
dpkg-buildpackage
```

## Credits

* The driver source was taken from the Linux 5.0 source tree.
* The modified PCI device IDs can be found in the Intel datasheet:
  https://www.intel.com/content/www/us/en/products/docs/processors/core/8th-gen-core-family-datasheet-vol-2.html
* The Debian packaging files are based on this excellent blog post by Vincent
  Bernat: https://vincent.bernat.ch/en/blog/2018-packaging-driver-debian-dkms
