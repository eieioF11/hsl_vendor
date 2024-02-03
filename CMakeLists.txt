cmake_minimum_required(VERSION 3.5)

project(hsl_vendor)

find_package(ament_cmake REQUIRED)

include(ExternalProject)
ExternalProject_Add(ThirdParty-HSL
  GIT_REPOSITORY  https://github.com/eieioF11/ThirdParty-HSL.git
  GIT_TAG         1.0.0
  BUILD_IN_SOURCE   YES
  CONFIGURE_COMMAND ./configure --prefix=${CMAKE_CURRENT_BINARY_DIR}/ThirdParty-HSL_install
  BUILD_COMMAND     make
  INSTALL_COMMAND   make install

)

install(
  DIRECTORY   ${CMAKE_CURRENT_BINARY_DIR}/ThirdParty-HSL_install/
  DESTINATION ${CMAKE_INSTALL_PREFIX}
)

install(
  FILES       ${CMAKE_CURRENT_BINARY_DIR}/ThirdParty-HSL_install/lib/libcoinhsl.so
  RENAME      libhsl.so
  DESTINATION lib
)