cmake_minimum_required(VERSION 3.0.0)

project(Circle VERSION 0.1.0)

include(CTest)
enable_testing()

add_executable(Circle main.cpp)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

find_package(SFML COMPONENTS system window graphics audio network CONFIG REQUIRED)

target_link_libraries(Circle PUBLIC ${SFML_INCLUDE_DIRS})

# If you want SFML to provide an implementation of main():
#target_link_libraries(Circle PRIVATE sfml-main)
