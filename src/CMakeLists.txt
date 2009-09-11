# Created by Tomas Chvatal (Scarabeus IV)
###############################################################################
# sdlpango/src/CMakeLists.txt
###############################################################################
INCLUDE_DIRECTORIES ( ${ZLIB_INCLUDE_DIR} ${PNG_INCLUDE_DIR}
		${OPENGL_INCLUDE_DIR}  ${CMAKE_SOURCE_DIR}/include/ )
LINK_LIBRARIES ( ${CMAKE_DL_LIBS} ${ZLIB_LIBRARIES} ${PNG_LIBRARY}
		${OPENGL_gl_LIBRARY} )
SET ( SRCS ${APPNAME}.c
)
SET(CMAKE_SHARED_LIBRARY_C_FLAGS "-fPIC")
SET(CMAKE_STATIC_LIBRARY_C_FLAG "-Wl," )
ADD_LIBRARY ( shared SHARED ${SRCS} )
ADD_LIBRARY ( static STATIC ${SRCS} )
SET_TARGET_PROPERTIES(shared static PROPERTIES OUTPUT_NAME glpng)
SET_TARGET_PROPERTIES (shared PROPERTIES VERSION ${VERSION} SOVERSION ${SONAME_VERSION})
#INCLUDE(MacroCreateLibtoolFile.cmake)
#CREATE_LIBTOOL_FILE(pango-shared "/${CMAKE_INSTALL_LIBDIR}")
INSTALL ( TARGETS shared
	LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} )
INSTALL ( TARGETS static
	ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR} )


