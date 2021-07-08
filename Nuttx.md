[TOC]

# [Device Drivers](https://nuttx.apache.org/docs/latest/components/drivers/index.html)
- Upper-half
  - Implement high-level interface (open, close, read, write)
  - Call lower-half via callback
- Lower-half
  - Hardware-specific
  - Implement at the architecture or board level

## Character Devcie Drivers
- register_driver, struct file_operations
- User access: open(), close(), read(), write()
- Specialized Character Drivers: ioctl()
- Examples: drivers/dev_null.c, drivers/fifo.c, drivers/serial.c

## Block Device Drivers
- register_blockdriver, struct block_operations
- User access: mount
- Accessing a Character Driver as a Block Device: cmd_losetup
- Accessing a Block Driver as Character Device:  cmd_dd
- Examples. drivers/loop.c, drivers/mmcsd/mmcsd_spi.c, drivers/ramdisk.c, etc.

## Specialized Device Drivers
- OS logic itself and are not accessible to application logic.
- Exaples