# Velvet Tools
## Set of tools/usefull scripts for generating and flashing chromebook bootable kernel images

- ```vtlist``` lists available kernel versions
- ```vtbuild <version>``` builds a bootable image
- ```vtflash <version> </dev/diskname>``` flashes the image permamently
- ```vttest <version> </dev/diskname>``` flashes the image for testing
- ```vtdisable </dev/diskname>``` makes partiotion unbootable
- ```vthelp <page>``` shows helpful info scripts related things
- ```vtpack deb <version> <maintainer>``` makes you cool kelner.deb
- ```vtpack targz <version>``` packs kelner very nicely into tar.g
- ```vtpack dir <version>``` makes directory structure, usefull for packing for other linux distros

```<optional>```

# Config

config file can be found at /etc/velvettools/config

```
flash=auto (default)
if the kernel version is the same it will just flash it, but when switching versions it will test for successful boot first
flash=forced
will automatically flash without testing
flash=manual
will not flash automatically unless you ask for it

main_part=auto (default)
will automatically be detected
main_part=/dev/x
in case you are running not default configuretion you can specify the partition


test_part=auto (default)
will automatically be detected
test_part=n (only ^ forced or manual)
in case there is no test partition
test_part=/dev/x
in case you are running not default configuretion you can specify the partition

init_gen_hook=y
automatically rebuild and flash image (if enabled) when initramfs is rebuilt
init_gen_hook=n
or no
```

## structure

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

<- copied by post install script (/etc dir aint updated by default with newer version)