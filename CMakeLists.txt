# Created by Tomas Chvatal (Scarabeus IV)
###############################################################################
# sdlpango/CMakeLists.txt
###############################################################################
SET ( VERSION "1.45" CACHE STRING "Version" ) # this is redefine able
SET ( SONAME_VERSION "1" CACHE STRING "SONAME Version" )
SET ( CMAKE_INSTALL_PREFIX "/usr/local/" CACHE PATH "Install path prefix" )
SET ( CMAKE_INSTALL_LIBDIR lib )
SET ( WORKDIR ${CMAKE_SOURCE_DIR}/src )
###############################################################################

PROJECT ( glpng C )
SET ( APPNAME glpng )
CMAKE_MINIMUM_REQUIRED ( VERSION 2.6.0 )
CMAKE_MINIMUM_REQUIRED ( VERSION 2.6.0 FATAL_ERROR )
IF ( COMMAND cmake_policy )
	cmake_policy( SET CMP0003 NEW )
ENDIF ( COMMAND cmake_policy )
SET ( CMAKE_COLOR_MAKEFILE ON )
SET ( CMAKE_BUILD_TYPE_SHARED_LIBS ON )
# uninstall
###############################################################################
SET ( CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake" )
FIND_PACKAGE ( Zlib REQUIRED)
FIND_PACKAGE ( PNG REQUIRED )
FIND_PACKAGE ( OpenGL REQUIRED )
ADD_SUBDIRECTORY ( src )
ADD_SUBDIRECTORY ( Example )
# install include files
FILE ( GLOB files "${CMAKE_SOURCE_DIR}/include/GL/*.h" )
INSTALL ( FILES ${files} DESTINATION include/GL/ )
