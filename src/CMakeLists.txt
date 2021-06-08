add_library(sym
	symmetry.f90
	group_theory.f90
	itertools.f90
	classes.f90
	utilities.f90
	num_types.f90
	numerical_utilities.f90
	vector_matrix_utilities.f90
	)

add_library(utils
	num_types.f90
	utilities.f90
	numerical_utilities.f90
  vector_matrix_utilities.f90
	)

add_library(rational
	numerical_utilities.f90
	utilities.f90
	vector_matrix_utilities.f90
	num_types.f90
	rational_mathematics.f90
	)

add_executable(spacegroup4fortpy.x
  symmetry.f90
	spacegroup.f90
	)

target_link_libraries(spacegroup4fortpy.x utils)

install(TARGETS spacegroup4fortpy.x  RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})
INSTALL_SUBLIB(sym)
INSTALL_SUBLIB(rational)
INSTALL_SUBLIB(utils)
install(FILES ${PROJECT_SOURCE_DIR}/src/num_types.f90 DESTINATION ${CMAKE_INSTALL_PREFIX}/include)
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/num_types.mod DESTINATION ${CMAKE_INSTALL_LIBDIR})
