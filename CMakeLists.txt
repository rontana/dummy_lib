cmake_minimum_required(VERSION 3.3)
project(dummy_lib)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -fPIC")

include_directories(src)


set(SOURCE_FILES src/datasift/thing1.cpp src/datasift/thing1.hpp)

add_library( dummy_lib_object OBJECT ${SOURCE_FILES} )




add_library(dummy_lib_static STATIC $<TARGET_OBJECTS:dummy_lib_object>)
add_library(dummy_lib_shared SHARED $<TARGET_OBJECTS:dummy_lib_object>)

set_target_properties(dummy_lib_static PROPERTIES OUTPUT_NAME dummy_lib)
set_target_properties(dummy_lib_shared PROPERTIES OUTPUT_NAME dummy_lib)

