cmake_minimum_required (VERSION 3.0)

#set(CMAKE_GENERATOR_PLATFORM x64)
set(CMAKE_C_COMPILER=gcc)
set(CMAKE_CXX_COMPILER=g++)

project (win_ds1edit)

add_subdirectory("allegro")
add_subdirectory("winds1edit")
