cmake_minimum_required(VERSION 3.24)

project(test C CXX ASM)

set(CMAKE_MODULE_PATH
  ${CMAKE_MODULE_PATH}
  ${CMAKE_SOURCE_DIR}/..)

include(check_c_compiler)
include(check_cxx_compiler)

include(meta_config)
include(meta_custom)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

cmake_policy(SET CMP0054 NEW) # Only interpret if() arguments as variables or keywords when unquoted.
cmake_policy(SET CMP0076 NEW) # target_sources() command converts relative paths to absolute.
set(CMAKE_POLICY_DEFAULT_CMP0091 NEW) # MSVC runtime library flags are selected by an abstraction.
set(CMAKE_POLICY_DEFAULT_CMP0135 NEW) # Set the timestamps of all extracted contents to the time of the extraction.

# 显示详细信息
set (CMAKE_VERBOSE_MAKEFILE ON)

# 添加公共的编译指令
add_compile_options(-Wall -Wno-unused -gdwarf-2 -g3 -fno-common -fstack-protector)

add_executable(test_cc.exe test.cc)
add_executable(test_c.exe test.c)