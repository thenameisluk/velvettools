# Velvet Tools
## Set of tools / useful scripts for generating and flashing chromebook bootable kernel images

- ```vtlist``` lists available kernel versions
- ```vtbuild <version>``` builds a bootable image
- ```vtflash <version> </dev/diskname>``` flashes an image permanently
- ```vttest <version> </dev/diskname>``` flashes an image for testing purposes
- ```vtdisable </dev/diskname>``` makes partition unbootable
- ```vthelp <page>``` shows helpful info about scripts related things
- ```vtpack deb <version> <maintainer>``` makes you a cool kernel.deb
- ```vtpack targz <version>``` packs kernel very nicely into a tar.gz
- ```vtpack dir <version>``` makes directory structure, useful for packing for other linux distros

```<optional>```

# Config

The config file can be found at /etc/velvettools/config

```
flash=auto (default)
if the kernel version is the same it will just flash it, but when switching versions it will test for successful boot first (recommended)
flash=forced
will automatically flash without testing (not recommended)
flash=manual
will not automatically flash, unless you ask for it using vtflash or vttest (recommended for testing patches or cmdline)

main_part=auto (default)
will automatically be detected
main_part=/dev/x
in case you are running some non-default configuration, you can specify the partition


test_part=auto (default)
will automatically be detected
test_part=n (only if forced or manual)
in case there is no test partition
test_part=/dev/x
in case you are running some non-default configuration, you can specify the partition

init_gen_hook=y
automatically rebuild and flash image (if enabled) when initramfs is rebuilt
init_gen_hook=n
or not
```

## Structure

```
deb/
├── DEBIAN
│   ├── control
│   ├── postinst
│   ├── postrm
│   └── prerm
├── etc
│   ├── bash_completion.d
│   ├── initramfs
│   │   └── post-update.d
│   ├── initramfs-tools
│   │   └── hooks
│   └── velvettools
│       └── config
├── lib
│   └── systemd
│       └── system
│           └── vtcheck.service
└── usr
    ├── local
    │   └── bin
    │       ├── vtbuild
    │       ├── vtcheck
    │       ├── vtcommon
    │       ├── vtcommon-flash
    │       ├── vtdisable
    │       ├── vtflash
    │       ├── vthelp
    │       ├── vtlist
    │       ├── vtpack
    │       └── vttest
    └── share
        └── velvettools
            ├── bash
            │   └── velvettools
            ├── help
            │   ├── cmdline
            │   ├── dtbs
            │   ├── vtbuild
            │   ├── vtdisable
            │   ├── vtflash
            │   ├── vtlist
            │   ├── vtpack
            │   └── vttest
            └── hooks
                ├── after
                └── during
```

<- copied by the post-install script (/etc dir isn't updated by default on newer versions)
