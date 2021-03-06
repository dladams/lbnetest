# CMakeLists.txt file for lbnetest

#  This simply copies files into an install directory - there is no build

CMAKE_MINIMUM_REQUIRED (VERSION 2.8)

project(lbnetest NONE)

# cetbuildtools contains our cmake modules
set( CETBUILDTOOLS_VERSION $ENV{CETBUILDTOOLS_VERSION} )
if( NOT CETBUILDTOOLS_VERSION )
  message( FATAL_ERROR "ERROR: setup cetbuildtools to get the cmake modules" )
endif()
set( CMAKE_MODULE_PATH $ENV{CETBUILDTOOLS_DIR}/Modules ${CMAKE_MODULE_PATH} )

# Add any modules from this source necessary for building
set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/Modules ${CMAKE_MODULE_PATH} )

include(CetCMakeEnv)

# lbnetest has no architecture dependence
cet_cmake_env( noarch )

# Make sure cetbuildtools is set up (version is minimum)
find_ups_product(lbnecode v0_01_00)
find_ups_product(cetbuildtools v3_07_00)

# source code
add_subdirectory(Test35t)
add_subdirectory(test)
add_subdirectory(ups)

# packaging utility
include(UseCPack)


