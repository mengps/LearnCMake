# 要求 CMake 最低版本为 3.16
cmake_minimum_required(VERSION 3.16)

# 定义项目名称为 PROPERTY_TEST，版本号为 1.0，使用 C++ 语言
project(PROPERTY_TEST VERSION 1.0 LANGUAGES CXX)

# 添加一个名为 TEST_TARGET 的可执行文件，其源文件为 test.cpp
add_executable(TEST_TARGET test.cpp)

# 定义一个目标属性 TEST_TARGET，带有简短和详细描述
# 即使不使用 define_property，也可以使用 set_property / set_target_properties 来定义属性
define_property(TARGET PROPERTY TEST_TARGET
    BRIEF_DOCS "A test property"
    FULL_DOCS "A long description of this test property"
)

# 设置目标 TEST_TARGET 的属性 P_1 和 P_2 的值
set_target_properties(TEST_TARGET PROPERTIES 
    P_1 "这是属性P_1的值"
    P_2 "这是属性P_2的值"
)

# 获取目标 TEST_TARGET 的属性 P_1 的值，并将其存储在变量 TEST_TARGET_P1 中
get_target_property(TEST_TARGET_P1 TEST_TARGET P_1)

# 打印变量 TEST_TARGET_P1 的值
message("TEST_TARGET_P1: ${TEST_TARGET_P1}")