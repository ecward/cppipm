cmake_minimum_required(VERSION 2.8)
project(cppipm)

set( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

find_package(PkgConfig REQUIRED)
pkg_check_modules(EIGEN eigen3)

include_directories(
  include
  ${EIGEN_INCLUDE_DIRS}
)

#Just for QT creator to show the files
file(GLOB_RECURSE HEADERS "include/*.h")

add_library(cppipm SHARED
  src/cppipm.cpp  
  src/mpsReader.cpp
  ${HEADERS}
)

add_executable(test
  src/test/test.cpp
)

target_link_libraries(test
  cppipm
)

#copy test files to build dir
configure_file(test_data/QAFIRO.QPS test_data/QAFIRO.QPS COPYONLY)
configure_file(test_data/SIMPLE.QPS test_data/SIMPLE.QPS COPYONLY)
configure_file(test_data/TESTPROB2.QPS test_data/TESTPROB2.QPS COPYONLY)
configure_file(test_data/TESTPROB.QPS test_data/TESTPROB.QPS COPYONLY)

add_custom_target(run_tests
COMMAND test
)
add_dependencies(run_tests test)
