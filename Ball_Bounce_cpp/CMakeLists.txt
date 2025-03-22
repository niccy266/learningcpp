cmake_minimum_required(VERSION 3.12 FATAL_ERROR)

# Set project name and version
project(BallBounce VERSION 0.1)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt6 REQUIRED COMPONENTS Widgets)
qt_standard_project_setup()

# Enable debug symbols by default
if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Debug 
    CACHE STRING 
      "Choose the type of build (Debug or Release)" FORCE)
endif()

include(CTest)
enable_testing()

# Find SFML shared libraries
find_package(SFML 2.5 COMPONENTS system window graphics audio REQUIRED)

add_executable(BallBounce
    main.cpp
)

target_link_libraries(BallBounce PUBLIC sfml-window sfml-graphics)
target_link_libraries(BallBounce PRIVATE Qt6::Widgets)

# Set executable install location
install(TARGETS BallBounce DESTINATION bin)

set_target_properties(BallBounce PROPERTIES
    WIN32_EXECUTABLE ON
    MACOSX_BUNDLE ON
)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

