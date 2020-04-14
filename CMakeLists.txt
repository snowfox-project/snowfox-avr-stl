##########################################################################

cmake_minimum_required(VERSION 2.8)

##########################################################################

add_library(avr-stl INTERFACE)
target_include_directories(avr-stl INTERFACE include)
target_compile_options(avr-stl INTERFACE -Wno-deprecated-copy)

##########################################################################
