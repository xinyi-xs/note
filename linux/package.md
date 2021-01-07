# checkinstall make debian & rpm in ubuntu20.04

- make true you have installed rpm and checkinstall, if not run
```
apt install rpm
apt install checkinstall
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
-debian package
```shell
sudo checkinstall --backup=no --install=no --type=debian --arch=amd64  --pkgname=nanomq --pkgversion=0.2.1 --pkgrelease=0.2.1 --pkggroup=EMQX --maintainer=EMQX --provides=EMQX --pakdir .. --recommends=1 --suggests=1 -y
```
