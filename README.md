# Build Guide

## Linux System
Tested on Ubuntu 20.04

### Linux

1. Install the SFML dependencies, e.g. on Ubuntu/Debian via `sudo apt install libsfml-dev`
2. Install CMake, e.g. on Ubuntu/Debian via `sudo apt-get install -y cmake`
3. Open a terminal, and `cd` into the `spine-runtimes/spine-sfml` folder
4. Type `mkdir build && cd build && cmake ../..` to generate Make files
5. Type `make` to compile the example
6. Run the example by `cd spine-sfml && ./spine-sfml-example` or `./spine-sfml-testbed`

### Json Parser Guide

Flow the target cpp code:
```cpp
if (strstr(skeletonFile.buffer(), ".skel") != nullptr) {
    std::cout << "LOADING SKEL!!!" << std::endl; 
    SkeletonBinary *binary = nullptr;
    if (atlas) {
        binary = new SkeletonBinary(atlas);
    } else {
        binary = new SkeletonBinary(&nullLoader);
    }
    binary->setScale(scale);
    skeletonData = binary->readSkeletonDataFile(skeletonFile);
    delete binary;
} else {
    std::cout << "Parser JSON to SKEL!!!" << std::endl; 
    SkeletonJson *json = nullptr;
    if (atlas) {
        json = new SkeletonJson(atlas);
    } else {
        json = new SkeletonJson(&nullLoader);
    }
    json->setScale(scale);
    skeletonData = json->readSkeletonDataFile(skeletonFile);
    delete json;
}
```

We find two ways to parse skeleton. Instead of using binary file, we use json, shown like `String atlasFile("data/sack-pma.atlas");` and `String skeletonFile("data/sack-pro.json");` to instruct combine image into 2D animation.