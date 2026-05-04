
add_library(b
    realization.cpp
)

target_include_directories(b
    PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}
)

target_link_libraries(b
    PRIVATE a
)
