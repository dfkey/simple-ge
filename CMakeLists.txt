cmake_minimum_required (VERSION 2.8)

include (CheckCXXCompilerFlag)

project (simple_se)

if (CMAKE_VERSION VERSION_EQUAL "3.1" OR CMAKE_VERSION VERSION_GREATER "3.1")
  set (CMAKE_CXX_STANDARD 11)
else ()
  check_cxx_compiler_flag ("-std=c++11" COMPILER_SUPPORTS_CXX11)
  check_cxx_compiler_flag ("-std=c++0x" COMPILER_SUPPORTS_CXX0X)
  if (COMPILER_SUPPORTS_CXX11)
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
  elseif (COMPILER_SUPPORTS_CXX0X)
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")
  else ()
    message (STATUS "The compiler ${CMAKE_CXX_COMPILER} has no C++11 support. Please use a different C++ compiler.")
  endif ()
endif ()

add_executable (simple_se main.cpp)
