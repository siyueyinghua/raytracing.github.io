cmake_minimum_required(VERSION 3.19) # version can be different

set(CMAKE_CXX_COMPILER "D:/ProgramFiles/msys2/mingw64/bin/clang.exe")
set(CMAKE_CXX_COMPILER "D:/ProgramFiles/msys2/mingw64/bin/clang++.exe")

set(projectName ray_tracing)

project(${projectName} CXX) #name of your project

set(CMAKE_C_STANDARD 17)
set(CMAKE_CXX_STANDARD 17)

# ===================== TARGET ===================== #
include_directories("${resourcePath}/mingw64/include"
                    "${PROJECT_SOURCE_DIR}/inc"
					"${PROJECT_SOURCE_DIR}/../common")
set(targetName ray_tracing_one_weekend)

#-- file(GLOB_RECURSE DEPENDS_SOURCES LIST_DIRECTORIES false ${PROJECT_SOURCE_DIR}/src/*.c*)
file(GLOB_RECURSE DEPENDS_HEADERS LIST_DIRECTORIES false ${PROJECT_SOURCE_DIR}/inc/*.h)
file(GLOB TARGET_SOURCES LIST_DIRECTORIES false ${PROJECT_SOURCE_DIR}/*.c*)
file(GLOB TARGET_HEADERS LIST_DIRECTORIES false ${PROJECT_SOURCE_DIR}/*.h)
set(SOURCES ${DEPENDS_SOURCES} ${DEPENDS_HEADERS} ${TARGET_SOURCES} ${TARGET_HEADERS})

add_executable(${targetName}  ${SOURCES}) # add this executable

add_custom_target(run ${targetName})


# ===================== LINK ===================== #
set(resourcePath "D:/ProgramFiles/msys2")

set(CMAKE_LIBRARY_PATH "${resourcePath}/mingw64/lib" "${resourcePath}/clang64/lib")

#-- find_library(NAMES gtest gmock)

#-- target_link_libraries(${targetName} PRIVATE gtest gmock) # link google test to this executable


# ===================== DEBUG ===================== #
# For debug: print the variables
include(CMakePrintHelpers)
cmake_print_variables(PROJECT_SOURCE_DIR
                      DEPENDS_SOURCES
                      DEPENDS_HEADERS
                      TARGET_SOURCES
                      TARGET_HEADERS
                      INCLUDE_DIRECTORIES
                      CMAKE_GENERATOR
                      CMAKE_C_COMPILER
                      CMAKE_C_STANDARD
                      CMAKE_CXX_COMPILER
                      CMAKE_CXX_STANDARD
                      CMAKE_MESSAGE_LOG_LEVEL
                      CMAKE_SOURCE_DIR
                      CMAKE_BINARY_DIR
                      CMAKE_CURRENT_SOURCE_DIR
                      CMAKE_CURRENT_BINARY_DIR
                      CMAKE_PREFIX_PATH
                      CMAKE_LIBRARY_PATH
                      CMAKE_FRAMEWORK_PATH
                      CMAKE_SYSTEM_PREFIX_PATH
                      CMAKE_SYSTEM_LIBRARY_PATH
                      CMAKE_SYSTEM_FRAMEWORK_PATH)

cmake_print_properties(TARGETS run
    PROPERTIES POSITION_INDEPENDENT_CODE
    COMPILE_DEFINITIONS
    COMPILE_FEATURES
    COMPILE_OPTIONS
    INCLUDE_DIRECTORIES
    LINK_DIRECTORIES
    LINK_OPTIONS
    SOURCES)
