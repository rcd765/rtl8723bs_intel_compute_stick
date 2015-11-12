# rtl8723bs_intel_compute_stick
The realtek rtl8723bs combo driver for the Intel Compute Stick

Modified the source tree from the chestermills packages to compile for kernel 4.3.0.

Tested on the STCK1A32WFC intel compute stick running Ubuntu 14.04.3 with a 4.3.0 kernel installed.

Make sure the kernel has the following patches installed from https://github.com/hadess/rtl8723bs (patches folder) in the following order (using patch -p1 < filename.patch) :
0001-PM-QoS-Add-pm_qos_cancel_request_lazy-that-doesn-t-s.patch
0001-mmc-sdhci-get-runtime-pm-when-sdio-irq-is-enabled.patch
0002-mmc-sdhci-Support-maximum-DMA-latency-request-via-PM.patch
0003-mmc-sdhci-acpi-Fix-device-hang-on-Intel-BayTrail.patch
0004-mmc-sdhci-pci-Fix-device-hang-on-Intel-BayTrail.patch


Copy source to /usr/src on your stick, "sudo make all" and "sudo make install" to build and install the module.

I am getting great results and no lockups so far.

wlan0     Link encap:Ethernet  HWaddr <removed> 
          inet addr:<removed> Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2ac2:ddff:fea1:6c5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:227738 errors:0 dropped:3748 overruns:0 frame:0
          TX packets:96213 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:334061011 (334.0 MB)  TX bytes:10234600 (10.2 MB)
