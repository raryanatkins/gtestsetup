### Install Guide

### Dependencies

CMake
```
sudo apt-get install cmake
```

### Build with CMake

GoogleTest comes with a CMake build script
([CMakeLists.txt](https://github.com/google/googletest/blob/master/CMakeLists.txt))
that can be used on a wide range of platforms ("C" stands for cross-platform.).
If you don't have CMake installed already, you can download it for free from
<http://www.cmake.org/>.

CMake works by generating native makefiles or build projects that can be used in
the compiler environment of your choice. You can either build GoogleTest as a
standalone project or it can be incorporated into an existing CMake build for
another project.

#### Standalone CMake Project

When building GoogleTest as a standalone project, the typical workflow starts
with

```
git clone https://github.com/google/googletest.git -b release-1.10.0
cd googletest        # Main directory of the cloned repository.
mkdir build          # Create a directory to hold the build output.
cd build
cmake ..             # Generate native build scripts for GoogleTest.
```

The above command also includes GoogleMock by default. And so, if you want to
build only GoogleTest, you should replace the last command with

```
cmake .. -DBUILD_GMOCK=OFF
```

If you are on a \*nix system, you should now see a Makefile in the current
directory. Just type `make` to build GoogleTest. And then you can simply install
GoogleTest if you are a system administrator.

```
make
sudo make install    # Install in /usr/local/ by default
```

If you use Windows and have Visual Studio installed, a `gtest.sln` file and
several `.vcproj` files will be created. You can then build them using Visual
Studio.

On Mac OS X with Xcode installed, a `.xcodeproj` file will be generated.

### First Test Program

Link -pthread and -lgtest in your makefile

[Code Sample](https://github.com/google/googletest/blob/master/googletest/samples/sample1_unittest.cc)

This should be your main in your test file
```
int main(int argc, char **argv) {
  ::testing::InitGoogleTest(&argc, argv);
  return RUN_ALL_TESTS();
}
```
[Primer](https://github.com/google/googletest/blob/master/docs/primer.md)
