# ------ Set Options for Projects --------------- #
MESSAGE(STATUS "Set Options for Project")

## CMake minimum version required
CMAKE_MINIMUM_REQUIRED(VERSION 3.24)

## Set CXX Compiler Version
SET(CMAKE_CXX_STANDARD 17)

SET(PROJECT_NAME "NewGLTF")
PROJECT( ${PROJECT_NAME} )

MESSAGE(STATUS "Setting Done")
# ----------------------------------------------- #


# ------ Set Files ------------------------------ #
MESSAGE(STATUS "Set Source File")

SET(MAIN_DIR ${CMAKE_CURRENT_SOURCE_DIR})
SET(SRC_DIR ${MAIN_DIR}/src )

## Source Files
LIST(APPEND SRCS
    ## Demo file
    ${SRC_DIR}/main.cpp
)

ADD_EXECUTABLE( ${PROJECT_NAME} ${SRCS} )

MESSAGE(STATUS "Setting Done ")
# ----------------------------------------------- #



# ------ Set Variables for Dependency ----------- #
MESSAGE( STATUS "Setting Variables for Dependency")

SET( DEP_INCLUDE )
SET( DEP_LIB_DIR )
SET( DEP_LIBS )
SET( DEP_LIST )

MESSAGE( STATUS "Setting Done")
# ----------------------------------------------- #



# ------ Set Options for Target Files ----------- #
MESSAGE( STATUS "Add Executable by platform")

## Include Header Directories for Target Files
IF ( WIN32 )
    SET( STATIC_LIB lib )
    SET( DYNAMIC_LIB dll)

ELSE ()
    SET( STATIC_LIB a )
    SET( DYNAMIC_LIB so )

ENDIF()

MESSAGE( STATUS "Setting Done" )
# ----------------------------------------------- #



# ------ Link LogProject on Target  ------------- #
MESSAGE(STATUS "Set Options for Target Files")

TARGET_INCLUDE_DIRECTORIES( ${PROJECT_NAME} PUBLIC ${DEP_INCLUDE} ${INCS} )
TARGET_LINK_DIRECTORIES( ${PROJECT_NAME} PUBLIC ${LIB_DIR} ${DEP_LIB_DIR} )
TARGET_LINK_LIBRARIES( ${PROJECT_NAME} PUBLIC ${DEP_LIBS} opengl32.lib gdi32.lib )

MESSAGE(STATUS "Setting Done ")
# ----------------------------------------------- #