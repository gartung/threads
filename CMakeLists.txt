cmake_minimum_required(VERSION 3.6)

set(BUILD_TESTING ON)
include(CTest)
enable_testing()

set(CMAKE_CXX_FLAGS "-std=c++14 -pthread")
set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/modules ${CMAKE_MODULE_PATH})
find_package(TBB)
find_package(CppUnit)

include_directories(${CMAKE_SOURCE_DIR})
include_directories(${TBB_INCLUDE_DIRS})
include_directories(${CPPUNIT_INCLUDE_DIR})

add_subdirectory(hep_concurrency)
add_subdirectory(test)

install(DIRECTORY hep_concurrency DESTINATION ${CMAKE_INSTALL_PREFIX}/include FILES_MATCHING PATTERN "*.h*" )
