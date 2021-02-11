cmake_minimum_required(VERSION 3.0 FATAL_ERROR)

project(gzbridge)

find_package(gazebo REQUIRED)
pkg_check_modules(jansson REQUIRED jansson)

# build sources
set(SOURCE_FILES 
  ./src/ConfigLoader.cc
  ./src/GazeboInterface.cc
  ./src/GZNode.cc
  ./src/OgreMaterialParser.cc
  ./src/pb2json.cc
)

include_directories(${GAZEBO_INCLUDE_DIRS})
link_directories(${GAZEBO_LIBRARY_DIRS})

list(APPEND CMAKE_CXX_FLAGS "${GAZEBO_CXX_FLAGS} --std=c++17 -Wall")

add_library(gzbridge SHARED ${SOURCE_FILES} ${CMAKE_JS_SRC})

# Gives our library file a .node extension without any "lib" prefix
set_target_properties(gzbridge PROPERTIES PREFIX "" SUFFIX ".node")

target_include_directories(gzbridge PRIVATE ${CMAKE_JS_INC})

target_link_libraries(gzbridge ${GAZEBO_LIBRARIES} ${jansson_LIBRARIES} ${CMAKE_JS_LIB})

if (UNIX)
  target_link_libraries(gzbridge pthread)
endif()
