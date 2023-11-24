# cpp-learning

cmake_minimum_required(VERSION 3.10)

project(your_project)

include(ExternalProject)

# Declare cpprestsdk using ExternalProject_Add
ExternalProject_Add(
    cpprestsdk
    GIT_REPOSITORY https://github.com/microsoft/cpprestsdk.git
    GIT_TAG master
)

# Add cpprestsdk to your project
add_subdirectory(${CMAKE_CURRENT_BINARY_DIR}/cpprestsdk-src
                 ${CMAKE_CURRENT_BINARY_DIR}/cpprestsdk-build
                 EXCLUDE_FROM_ALL)

# Add your project executable
add_executable(your_project main.cpp)

# Link your project to cpprestsdk
target_link_libraries(your_project PRIVATE cpprestsdk::cpprest)
