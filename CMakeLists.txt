cmake_minimum_required(VERSION 3.0)

# Disable in-source builds to prevent source tree corruption.
if(" ${CMAKE_SOURCE_DIR}" STREQUAL " ${CMAKE_BINARY_DIR}")
	message(FATAL_ERROR "FATAL: In-source builds are not allowed. You should create a separate directory for build files.")
endif()

project(ngham C)

include_directories(${CMAKE_SOURCE_DIR}/include)
include_directories(${CMAKE_SOURCE_DIR}/rsclib/include)

add_library(rsclib SHARED ${CMAKE_SOURCE_DIR}/rsclib/src/rsc.c)
add_library(ngham SHARED ${CMAKE_SOURCE_DIR}/src/ngham.c)

install(DIRECTORY ${CMAKE_SOURCE_DIR}/include/ DESTINATION include)
install(TARGETS ngham DESTINATION lib)
