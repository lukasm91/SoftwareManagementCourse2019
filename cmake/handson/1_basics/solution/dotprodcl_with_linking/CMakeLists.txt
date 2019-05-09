cmake_minimum_required(VERSION 3.14)

project(dotprodcl LANGUAGES CXX)

# Don't do this, see excercises in next sessions
set(DOTPROD_ROOT "${CMAKE_CURRENT_LIST_DIR}/../dotprod/install" CACHE STRING "Path to dotprod library")

find_package(Boost 1.66 REQUIRED
    COMPONENTS program_options
    )

set(FLOAT_TYPE "double" CACHE STRING "Floating point precision (float/double)" )
set_property(CACHE FLOAT_TYPE PROPERTY STRINGS "float;double")

add_subdirectory(src)