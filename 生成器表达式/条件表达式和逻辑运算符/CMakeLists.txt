cmake_minimum_required(VERSION 3.16)

add_library(MyExecutable STATIC test.cpp)

add_custom_command(
   TARGET MyExecutable PRE_BUILD
   COMMAND ${CMAKE_COMMAND} -E echo "==================================="
)

#条件表达式 $<condition:true_string>
#等价于C++ if (condition == "1") return true_string else return ""
add_custom_command(
   TARGET MyExecutable PRE_BUILD
   COMMAND ${CMAKE_COMMAND} -E echo "[1]: WIN32: ${WIN32} | $<${WIN32}:is win32> | $<0:is 0>"
)

#条件表达式 $<IF:condition,true_string,false_string>
#等价于C++ condition ? true_string : false_string
set(IS_DEBUG "1")
add_custom_command(
   TARGET MyExecutable PRE_BUILD
   COMMAND ${CMAKE_COMMAND} -E echo "[2]: IS_DEBUG: ${IS_DEBUG} | $<IF:${IS_DEBUG},is debug,is release>"
)

#条件表达式 $<BOOL:string>
#等价于C++ if (string) return "1" else return "0"
set(STRING2BOOL "not empty")
add_custom_command(
   TARGET MyExecutable PRE_BUILD
   COMMAND ${CMAKE_COMMAND} -E echo "[3]: STRING2BOOL: ${STRING2BOOL} | $<BOOL:${STRING2BOOL}> | $<$<BOOL:${STRING2BOOL}>:STRING2BOOL is not empty>"
)

add_custom_command(
   TARGET MyExecutable PRE_BUILD
   COMMAND ${CMAKE_COMMAND} -E echo "==================================="
)

#逻辑运算符 $<AND:conditions>
#等价于C++ if (condition && condition && ...) return "1" else return "0"
add_custom_command(
   TARGET MyExecutable PRE_BUILD
   COMMAND ${CMAKE_COMMAND} -E echo "[1]: (1 && 0 && 1) = $<AND:1,0,1>"
)

#逻辑运算符 $<OR:conditions>
#等价于C++ if (condition || condition || ...) return "1" else return "0"
add_custom_command(
   TARGET MyExecutable PRE_BUILD
   COMMAND ${CMAKE_COMMAND} -E echo "[2]: (1 || 0 || 0) = $<OR:1,0,0>"
)

#逻辑运算符 $<NOT:condition>
#等价于C++ if (!condition) return "1" else return "0"
add_custom_command(
   TARGET MyExecutable PRE_BUILD
   COMMAND ${CMAKE_COMMAND} -E echo "[3]: !1 = $<NOT:1>"
)

add_custom_command(
   TARGET MyExecutable PRE_BUILD
   COMMAND ${CMAKE_COMMAND} -E echo "==================================="
)