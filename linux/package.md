# checkinstall make debian & rpm on ubuntu20.04
- make true you have installed rpm and checkinstall, if not run
```
apt install rpm
apt install checkinstall
```
- make rpmbuild directory
```
sudo mkdir -p /root/rpmbuild/SOURCES

```
- get source file nanomq
```
git clone https://github.com/nanomq/nanomq.git
```
- create build dir and make
```shell 
cd nanomq && mkdir build
cd build && cmake .. && make
```
- rpm packeage
```shell
sudo checkinstall --backup=no --install=no --type=rpm --arch=amd64  --pkgname=nanomq --pkgversion=0.2.1 --pkgrelease=0.2.1 --pkggroup=EMQX --maintainer=EMQX --provides=EMQX --pakdir .. --recommends=1 --suggests=1 -y
```
- debian package
```shell
sudo checkinstall --backup=no --install=no --type=debian --arch=amd64  --pkgname=nanomq --pkgversion=0.2.1 --pkgrelease=0.2.1 --pkggroup=EMQX --maintainer=EMQX --provides=EMQX --pakdir .. --recommends=1 --suggests=1 -y
```

- some troubles you may encounter
1. error: line 11: Empty tag: Recommends

this is a known bug checkinstall, when you build rpm on ubuntu,you must be sure every option is filled with sth when you use checkinstall with interactive mode.[see this](http://checkinstall.izto.org/checkinstall.git/), clone this project to see BUGS 
```
to make sure every blank is not empty
1 -  Summary: [ Package created with checkinstall 1.6.3 ]
2 -  Name:    [ build ]
3 -  Version: [ 20210107 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ Applications/System ]
7 -  Architecture: [ x86_64 ]
8 -  Source location: [ build ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Recommends: [  ]
12 - Suggests: [  ]
13 - Provides: [ build ]
```
