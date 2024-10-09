# 要求 CMake 最低版本为 3.16
cmake_minimum_required(VERSION 3.16)

# 定义一个名为 CURRENT_DIRECTORY 的目录属性
define_property(DIRECTORY 
    # 目录属性的名称
    PROPERTY CURRENT_DIRECTORY
    # 简短的文档说明
    BRIEF_DOCS "The current directory"
    # 详细的文档说明
    FULL_DOCS "The current directory"
)

# 设置当前目录属性为当前源代码目录
set_property(DIRECTORY PROPERTY CURRENT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})

# 获取当前目录属性
get_property(CURRENT_DIR DIRECTORY PROPERTY CURRENT_DIRECTORY)

# 打印当前目录信息
message("CURRENT_DIR: ${CURRENT_DIR}")

# 添加预处理定义，定义宏TEST_DEFINED的值为1
add_compile_definitions(TEST_DEFINED=1)

# 获取当前目录的属性COMPILE_DEFINITIONS，即定义的宏
get_directory_property(DEFS COMPILE_DEFINITIONS) 

# 打印获取到的定义信息
message("DEFS: ${DEFS}")

# 将库目录链接到当前目录下的lib目录
link_directories(${CMAKE_CURRENT_SOURCE_DIR}/lib)

# 获取链接目录属性
get_property(LINK_DIR DIRECTORY PROPERTY LINK_DIRECTORIES)

# 获取源目录属性
get_property(S_DIR DIRECTORY PROPERTY SOURCE_DIR)

# 打印链接目录和源目录信息
message("LINK_DIR: ${LINK_DIR} S_DIR: ${S_DIR}")

# 设置当前目录及其子目录的编译器标志  
set_directory_properties(PROPERTIES COMPILE_FLAGS "-Wall -Wextra")

# 获取当前目录的编译标志
get_directory_property(COMPILE_FLAGS COMPILE_FLAGS)

# 打印获取到的编译标志信息
message("COMPILE_FLAGS: ${COMPILE_FLAGS}")
