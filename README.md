# spz-build
forked from [stytim/spz](https://github.com/stytim/spz/tree/main) -- Ubuntu executable build for .spz splat files for up to 10x compression

## How to Build on Ubuntu (currently only supported, tested with Ubuntu 22.04)
### Install Dependencies
```bash
sudo apt install gcc-11 g++-11 -y
```
```bash
wget https://github.com/Kitware/CMake/releases/download/v3.30.1/cmake-3.30.1.tar.gz &&
tar xfvz cmake-3.30.1.tar.gz && cd cmake-3.30.1 &&
./bootstrap && make -j$(nproc) && sudo make install &&
sudo rm -rf /usr/bin/cmake &&
sudo ln -s /usr/local/bin/cmake /usr/bin/cmake
```

### Build and Install
```bash
git clone https://github.com/Eecornwell/spz-build.git &&
cd spz-build/src &&
mkdir build &&
cd build &&
cmake .. &&
make

sudo make install
sudo ln -sf /path/to/spz-build/src/build/splat_converter /usr/local/bin/splat_converter
```

### How to Run
```bash
# PLY -> SPZ
splat_converter <name-of-file>.ply
```
```bash
# SPZ -> PLY
splat_converter <name-of-file>.spz
```

### Changes from original code at [stytim/spz](https://github.com/stytim/spz/tree/main)
- Added linux build commands in CMakeLists.txt
- Added support for ply files with comments in header