cmake_minimum_required(VERSION 3.5)

project(TestingCMakeAbstracts LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(a)
add_subdirectory(b)
add_subdirectory(r0)
add_subdirectory(r1)


add_executable(TestingCMakeR0
    main.cpp
)

# https://linux.die.net/man/1/ld
# --start-group archives --end-group
#     The archives should be a list of archive files. They may be either explicit file names, or -l options.

#     The specified archives are searched repeatedly until no new undefined references are created. Normally, an archive is searched only once in the order that it is specified on the command line. If a symbol in that archive is needed to resolve an undefined symbol referred to by an object in an archive that appears later on the command line, the linker would not be able to resolve that reference. By grouping the archives, they all be searched repeatedly until all possible references are resolved.

#     Using this option has a significant performance cost. It is best to use it only when there are unavoidable circular references between two or more archives.

target_link_libraries(TestingCMakeR0
    PRIVATE
        -Wl,--start-group
        r0
        b  # <- this would fail with "undefined reference to 'doStuff()'"
        -Wl,--end-group
)


add_executable(TestingCMakeR1
    main.cpp
)

target_link_libraries(TestingCMakeR1
    PRIVATE b
    PRIVATE r1
    # PRIVATE b  # <- this would fail with "undefined reference to 'doStuff()'"
)

