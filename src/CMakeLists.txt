# Spacegroup finder, enumeration support functions
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

# Reallocation of dynamic variables, 3x3 inverse, determinant, mink reduction, etc.	
add_library(utils
	num_types.f90
	utilities.f90
	numerical_utilities.f90
  vector_matrix_utilities.f90
	)

# gcd, SmithNormalForm, HermiteNormalForm, etc.	
add_library(rational
	numerical_utilities.f90
	utilities.f90
	vector_matrix_utilities.f90
	num_types.f90
	rational_mathematics.f90
	)

# General combinatorics functions like nchoosek, M permutations of N things, stable binomials, etc.	
add_library(combinatorics
	combinatorics.f90
)

# This library is useful for checking the equivalence of enumerated structures which have different representations. Not used very often anymore but still useful.
add_library(compare_structures

)

# This exe is needed to generate spacegroup information for tests of enumlib. This is a one-off code but could be adjusted for a more general purpose, stand-alone spacegroup finder
add_executable(spacegroup4fortpy.x
  symmetry.f90
  spacegroup.f90
)

# Add the sym.x executable after merging Alin's additions into Gus' local version
#add_executable(sym.x
# symdriver.f90
#)

target_link_libraries(spacegroup4fortpy.x utils)
#target_link_libraries(sym.x sym)

install(TARGETS spacegroup4fortpy.x  RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})
#install(TARGETS sym.x RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})
INSTALL_SUBLIB(sym)
INSTALL_SUBLIB(rational)
INSTALL_SUBLIB(utils)
INSTALL_SUBLIB(combinatorics)
INSTALL_SUBLIB(compare_structures)

install(FILES ${PROJECT_SOURCE_DIR}/src/num_types.f90 DESTINATION ${CMAKE_INSTALL_PREFIX}/include)
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/num_types.mod DESTINATION ${CMAKE_INSTALL_LIBDIR})
