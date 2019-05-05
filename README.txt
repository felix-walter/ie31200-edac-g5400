# Intel E3 1200 EDAC driver, patched to work with Pentium G5400

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
