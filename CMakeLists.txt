cmake_minimum_required(VERSION 3.5)

project(hat-trie-cmake LANGUAGES CXX C)

set(CMAKE_C_STANDARD 17)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(EXTERNAL_INSTALL_LOCATION ${CMAKE_CURRENT_BINARY_DIR}/external)

include(ExternalProject)

function(main)
  ExternalProject_Add(
    hat-trie
    PREFIX ${EXTERNAL_INSTALL_LOCATION}
    GIT_REPOSITORY https://github.com/Tessil/hat-trie.git
    CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${EXTERNAL_INSTALL_LOCATION}
    UPDATE_DISCONNECTED TRUE
    INSTALL_COMMAND ""
  )

  add_library(thirdparty_hattrie INTERFACE)
  add_dependencies(thirdparty_hattrie googletest)
  target_include_directories(thirdparty_hattrie INTERFACE
    ${EXTERNAL_INSTALL_LOCATION}/src/hat-tri/include
  )
endfunction(main)

main()
