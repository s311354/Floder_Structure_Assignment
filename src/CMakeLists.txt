cmake_minimum_required(VERSION 3.5)
project(GRAPH VERSION 0.0.1 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_BUILD_TYPE RelWithDebInfo)

add_definitions(-std=c++11)
add_definitions(-Werror) # stop compile on warning
message(${CMAKE_SOURCE_DIR})

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D_GLIBCXX_DEBUG")

set(SOURCE_FILES    graph.cc
                    graph_directed.cc
                    graph_representation.cc)

find_path(GRAPH_INCLUDE_DIRS graph.h graph_directed.h graph_representation.h HINTS ${CMAKE_SOURCE_DIR}/include)

add_library(graphs_lib SHARED ${SOURCE_FILES})
target_include_directories(graphs_lib PUBLIC ${GRAPH_INCLUDE_DIRS})
