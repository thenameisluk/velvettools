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


## structure

```
deb/
├── DEBIAN
│   └── control
│   ├── postinst
│   └── postrm
├── etc
│   ├── bash_completion.d <- /usr/share/velvettools/bash/velvettools
│   ├── initramfs
│   │   └── post-update.d <- /usr/share/velvettools/hooks/after
│   └── initramfs-tools
│       └── hooks <- /usr/share/velvettools/hooks/during
└── usr
    ├── local
    │   └── bin
    │       ├── vtbuild
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