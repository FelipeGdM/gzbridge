#
# This file is not currently used, refer to te root CMakeLists.txt for 
# the building strategy
#
# This files configures the tests compilation for the project
# and may be used again in the future
#

enable_testing()

add_subdirectory(test)

# build tests
include_directories (
  ${PROJECT_SOURCE_DIR}
  ${PROJECT_SOURCE_DIR}/test/gtest/include
  ${PROJECT_SOURCE_DIR}/test/gtest
)

set (test_sources
  pb2json_TEST.cc)

foreach(src ${test_sources})
  string(REGEX REPLACE "\\.cc" "" BINARY_NAME ${src})
  set(BINARY_NAME UNIT_${BINARY_NAME})

  add_executable(${BINARY_NAME} ${src})

  link_directories(${PROJECT_BINARY_DIR}/test)
  target_link_libraries(${BINARY_NAME}
    gtest
    gtest_main
    gzbridge
  )
  if (UNIX)
    target_link_libraries(${BINARY_NAME} pthread)
  endif()

  add_test(${BINARY_NAME} ${CMAKE_CURRENT_BINARY_DIR}/${BINARY_NAME})

endforeach()

