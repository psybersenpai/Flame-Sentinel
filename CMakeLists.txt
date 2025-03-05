cmake_minimum_required(VERSION 3.10)
project(FlameSentinel)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

include_directories(include)

add_executable(FlameSentinel src/main.cpp)
