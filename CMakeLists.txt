cmake_minimum_required(VERSION 3.12)
project(ed25519-donna)


add_library(ed25519-donna
        ed25519.c
    )
target_compile_options(ed25519-donna PRIVATE
        -Wno-overlength-strings
    )
if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
    target_compile_options(ed25519-donna PRIVATE
            -Wno-implicit-fallthrough
            -Wno-error
        )
endif()
target_include_directories(ed25519-donna PUBLIC .)
install(TARGETS ed25519-donna LIBRARY DESTINATION lib ARCHIVE DESTINATION lib)
