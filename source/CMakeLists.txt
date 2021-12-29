cmake_minimum_required(VERSION 3.21)
project(state_threads C)
enable_language(C ASM)


# ----------------------------------------------------------------------------------------------------------------------
if (${CMAKE_SYSTEM_NAME} MATCHES Linux)
    add_definitions(-DLINUX)
    if (EXISTS "/usr/include/sys/epoll.h" OR
            EXISTS "/usr/include/x86_64-linux-gnu/sys/epoll.h")
        add_definitions(-DMD_HAVE_EPOLL)
    endif ()
endif ()


add_library(st SHARED event.c io.c key.c sched.c stk.c sync.c md.S)