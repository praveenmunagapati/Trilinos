
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR})
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_BINARY_DIR})

FILE(GLOB SOURCES *.C)

#removing due to dependence on a header not in Trilinos
#LIST(REMOVE_ITEM SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/UnitTestDistributedIndexWithBulkData.cpp")

TRIBITS_ADD_EXECUTABLE_AND_TEST(
    shylubddc_unit_tests
    SOURCES ${SOURCES}
    DEPLIBS
    ARGS ""
    COMM mpi
    NUM_MPI_PROCS 2
    )

TRIBITS_COPY_FILES_TO_BINARY_DIR(ShyLUBDDCDriverFiles
    SOURCE_FILES SolverBDDCTest.inp SolverBDDCTestSimple.inp SparseSolverTest.inp
    )

