cmake_minimum_required(VERSION 4.2.1)
project(cmake_planning_test)
set(CMAKE_CXX_STANDARD 17)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
set(source
    planning_main.cpp
    process.cpp
    pnc_map.cpp
)
add_executable(planning_main ${source})
