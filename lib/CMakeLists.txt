# // ------------------------------------------------------------------------------
#
# This is CMake-Project for SCNN Library.
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
set ( PROJECT_NAME "scnn-lib" )

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
# HEADERS
# =================================================================================

set ( SCNN_HEADERS
	"../include/scnn/scnn.hpp" )

# =================================================================================
# SOURCES
# =================================================================================

set ( SCNN_SOURCES
	"scnn.cpp" )

# =================================================================================
# BUILD & CONFIGURE & LINK
# =================================================================================

# Add STATIC Library Object
if ( SCNN_BUILD_STATIC )
	add_library ( scnn STATIC ${SCNN_SOURCES} ${SCNN_HEADERS} )
endif ( SCNN_BUILD_STATIC )

# Add SHARED Library Object
if ( SCNN_BUILD_SHARED )
	add_library ( scnn SHARED ${SCNN_SOURCES} ${SCNN_HEADERS} )
endif ( SCNN_BUILD_SHARED )

# =================================================================================
# INSTALL
# =================================================================================

# Install STATIC Library
if ( SCNN_BUILD_STATIC )
	install ( TARGETS scnn )
endif ( SCNN_BUILD_STATIC )

# Install SHARED Library
if ( SCNN_BUILD_SHARED )
	install ( TARGETS scnn )
endif ( SCNN_BUILD_SHARED )