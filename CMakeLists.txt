cmake_minimum_required(VERSION 3.14)

project(gflags.cpm)

if(PROJECT_IS_TOP_LEVEL)
  file(DOWNLOAD https://github.com/cpm-cmake/CPM.cmake/releases/latest/download/CPM.cmake
       ${CMAKE_CURRENT_BINARY_DIR}/cmake/CPM.cmake
  )
  include(${CMAKE_CURRENT_BINARY_DIR}/cmake/CPM.cmake)
endif()

get_property(
  CPM_INITIALIZED GLOBAL
  PROPERTY CPM_INITIALIZED
  SET
)

if(NOT CPM_INITIALIZED)
  message(FATAL "You should include CPM.cmake frist")
endif()

CPMAddPackage(
  NAME gflags
  VERSION 2.2.2
  URL https://github.com/gflags/gflags/archive/refs/tags/v2.2.2.tar.gz
  PATCHES ./03a4842c9c6aaef438d7bf0c84e8a62c8064992b.patch
  EXCLUDE_FROM_ALL YES
  SYSTEM NO
  OPTIONS "GFLAGS_EXPORT_NAMESPACE_SET OFF"
)

if(NOT PROJECT_IS_TOP_LEVEL)
  return()
endif()

add_subdirectory(examples)
