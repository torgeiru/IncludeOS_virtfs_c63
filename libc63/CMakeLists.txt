# TODO: Update 3.14vers
cmake_minimum_required(VERSION 3.14)

#
# This tells CMake that your project's name is homeexam-01, and that the programs
# here are written in C.
# 
project(Codec63
	VERSION 3.0
	DESCRIPTION "Build configuration for Codec63")

# Use the C standard from 2011. No effect on Windows (Visual Studio ignores
set(CMAKE_CXX_EXTENSIONS ON) # definitely use GNU extensions (actually default)

# Overwrite default -O3 flag for Release mode
# set(CMAKE_C_FLAGS_RELEASE "-O1 -fno-tree-vectorize")

set(CMAKE_BUILD_TYPE Release)

add_library(c63
            STATIC dsp.cpp dsp.hpp
	           tables.cpp tables.hpp
	           io.cpp io.hpp
	           common.cpp common.hpp
	           me.cpp me.hpp)

# target_link_libraries(c63enc c63 m)