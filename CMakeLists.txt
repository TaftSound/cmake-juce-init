cmake_minimum_required(VERSION 3.22)

project(JuceSetup)

set(CMAKE_CXX_STANDARD 20)

set(LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/libraries)

include(cmake/CPM.cmake)

CPMAddPackage(
        NAME JUCE
        GIT_TAG 7.0.9
        VERSION 7.0.9
        GITHUB_REPOSITORY juce-framework/JUCE
        SOURCE_DIR ${LIB_DIR}/juce
)

if (MSVC)
    add_compile_options(/Wall /WX)
else ()
    add_compile_options(-Wall -Wextra -Wpedantic)
endif ()

add_subdirectory(plugin)