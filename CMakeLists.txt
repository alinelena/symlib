cmake_minimum_required(VERSION 3.0.0)

project(symlib
	VERSION 0.0.1
	HOMEPAGE_URL https://github.com/msg-byu/symlib
	LANGUAGES Fortran)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake")
include(helper)
include(GNUInstallDirs)

set(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/${CMAKE_INSTALL_LIBDIR})
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/${CMAKE_INSTALL_BINDIR})

add_subdirectory(src)
