cmake_minimum_required(VERSION 3.17)
project(SpMM_comparision)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)


# LocationByValue MPI
message("Finding MPI")
find_package(MPI REQUIRED)
message(STATUS "MPI include dir: ${MPI_CXX_INCLUDE_PATH}")
message(STATUS "MPI libs: ${MPI_CXX_LIBRARIES}")
message(STATUS "MPI executable: ${MPIEXEC_EXECUTABLE}")

#include_directories(SYSTEM ${MPI_CXX_INCLUDE_PATH})

#message("Finding OpenCV")
#find_package( OpenCV REQUIRED )
#
#message(STATUS "OPENCV include  dir: ${OpenCV_INCLUDE_DIRS}")
#message(STATUS "OPENCV libs  dir: ${OpenCV_LIBS}")
#include_directories( ${OpenCV_INCLUDE_DIRS} )


#set(OpenBLAS_DIR "/usr/local/opt/openblas/lib/cmake/openblas")
#message("Finding openBLAS")
#find_package(OpenBLAS REQUIRED)
##set(OpenBLAS_CXX_INCLUDE_PATH "/usr/local/opt/openblas/include")
##set(OpenBLAS_CXX_LIBRARIES "/usr/local/opt/openblas/lib/libopenblas.dylib")
#message(STATUS "OpenBLAS include dir: ${OpenBLAS_CXX_INCLUDE_PATH}")
#message(STATUS "OpenBLAS libs: ${OpenBLAS_CXX_LIBRARIES}")
#
#include_directories(${OpenBLAS_CXX_INCLUDE_PATH})

message("Finding OpenMP")
find_package(OpenMP REQUIRED)

message("CMAKE_BINARY_PATH ${CMAKE_BINARY_DIR}")
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

message("Finding Intel")
find_package(intel REQUIRED)


set(SOURCES src/main.cpp)

add_executable(SpMM_comparision ${SOURCES})

#add_subdirectory(src/dmrpt)
#
#target_link_libraries(SpMM_comparision stdc++fs)
#target_link_libraries(SpMM_comparision src)
##target_link_libraries(distributed_mrpt ${MPI_CXX_LIBRARIES})
#target_link_libraries(SpMM_comparision MPI::MPI_CXX)
#target_link_libraries(SpMM_comparision OpenMP::OpenMP_CXX)