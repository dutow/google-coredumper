cmake_minimum_required(VERSION  3.10)
project(coredumper C CXX)

option(BUILD_SHARED_LIBS "Build shared libraries (.dll/.so) instead of static ones (.lib/.a)" ON)

# We do not wish to work without threading support
# TODO: remove related ifdefs
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

set(COREDUMPER_SRC_DIR "${CMAKE_CURRENT_SOURCE_DIR}")

add_subdirectory(src)

include(CTest)
if(BUILD_TESTING)
  enable_testing()
  add_subdirectory(test)
endif()
