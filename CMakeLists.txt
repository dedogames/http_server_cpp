##################################
# Http-Server Makefile           #
# Developer: Gelson G Rodrigues  #
# Email: geoldery@gmail.com      #
##################################
cmake_minimum_required(VERSION 3.10)

#Set language
project("http-server" LANGUAGES CXX) 

set (CMAKE_CONFIGURATION_TYPES "Debug;Release" CACHE STRING "" FORCE)

if (CMAKE_BUILD_TYPE STREQUAL "Debug") 
	MESSAGE("Debug Configuration")
	SET(INSTALLATION_PATH ${CMAKE_BINARY_DIR}/Debug)
elseif(CMAKE_BUILD_TYPE STREQUAL "Release")
	MESSAGE("Release Configuration")
	SET(INSTALLATION_PATH ${CMAKE_BINARY_DIR}/Release)
endif()
MESSAGE("Installation path:" ${INSTALLATION_PATH})
 
find_package (Threads) 

#Using Boost
set(Boost_USE_STATIC_LIBS ON)
find_package(Boost 1.77 REQUIRED COMPONENTS thread system filesystem  )
include_directories(${Boost_INCLUDE_DIR})
add_subdirectory(src)  
 
