##################################
# Http-Server Makefile           #
# Developer: Gelson G Rodrigues  #
# Email: geoldery@gmail.com      #
##################################
cmake_minimum_required(VERSION 2.8)

#Set language
project("http-server") 

set (CMAKE_CONFIGURATION_TYPES "Debug;Release" CACHE STRING "" FORCE)

set(CMAKE_CXX_FLAGS "")
set(CMAKE_CXX_FLAGS_RELEASE " -lpthread -ldl -std=c++17 -O2 -g")
set(CMAKE_CXX_FLAGS_DEBUG " -lpthread -ldl -std=c++17 -g")

if (CMAKE_BUILD_TYPE STREQUAL "Debug") 
	MESSAGE("Debug Configuration")
	SET(INSTALLATION_PATH ${CMAKE_BINARY_DIR}/Debug)
elseif(CMAKE_BUILD_TYPE STREQUAL "Release")
	MESSAGE("Release Configuration")
	SET(INSTALLATION_PATH ${CMAKE_BINARY_DIR}/Release)
endif()
MESSAGE("Installation path:" ${INSTALLATION_PATH})

set(LIBRARIES_INCLUDE_PATH "usr/include")
set(LIBRARIES_PATH "/usr/lib64")

find_package (Threads) 
#Using Boost
#boost 1.69
set(BOOST_INCLUDEDIR ${LIBRARIES_INCLUDE_PATH}/boost)
include_directories(${BOOST_INCLUDEDIR})
find_package(Boost 1.69 REQUIRED COMPONENTS thread system filesystem timer chrono date_time locale iostreams program_options) 
 
 add_subdirectory(src)