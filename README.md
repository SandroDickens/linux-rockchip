# Linux for Rockchip

## 1. Clone Sourcecode

```shell
git clone --depth=1 -b linux-5.10.y https://github.com/SandroDickens/linux-rockchip.git
```

## 2. Config

```shell
touch .scmversion
# cross compile
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- rockchip_linux_defconfig
# native compile
make rockchip_linux_defconfig
```

## 3. Compile

## 3.1 compile deb pkg

```shell
# cross compile
make KERNELRELEASE="$(make kernelversion)-rockchip" KBUILD_IMAGE="arch/arm64/boot/Image" CROSS_COMPILE=aarch64-linux-gnu- ARCH=arm64 -j$(nproc) bindeb-pkg
# native compile
make KERNELRELEASE="$(make kernelversion)-rockchip" KBUILD_IMAGE="arch/arm64/boot/Image" -j$(nproc) bindeb-pkg
```

## 3.2 compile binary pkg

```shell
# cross compile
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- Image modules dtbs -j$(nproc)
# native compile
make Image modules dtbs -j$(nproc)
```
