set(sources
  "${PROJECT_SOURCE_DIR}/src/main.cpp"
)
set(headers
  "${PROJECT_SOURCE_DIR}/include/Zynamic/Zynamic"
)

# Map extensionless files to Microsoft Visual C++
set_source_files_properties(${headers} 
PROPERTIES 
  CXX HEADER_FILE_ONLY
)

add_executable(Zynamic 
  ${sources}
  ${headers}
)

target_include_directories(Zynamic
PUBLIC
  $<INSTALL_INTERFACE:include>
  $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>

PRIVATE
  ${CMAKE_CURRENT_SOURCE_DIR}
)

target_compile_features(Zynamic
PRIVATE
  cxx_std_23
)

target_compile_options(Zynamic
PRIVATE
  /MP
  /Zi
)
