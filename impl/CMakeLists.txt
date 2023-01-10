cmake_minimum_required(VERSION 3.5)
project(GRAPH VERSION 0.0.1)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_BUILD_TYPE RelWithDebInfo)

find_path(GRAPH_INCLUDE_DIRS graph.h graph_representation.h graph_directed.h config.h HINTS ${CMAKE_SOURCE_DIR}/include)

add_definitions(-std=c++11)
add_definitions(-Werror) # stop compile on warning
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D_GLIBCXX_DEBUG")

message(${GRAPH_INCLUDE_DIRS})

configure_file("${GRAPH_INCLUDE_DIRS}/config.h.in" "${GRAPH_INCLUDE_DIRS}/config.h")

add_executable(folder_structure main.cc)
target_include_directories(folder_structure PUBLIC ${GRAPH_INCLUDE_DIRS})
target_link_libraries(folder_structure graphs_lib)
