cmake_minimum_required(VERSION 3.0.0)
project(window VERSION 0.1.0)

include(CTest)
enable_testing()

add_executable(window main.cpp)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

find_package(SFML COMPONENTS system window graphics CONFIG REQUIRED)
target_link_libraries(window PRIVATE sfml-system sfml-network sfml-graphics sfml-window)

# If you want SFML to provide an implementation of main():
#target_link_libraries(window PRIVATE sfml-main)
