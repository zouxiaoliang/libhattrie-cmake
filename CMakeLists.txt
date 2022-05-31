cmake_minimum_required(VERSION 3.5)

project(libhattrie-cmake LANGUAGES CXX C)

set(CMAKE_C_STANDARD 17)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(HAS_THIRDPARTY_HATTRIE ON PARENT_SCOPE)

function(libHatTrienMain)
    set(library_root "${CMAKE_CURRENT_SOURCE_DIR}/hat-trie")
    message(STATUS "thirdparty_libhattrie root path: ${library_root}")

    add_library(thirdparty_libhattrie INTERFACE)
    target_include_directories(thirdparty_libhattrie SYSTEM INTERFACE
      "${library_root}/include"
    )
endfunction()

libHatTrienMain()