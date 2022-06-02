https://kezunlin.me/post/d97b21ee/

## 1. Install in linux
```bash 
sudo apt install libeigen3-dev
```
include path: /usr/include/eigen3
lib path: /usr/lib/cmake/eigen3

**How to use it in CMakeLists.txt**:
```bash
cmake_minimum_required(VERSION 2.8)
project(Test)

find_package(Eigen3 REQUIRED)
MESSAGE( [Main] " EIGEN3_INCLUDE_DIRS = ${EIGEN3_INCLUDE_DIRS}") 
# EIGEN3_INCLUDE_DIRS = /usr/include/eigen3

include_directories(${EIGEN3_INCLUDE_DIRS})

add_executable(main test.cpp)
```
***Note: No need to link libraries for eigen3*** 
## 2. 