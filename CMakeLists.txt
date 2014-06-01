cmake_minimum_required(VERSION 2.8.5 FATAL_ERROR)

project(glpng C)
include(GNUInstallDirs)

set(SONAME_VERSION 1)
set(MINOR_VERSION 46)
set(VERSION ${SONAME_VERSION}.${MINOR_VERSION})

set(BUILD_STATIC_LIBS ON CACHE BOOL "Set to ON to build static libraries")

find_package(ZLIB REQUIRED)
find_package(PNG REQUIRED)
find_package(OpenGL REQUIRED)

add_subdirectory(src)
configure_file(FindGLPNG.cmake.in FindGLPNG.cmake @ONLY)

install(FILES include/GL/glpng.h DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/GL/)
install(FILES glpng.htm DESTINATION ${CMAKE_INSTALL_DOCDIR})
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/FindGLPNG.cmake DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/cmake/Modules)
