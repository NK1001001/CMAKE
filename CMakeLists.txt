cmake_minimum_required (VERSION 2.6)
project (AssembTest)
    # The version number.
    set (AssembTest_VERSION_MAJOR 1)
    set (AssembTest_VERSION_MINOR 0)
     include(CheckCXXCompilerFlag)
    CHECK_CXX_COMPILER_FLAG("-std=c++11" COMPILER_SUPPORTS_CXX11)
    CHECK_CXX_COMPILER_FLAG("-std=c++0x" COMPILER_SUPPORTS_CXX0X)
    if(COMPILER_SUPPORTS_CXX11)
        set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
    elseif(COMPILER_SUPPORTS_CXX0X)
        set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")
    else()
        message(FATAL_ERROR "The compiler ${CMAKE_CXX_COMPILER} has no C++11 support. Please use a different C++ compiler.")
    endif()


    # configure a header file to pass some of the CMake settings
    # to the source code
    #configure_file (
    #  "${PROJECT_SOURCE_DIR}/AssembTestConfig.h.in"
    #  "${PROJECT_BINARY_DIR}/AssembTestConfig.h"
    #  )

    # add the binary tree to the search path for include files
    # so that we will find AssembTestConfig.h
    include_directories("${PROJECT_BINARY_DIR}")

    # add the executable
    add_executable(AssembTest test_assembly.cpp)
