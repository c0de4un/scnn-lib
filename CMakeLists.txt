# // ------------------------------------------------------------------------------
#
# This is CMake-Project for SCNN.
#
# SCNN - Simple Convolution Nerual Network Library.
#
# @Features:
# - multi-threading;
# - GPU calculation via OpenCL;
# - ECS model;
#
# License: see "LICENSE" file.
#
# // ------------------------------------------------------------------------------

# =================================================================================
# CMake Meta-Data
# =================================================================================

# CMake-Version
cmake_minimum_required ( VERSION 3.5 FATAL_ERROR ) # QT5 + CMake required 3.5 minimum.

# =================================================================================
# PROJECT
# =================================================================================

# Project Name
set ( PROJECT_NAME "scnn" )

# Project Version
set ( PROJECT_VERSION 0.1.0 )

# Configure Project
project ( ${PROJECT_NAME} VERSION ${PROJECT_VERSION} LANGUAGES C CXX )

# C++ Version
set ( CMAKE_CXX_STANDARD 11 )
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

# =================================================================================
# OPTIONS
# =================================================================================

option ( SCNN_BUILD_STATIC "Build STATIC Library ?" ON )
option ( SCNN_BUILD_SHARED "Build SHARED Library ?" OFF )
option ( SCNN_TESTS "Run STATIC-Tests ?" OFF )
option ( SCNN_BUILD_DEMOS "Build SCNN Demo ?" ON )

# =================================================================================
# MODULES
# =================================================================================

# Library
add_subdirectory ( "lib" )

# Demos
if ( SCNN_BUILD_DEMOS )
	add_subdirectory ( "demos/digits" )
endif ( SCNN_BUILD_DEMOS )