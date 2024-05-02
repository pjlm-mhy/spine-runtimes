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