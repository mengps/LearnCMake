# 要求 CMake 最低版本为 3.16
cmake_minimum_required(VERSION 3.16)

# 定义一个名为 GLOBAL_PROPERTY_TEST 的全局属性
define_property(GLOBAL 
    # 全局属性的名称
    PROPERTY GLOBAL_PROPERTY_TEST
    # 简短的文档说明
    BRIEF_DOCS "A global property test"
    # 完整的文档说明
    FULL_DOCS "A global property test"
)

# 设置全局属性 GLOBAL_PROPERTY_TEST 为 ON
set_property(GLOBAL PROPERTY GLOBAL_PROPERTY_TEST ON)

# 获取全局属性 GLOBAL_PROPERTY_TEST 的值，并将结果存储在变量 IS_GLOBAL 中
get_property(IS_GLOBAL GLOBAL PROPERTY GLOBAL_PROPERTY_TEST)

# 打印变量 IS_GLOBAL 的值，用于确认全局属性是否已设置
message("IS_GLOBAL: ${IS_GLOBAL}")

# 获取当前 CMake 角色，并将结果存储在变量 ROLE 中
get_cmake_property(ROLE CMAKE_ROLE)

# 打印变量 ROLE 的值，用于显示当前 CMake 角色
message("ROLE: ${ROLE}")
