file(GLOB_RECURSE httpserver_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")
file(GLOB_RECURSE httpserver_HEADERS "${CMAKE_CURRENT_SOURCE_DIR}/*.hpp")

set (httpserver_INCLUDE_DIRS "")
foreach (_headerFile ${httpserver_HEADERS})
    get_filename_component(_dir ${_headerFile} PATH)
    list (APPEND httpserver_INCLUDE_DIRS ${_dir})
endforeach()
list(REMOVE_DUPLICATES httpserver_INCLUDE_DIRS)

add_executable(httpserver ${httpserver_SOURCES} ${httpserver_HEADERS})
target_include_directories(httpserver PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}/")
set_target_properties(httpserver PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${INSTALLATION_PATH}/)
install(TARGETS httpserver DESTINATION bin)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}) 

set(httpserver_TARGET_LIBRARIES 
    ${CMAKE_THREAD_LIBS_INIT} #pthread
    ${Boost_FILESYSTEM_LIBRARY}
    ${Boost_THREAD_LIBRARY}
    ${Boost_SYSTEM_LIBRARY}
    ${Boost_THREAD_LIBRARIES}
    ${Boost_DATE_TIME_LIBRARIES}
    ${Boost_FILESYSTEM_LIBRARIES}
    ${Boost_SYSTEM_LIBRARIES}
    ${Boost_TIMER_LIBRARIES}
    ${Boost_CHRONO_LIBRARIES}
    ${Boost_PROGRAM_OPTIONS_LIBRARIES}            
   
) 
 
#link libs with executable httpserver
target_link_libraries(httpserver ${httpserver_TARGET_LIBRARIES} )
 