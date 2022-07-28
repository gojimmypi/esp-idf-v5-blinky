
sysprog files per [esp-idf-v5 topic](https://sysprogs.com/w/forums/topic/esp-idf-v5/#post-32814):

That said, it looks like your manual setup is using a different toolchain (esp-2022r1-RC1-11.2.0), that would explain the different behavior.

The best way to integrate it would be to:

Create a backup of the c:\SysGCC directory

Delete the old ESP32 compiler directory (E:\sysgcc\esp32\tools\xtensa-esp32-elf\esp-2021r2-patch3) and copy the 2022r1 version under E:\sysgcc\esp32\tools\xtensa-esp32-elf.

Edit toolchain.xml and bsp.xml, replacing xtensa-esp32-elf/esp-2021r2-patch3 with xtensa-esp32-elf/esp-2022r1-RC1-11.2.0 where appropriate (please use extra caution, since ESP32-S2/C3 targets use separate toolchains in their own directories).

Reopen the solution.

Again, this is something to do at your own risk. We will do all these steps, retest everything and publish a ready-to-use package once Espressif deems them stable enough for a general release. We intentionally do not do this for pre-release versions, as they tend to be much less reliable and often change in various subtle ways before the final release.