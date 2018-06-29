cmake_minimum_required(VERSION 3.4)

project(helloworld)
# The version number.
set (helloworld_VERSION_MAJOR 0)
set (helloworld_VERSION_MINOR 4)


# The following folder will be included
#include_directories("${PROJECT_SOURCE_DIR}" .)


#set(CMAKE_INSTALL_PREFIX ${CMAKE_CURRENT_SOURCE_DIR}/src)
set(CMAKE_BINARY_DIR ${CMAKE_SOURCE_DIR}/bin)
#set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR})

add_executable(${PROJECT_NAME} main.cpp)

set_target_properties( helloworld PROPERTIES
    CXX_STANDARD 14
    CXX_STANDARD_REQUIRED ON
    COMPILE_OPTIONS "-Wpedantic;-Wall;-Wextra"
)

# add the install targets
install (TARGETS ${PROJECT_NAME} DESTINATION bin)

#include(CPack)

INCLUDE(InstallRequiredSystemLibraries)

set(CPACK_GENERATOR "DEB")
SET(CPACK_DEBIAN_PACKAGE_MAINTAINER "Yury")
set(CPACK_PACKAGE_VERSION_MAJOR "${PROJECT_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${PROJECT_VERSION_MINOR}")
set(CPACK_PACKAGE_VERSION_PATCH "$ENV{TRAVIS_BUILD_NUMBER}")
set(CPACK_PACKAGE_FILE_NAME "helloworld.CPACK_PACKAGE_VERSION_MAJOR.CPACK_PACKAGE_VERSION_MINOR-Linux")

INCLUDE(CPack)



