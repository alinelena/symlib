cmake_minimum_required(VERSION 3.0.0)

project(symlib
  VERSION 2.0.1
  HOMEPAGE_URL https://github.com/msg-byu/symlib
  LANGUAGES Fortran)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake")
if (NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE "Release")
endif()
include(helper)
include(flags)
include(GNUInstallDirs)

set(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/${CMAKE_INSTALL_LIBDIR})
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/${CMAKE_INSTALL_BINDIR})

add_subdirectory(src)

configure_file(${PROJECT_SOURCE_DIR}/cmake/symlib.pc.cmake ${CMAKE_CURRENT_BINARY_DIR}/symlib.pc)
install(
  FILES  ${CMAKE_CURRENT_BINARY_DIR}/symlib.pc
  DESTINATION ${CMAKE_INSTALL_LIBDIR}/pkgconfig
  COMPONENT pkgconfig)

