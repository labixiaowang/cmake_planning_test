cmake_minimum_required(VERSION 3.10)  
project(cmake_planning_test)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 设置可执行文件输出目录（现代方式）
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)

# 源文件列表
set(EXECUTABLE_SOURCES 
    planning_main.cpp
)

set(LIBRARY_SOURCES
    src/pnc_map.cpp
    src/process.cpp
)

# 创建动态库
add_library(planning_lib SHARED ${LIBRARY_SOURCES})

# 添加头文件目录（PUBLIC 使得链接此库的目标也能访问 include/）
target_include_directories(planning_lib 
    PUBLIC 
    ${PROJECT_SOURCE_DIR}/include
)

# 创建可执行文件
add_executable(planning_main ${EXECUTABLE_SOURCES})

# 链接库（注意：不能用 PUBLIC！）
target_link_libraries(planning_main planning_lib)