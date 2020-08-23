cmake_minimum_required(VERSION 3.0)

add_definitions(-std=c++11)
# add_compile_options(-g)
project(tcp-proxy)


# set(CMAKE_CXX_FLAGS_RELEASE "/MT")
# set(CMAKE_CXX_FLAGS_DEBUG "/MTd")


find_package(Boost 1.7.0 REQUIRED COMPONENTS thread system)
message(STATUS "Boost_INCLUDE_DIRS:${Boost_INCLUDE_DIRS}")
message(STATUS "Boost_LIBRARY_DIRS:${Boost_LIBRARY_DIRS}")
message(STATUS "Boost_LIBRARIES:${Boost_LIBRARIES}")

aux_source_directory(. MainSourceFiles)
link_directories(${Boost_LIBRARY_DIRS})
include_directories(${Boost_INCLUDE_DIRS})
add_executable(tcp-proxy ${MainSourceFiles})
target_link_libraries(tcp-proxy ${Boost_LIBRARIES})