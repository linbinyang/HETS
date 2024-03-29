# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT license.

cmake_minimum_required(VERSION 3.12)
project(ClustarExamples VERSION 3.4.5 LANGUAGES CXX)

# Executable will be in ../bin
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${ClustarExamples_SOURCE_DIR}/../bin)

add_executable(clustarexamples boot.cpp)
target_sources(clustarexamples
    PRIVATE
        calc.cpp
        performance.cpp
)

# Import Microsoft SEAL
find_package(SEAL 3.4.5 EXACT REQUIRED
    # Providing a path so this can be built without installing Microsoft SEAL
    PATHS ${ClustarExamples_SOURCE_DIR}/../src/cmake
)

# Link Microsoft SEAL
target_link_libraries(clustarexamples SEAL::seal pthread)