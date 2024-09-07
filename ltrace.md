# LTRACE

## MIPS LE

### Get zlib-1.3.1

```bash
mkdir mipsel-build
cd mipsel-build
make clean
CC=mipsel-linux-gnu-gcc-9 LD=mipsel-linux-gnu-ld CFLAGS="-O3 -fPIC" ../configure --prefix=`pwd`/out --static
make -j2
make install
```

### Get libelf

```bash
mkdir mipsel-build
cd mipsel-build
make clean
CC=mipsel-linux-gnu-gcc-9 LD=mipsel-linux-gnu-ld CPP=mipsel-linux-gnu-cpp-9 CXX=mipsel-linux-gnu-g++-9 LDFLAGS="-Wl,-rpath-link,/home/shay/Downloads/zlib-1.3.1/mipsel-build/out/lib -L/home/shay/Downloads/zlib-1.3.1/mipsel-build/out/lib" CCFLAGS="-Wl,-rpath-link,/home/shay/Downloads/zlib-1.3.1/mipsel-build/out/lib -I/home/shay/Downloads/zlib-1.3.1/mipsel-build/out/include" ../configure --host=mipsel-unknown-linux-gnu --build=aarch64-unknown-linux-gnu --prefix=`pwd`/out  --disable-demangler --disable-libdebuginfod --disable-debuginfod --disable-shared --enable-static
```

Before running `make -j2`, Change the following in `mipsel-build/config.h`:

```c
/* Define if you want 64-bit support (and your system supports it) */
#define __LIBELF64 1

/* Define to a 64-bit signed integer type if one exists */
#define __libelf_i64_t long long

/* Define to a 64-bit unsigned integer type if one exists */
#define __libelf_u64_t unsigned long long
```

```bash
make -j2
make install
```

### Get Ltrace

```bash
mkdir mipsel-build
cd mipsel-build

# static
make clean
CC=mipsel-linux-gnu-gcc-9 LD=mipsel-linux-gnu-ld CPP=mipsel-linux-gnu-cpp-9 CXX=mipsel-linux-gnu-g++-9 LDFLAGS="-static -Wl,-rpath-link,/home/shay/Downloads/zlib-1.3.1/mipsel-build/out/lib -L/home/shay/Downloads/zlib-1.3.1/mipsel-build/out/lib" CPPFLAGS="-static -Wformat-overflow=0 -Wno-error=deprecated-declarations -Wno-error=logical-not-parentheses -Wno-error=bool-compare -Wno-error=unused-local-typedefs -Wl,-rpath-link,/home/shay/Downloads/zlib-1.3.1/mipsel-build/out/lib -I/home/shay/Downloads/zlib-1.3.1/mipsel-build/out/include" ../configure --host=mipsel-linux-gnu --build=aarch64-unknown-linux-gnu --prefix=`pwd`/out  --with-libelf=/home/shay/Downloads/libelf/mipsel-build/out CCFLAGS="-static -Wformat-overflow=0 -Wl,-rpath-link,/home/shay/Downloads/zlib-1.3.1/mipsel-build/out/lib -I/home/shay/Downloads/zlib-1.3.1/mipsel-build/out/include" --enable-static --disable-shared
make -j2
make install

```
