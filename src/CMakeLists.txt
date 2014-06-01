include_directories(
	${ZLIB_INCLUDE_DIR}
	${PNG_INCLUDE_DIR}
	${OPENGL_INCLUDE_DIR}
	${CMAKE_SOURCE_DIR}/include/
)

link_libraries(
	${ZLIB_LIBRARIES}
	${PNG_LIBRARY}
	${OPENGL_gl_LIBRARY}
)

add_library(glpng SHARED glpng.c)
set_target_properties(glpng PROPERTIES VERSION ${VERSION} SOVERSION ${SONAME_VERSION})
install(TARGETS glpng DESTINATION ${CMAKE_INSTALL_LIBDIR})

if(BUILD_STATIC_LIBS)
	add_library(glpng-static STATIC glpng.c)
	set_target_properties(glpng-static PROPERTIES OUTPUT_NAME glpng)
	install(TARGETS glpng-static DESTINATION ${CMAKE_INSTALL_LIBDIR})
endif(BUILD_STATIC_LIBS)
