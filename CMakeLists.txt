cmake_minimum_required(VERSION 3.20)

project(YAE_Example)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(YAE_ROOT "${CMAKE_CURRENT_SOURCE_DIR}/deps/yae")
set(YAE_PROJECT_ROOT "${CMAKE_CURRENT_SOURCE_DIR}")
set(CMAKE_MODULE_PATH "${CMAKE_MODULE_PATH};${YAE_ROOT}/cmake")


include(yae_lto)
enable_lto_globally()


# ---------------------------- External Dependencies -----------------------------

# https://github.com/fmtlib/fmt 10.1.1
add_subdirectory(cloned_dependencies/fmt/10_1_1 SYSTEM)

# https://github.com/Sunday111/EverydayTools for_yae
option(EDT_WITH_TESTS "" ON)
add_subdirectory(cloned_dependencies/Sunday111/EverydayTools SYSTEM)

# https://github.com/Sunday111/CppReflection for_yae
add_subdirectory(cloned_dependencies/Sunday111/CppReflection SYSTEM)

# https://github.com/martinus/unordered_dense v4.1.2
add_subdirectory(cloned_dependencies/martinus/unordered_dense SYSTEM)

# https://github.com/google/benchmark v1.8.3
option(BENCHMARK_ENABLE_TESTING "" OFF)
add_subdirectory(cloned_dependencies/google/benchmark/1_8_3 SYSTEM)

# https://github.com/google/googletest v1.15.0
option(INSTALL_GTEST "" OFF)
option(BUILD_GMOCK "" OFF)
add_subdirectory(cloned_dependencies/google/googletest/1_15_0 SYSTEM)

# --------------------------------- Own Modules ----------------------------------
add_subdirectory(src/hello_world)
add_subdirectory(deps/yae/modules/examples/ecs)
add_subdirectory(deps/yae/modules/examples/ecs_benchmark)
add_subdirectory(deps/yae/modules/examples/ecs_tests)
add_subdirectory(deps/yae/modules/examples/yae_example_benchmark)
add_subdirectory(deps/yae/modules/examples/yae_example_benchmark_main)
add_subdirectory(deps/yae/modules/examples/yae_example_library)
add_subdirectory(deps/yae/modules/examples/yae_example_header_only)
add_subdirectory(deps/yae/modules/examples/yae_example_executable)
add_subdirectory(deps/yae/modules/examples/yae_example_tests)
add_subdirectory(deps/yae/modules/examples/yae_example_tests_main)

enable_testing()
