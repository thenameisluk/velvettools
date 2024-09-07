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

# Config (wip)

flash=auto (default)
flash=forced
flash=manual

main_part=auto (default)
main_part=/dev/x

test_part=auto (default)
test_part=n (only ^ forced or manual)
test_part=/dev/x

init_gen_hook=y
init_gen_hook=n

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