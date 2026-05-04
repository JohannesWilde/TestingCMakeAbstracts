cmake_minimum_required(VERSION 3.5)

project(TestingCMakeAbstracts LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(a)
add_subdirectory(r0)
add_subdirectory(r1)


add_executable(TestingCMakeR0
    main.cpp
)

target_link_libraries(TestingCMakeR0
    PRIVATE r0
)


add_executable(TestingCMakeR1
    main.cpp
)

target_link_libraries(TestingCMakeR1
    PRIVATE r1
)

