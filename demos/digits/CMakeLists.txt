# // ------------------------------------------------------------------------------
#
# This is CMake-Project for SCNN Digits Recognition Demo.
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
set ( PROJECT_NAME "scnn-digits-demo" )

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

set ( DIGITS_HEADERS
	"main.hpp" )

# =================================================================================
# SOURCES
# =================================================================================

set ( DIGITS_SOURCES
	"main.cpp" )

# =================================================================================
# RESOURCES
# =================================================================================

if ( WIN32 OR WIN64 ) # WINDOWS
	set ( DIGITS_RESOURCES "../../res/win_res.rc" )
else ( WIN32 OR WIN64 ) # UNIX
	set ( DIGITS_RESOURCES "" )
endif ( WIN32 OR WIN64 )

# =================================================================================
# BUILD & CONFIGURE & LINK
# =================================================================================

# Add Executable-Object
add_executable ( digits ${DIGITS_SOURCES} ${DIGITS_HEADERS} ${DIGITS_RESOURCES} )

# Link
target_link_libraries ( digits scnn )

# Configure Executable Object
set_target_properties ( digits PROPERTIES
	CXX_EXTENSIONS FALSE
	OUTPUT_NAME "Digits"
	RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/bin/${CMAKE_BUILD_TYPE}" )

# =================================================================================
# INSTALL
# =================================================================================

# Install
install ( TARGETS digits )