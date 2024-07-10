cmake_minimum_required(VERSION 3.20)
include(set_compiler_options)
set(module_source_files
    ${CMAKE_CURRENT_SOURCE_DIR}/private/main.cpp)
add_executable(hello_world ${module_source_files})
set_generic_compiler_options(hello_world PRIVATE)
target_link_libraries(hello_world PRIVATE fmt)
target_include_directories(hello_world PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/code/public)
target_include_directories(hello_world PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/code/private)
