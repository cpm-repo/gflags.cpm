set(EXAMPLES target_link_libraries)
foreach(DIR IN LISTS EXAMPLES)
  add_subdirectory("${DIR}")
endforeach()
