cmake_minimum_required(VERSION 3.0.0...3.13)

project(engine VERSION 0.4.0 LANGUAGES C)
set_property(GLOBAL PROPERTY CTEST_TARGETS_ADDED 1)

include(CTest)
enable_testing()

# Makes binaries for GLAD and GLFW, two important OpenGL programs
add_subdirectory("third-party/glad")
add_subdirectory("third-party/glfw")

find_package(OpenGL REQUIRED COMPONENTS OpenGL)
find_package(OpenGL)



# Libraries
# add_subdirectory(libs/CGWorks)

##### Main program #####
add_executable(main "main.c")
target_link_libraries(main glad glfw)

include(CTest)
enable_testing()

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

