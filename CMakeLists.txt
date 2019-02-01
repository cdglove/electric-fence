project(efence LANGUAGES C)
cmake_minimum_required(VERSION 3.12)
find_package(Threads)
add_library(efence efence.c page.c print.c)
target_link_libraries(efence Threads::Threads)

enable_testing()
add_executable(eftest eftest.c)
target_link_libraries(eftest efence)
add_test(eftest eftest)

add_executable(tstheap tstheap.c)
target_link_libraries(tstheap efence)
add_test(tstheap tstheap)