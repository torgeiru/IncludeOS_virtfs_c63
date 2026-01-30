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

add_library(c63
            STATIC dsp.cpp dsp.hpp
	           tables.cpp tables.hpp
	           io.cpp io.hpp
	           common.cpp common.hpp
	           me.cpp me.hpp)
