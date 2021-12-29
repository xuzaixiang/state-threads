cmake_minimum_required(VERSION 3.21)
project(state_threads C)

if (CMAKE_BUILD_TYPE AND (CMAKE_BUILD_TYPE STREQUAL "Debug"))
    add_definitions(-DDEBUG)
endif ()

include_directories(../include)
add_subdirectory(../source st)

# example_server
add_executable(example_server server.c error.c)
target_link_libraries(example_server st)

# example_proxy
add_executable(example_proxy proxy.c)
target_link_libraries(example_proxy st)

# example_lookupdns
add_executable(example_lookupdns lookupdns.c res.c)
target_link_libraries(example_lookupdns st resolv)

