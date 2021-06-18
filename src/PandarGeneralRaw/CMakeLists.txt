cmake_minimum_required(VERSION 3.5)
project(PandarGeneral)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

find_package(Eigen3 REQUIRED)
find_package(PCL REQUIRED COMPONENTS common)

set (CMAKE_CXX_FLAGS "-fPIC")


include_directories(
	.
	include
	include/pandarGeneral
	${EIGEN3_INCLUDE_DIR}
	${PCL_INCLUDE_DIRS}
)


add_library( ${PROJECT_NAME}
	src/input.cc
	src/pandarGeneral_internal.cc
	src/pandarGeneral.cc
  src/pcap_reader.cpp
)

target_link_libraries(${PROJECT_NAME}
		${EIGEN3_LIBRARIES}
		${PCL_IO_LIBRARIES}
)

if(${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_CURRENT_SOURCE_DIR})

endif(${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_CURRENT_SOURCE_DIR})

