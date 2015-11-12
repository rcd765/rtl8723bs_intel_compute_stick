# rtl8723bs_intel_compute_stick
The realtek rtl8723bs combo driver for Linux on the Intel Compute Stick

Modified the source from:  http://asus.archive.canonical.com/pool/public/r/rtl8723bs-bluetooth-dkms/
to compile for kernel 4.3.0 and use on the Intel Compute Stick.

Tested on the STCK1A32WFC intel compute stick running Ubuntu 14.04.3 with a 4.3.0 kernel installed.

Steps to reproduce:

1) Install Ubuntu 14.04.3 on the Intel Compute Stick (ICS). No wifi or BT available at this stage.

2) On another machine Download the 4.3 kernel from kernel.org and copy it on a USB stick - to insert in ICS.

3) Copy the kernel source tree to /usr/src/ on the root file system on the stick.

4) Change directory to /usr/src/linux-4.3 and apply the kernel patches from https://github.com/hadess/rtl8723bs (patches folder) in the following order (using patch -p1 < filename.patch) :

0001-PM-QoS-Add-pm_qos_cancel_request_lazy-that-doesn-t-s.patch
0001-mmc-sdhci-get-runtime-pm-when-sdio-irq-is-enabled.patch
0002-mmc-sdhci-Support-maximum-DMA-latency-request-via-PM.patch
0003-mmc-sdhci-acpi-Fix-device-hang-on-Intel-BayTrail.patch
0004-mmc-sdhci-pci-Fix-device-hang-on-Intel-BayTrail.patch

5) Ensure the CONFIG_PINCTRL_BAYTRAIL and is set in the kernel .config.  A default wireless driver should also be enabled to pull in the wireless support.

6) Compile and the new kernel (sudo make -j4)

7) install the modules and kernel (sudo make -j4 modules_install install)

8) reboot with the new kernel (still no wifi).

9) Copy or clone the driver source to /usr/src/ on your stick.  In the rtl8723bs_intel_compute_stick directory do "sudo make all" and "sudo make install" to build and install the module.

10) reboot and you should have wifi and BT enabled.

I am getting great results with HD youtube videos over wifi.
