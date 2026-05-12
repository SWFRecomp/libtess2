cmake_minimum_required(VERSION 3.10)

project(libtess2)
set(CMAKE_C_STANDARD 17)
set(CMAKE_C_STANDARD_REQUIRED ON)

set(CMAKE_SKIP_BUILD_RPATH FALSE)
set(CMAKE_BUILD_WITH_INSTALL_RPATH TRUE)
set(CMAKE_INSTALL_RPATH "$\{ORIGIN\}")

set(SOURCES
    ${PROJECT_SOURCE_DIR}/Source/bucketalloc.c
    ${PROJECT_SOURCE_DIR}/Source/dict.c
    ${PROJECT_SOURCE_DIR}/Source/geom.c
    ${PROJECT_SOURCE_DIR}/Source/mesh.c
    ${PROJECT_SOURCE_DIR}/Source/priorityq.c
    ${PROJECT_SOURCE_DIR}/Source/sweep.c
    ${PROJECT_SOURCE_DIR}/Source/tess.c
)

add_library(${PROJECT_NAME} STATIC ${SOURCES})

# frick u ninja
if (${CMAKE_GENERATOR} MATCHES "Ninja")
set(CONFIG_DIR .)
else()
set(CONFIG_DIR $<CONFIG>)
endif()

target_include_directories(${PROJECT_NAME} PRIVATE
    ${PROJECT_SOURCE_DIR}/Include
)