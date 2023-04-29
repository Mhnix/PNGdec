cmake_minimum_required(VERSION 3.13)

project(PNGdec C CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_EXTENSIONS OFF)

set(LIBRARY_OUTPUT_PATH lib)

add_subdirectory(src)

include(CMakePackageConfigHelpers)

configure_package_config_file(${CMAKE_CURRENT_SOURCE_DIR}/Config.cmake.in
  "${CMAKE_CURRENT_BINARY_DIR}/PNGdecConfig.cmake"
  INSTALL_DESTINATION lib/cmake/PNGdec
)
install(FILES
  "${CMAKE_CURRENT_BINARY_DIR}/PNGdecConfig.cmake"
  DESTINATION lib/cmake/PNGdec
)
