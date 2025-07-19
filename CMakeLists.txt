# 指定CMake最低版本要求
cmake_minimum_required(VERSION 3.20)

project(DSAA VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/library/static)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/library/runtime)

include_directories(${PROJECT_SOURCE_DIR}/include)

add_library(dsaa_static STATIC
        main.cpp
)
target_link_libraries(dsaa_static PRIVATE
        pthread
)
set_target_properties(dsaa_static PROPERTIES OUTPUT_NAME "dsaa_static")

add_executable(DSAA main.cpp)
target_link_libraries(DSAA PRIVATE
        pthread
)
