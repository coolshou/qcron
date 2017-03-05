cmake_minimum_required(VERSION 3.5)

set(${PROJECT}_SRC_FILES
  qcron.cpp
  qcronfield.cpp
  qcronnode.cpp
  holiday.cpp
  )

set(${PROJECT}_HEADERS
  qcron.hpp
  )

set(CMAKE_AUTOMOC ON)
find_package(Qt5Core REQUIRED)
include_directories(${Qt5Core_INCLUDE_DIRS})
set(CMAKE_POSITION_INDEPENDENT_CODE ON)
# Declaration.

add_library(${PROJECT} SHARED ${${PROJECT}_SRC_FILES})

set_target_properties(${PROJECT} PROPERTIES
  PUBLIC_HEADER "${${PROJECT}_HEADERS}"
  COMPILE_FLAGS "${EQUILAB_CXX_FLAGS}")

install(TARGETS ${PROJECT}
  LIBRARY DESTINATION ${LIBRARY_OUTPUT_DIR}
  RUNTIME DESTINATION ${LIBRARY_OUTPUT_DIR}
  PUBLIC_HEADER DESTINATION ${PUBLIC_HEADER_DIR}/${PROJECT}
  COMPONENT library)
