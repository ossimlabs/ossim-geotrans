PROJECT(geotrans)
MESSAGE("**********************Setting up geotrans********************")
INCLUDE(OssimVersion)
INCLUDE(OssimUtilities)
INCLUDE(OssimCommonVariables)

IF(NOT APPLE)
  cmake_minimum_required(VERSION 2.6)
ELSE(NOT APPLE)
  cmake_minimum_required(VERSION 2.8)
ENDIF(NOT APPLE)

################################################## BUILD THE LIBRARY #######################################
SET(LIB_NAME geostrans)
include_directories( ${PROJECT_SOURCE_DIR}/include/geotrans )

FILE(GLOB_RECURSE GEOTRANS_SRCS *.cpp)
FILE(GLOB_RECURSE GEOTRANS_HEADERS "${CMAKE_CURRENT_SOURCE_DIR}/include/*.h")

SET(INSTALL_INCLUDE_DIR "include/geotrans")
OSSIM_LINK_LIBRARY(${LIB_NAME} COMPONENT_NAME ossim TYPE "${OSSIM_USER_DEFINED_DYNAMIC_OR_STATIC}" HEADERS ${GEOTRANS_HEADERS} SOURCE_FILES ${GEOTRANS_SRCS} 
                   INSTALL_LIB INSTALL_HEADERS VERSION_SYMLINKS ADDITIONAL_COMPILE_FLAGS "-D_USRDLL")

####################################### SETUP THE UNINSTALL #################################
OSSIM_ADD_COMMON_MAKE_UNINSTALL()
