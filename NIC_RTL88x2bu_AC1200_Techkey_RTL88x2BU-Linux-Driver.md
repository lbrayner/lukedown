From <https://github.com/RinCat/RTL88x2BU-Linux-Driver> (see README.md):

# REALTEK RTL88x2B USB Linux Driver
**Current Driver Version**: 5.13.1-30
**Support Kernel**: 2.6.24 ~ 6.10 (with unofficial patches)

Linux in-tree rtw8822bu driver is working in process, check [this](https://lore.kernel.org/lkml/20220518082318.3898514-1-s.hauer@pengutronix.de/) patchset.

Official release note please check ReleaseNotes.pdf

**Note:** if you believe your device is **RTL8812BU** or **RTL8822BU** but after loaded the module no NIC shows up, the device ID maybe not in the driver whitelist. In this case please submit a new issue with `lsusb` result, and your device name, brand, website, etc.
