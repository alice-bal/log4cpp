cmake_minimum_required(VERSION 3.16)
set(CMAKE_CXX_STANDARD 20)
project(log)
include(FetchContent)
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)
FetchContent_Declare(
    log4cpp
    GIT_REPOSITORY https://github.com/orocos-toolchain/log4cpp.git
    GIT_TAG ac2d373d5d767f17a01cadaa291f13724b9d09e3
)
FetchContent_MakeAvailable(log4cpp)
add_executable(logtest "")
target_include_directories(logtest PRIVATE include)
# target_link_libraries(logtest PRIVATE log4cpp Threads::Threads)
target_link_libraries(logtest PRIVATE log4cpp pthread)
target_sources(logtest PRIVATE
    src/main.cpp
)