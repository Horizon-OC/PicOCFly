## Features

- Faster boot times (sub 0.2 seconds on average)
- Works even with defective RAM
- Supports Booting from a FAT32 partition on SD card, EMMC, BOOT1, or BOOT1 at 1MB offset
- Integrated UMS tool for accessing storage via USB
- Can launch payloads up to size of 128KB
- Integrated toolbox to update modchip firmware, update sdloader, rollback firmware
- Persistent configuration of the boot action (boot to menu by default, or boot payload by default), the boot storage (SD, EMMC, BOOT1 or automatic), the button combination to boot Stock (enable or disable)

## Debug/Fault indication LED colors

* `Blue` indicates glitching,
* `Light blue` indicates training,
* `Beige` indicates comparison to stored training data,
* `Yellow/Orange` indicates writing `sdloader` to `BOOT0` and/or success,
* `Red` indicates an issue with your modchip installation (otherwise known as a fault or error code).

### Fault description/Error codes

**Known error codes (`=` is a long pulse, `*` is a short pulse):**

`=` USB flashing done.

`**` RST (`B`) is not connected.

`*=` CMD (`A`)is not connected.

`=*` D0 (`C`/`DAT0`) is not connected.

`==` CLK (`D`) is not connected.

`***` No eMMC CMD1 response. (Bad eMMC?)

`**=` No eMMC block 1 read. (Should not happen.)

`*==` Bad wiring/cabling, typically has to do with the top ribbon cable that connects `3.3v`, `A`, `B`, `C`, `D` and `GND` pads. (Which is why I don't recommend using that ribbon cable.) Alternatively, it can also mean that the modchip is defective.

`*=*` No eMMC block 0 read. (eMMC init failure?)

`=**` eMMC initialization failure during glitching process.

`=*=` CPU never reach BCT check, should not happen. Typically caused by the SoC ribbon cable not being seated properly.

`==*` CPU always reach BCT check (no glitch reaction, check MOSFET/SoC ribbon cable).

`===` Glitch attempt limit reached, cannot glitch

`=***` eMMC initialization failure

`=**=` eMMC write failure - comparison failed

`==` eMMC write failure - write failed

`=*==` eMMC test failure - read failed

`==**` eMMC read failed during firmware update

`==*=` BCT copy failed - write failure

`===*` BCT copy failed - comparison failure

`====` BCT copy failed - read failure

* **For further troubleshooting, please see this page:** https://guide.nx-modchip.info/troubleshooting/error_codes/

## Credits
[Rehius](https://github.com/rehius) - Original Picofly dev <br>
[Nautilus](https://github.com/lulle2007200) - eMMC Payload boot / New SD Loader & More <br>
[DefenderOfHyrule](https://github.com/DefenderOfHyrule) - Faster Boot Time
