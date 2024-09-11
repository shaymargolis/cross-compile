# IPERF

## mipsel

```bash
mkdir mipsel-build
cd mipsel-build
CC=mipsel-linux-gnu-gcc-9 LD=mipsel-linux-gnu-ld CPP=mipsel-linux-gnu-cpp-9 CXX=mipsel-linux-gnu-g++-9 ../configure --host=mipsel-linux-gnu --build=aarch64-unknown-linux-gnu --prefix=`pwd`/out --disable-shared --enable-static --enable-static-bin
make -j2
make install
```
