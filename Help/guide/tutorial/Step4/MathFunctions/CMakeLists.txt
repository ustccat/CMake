add_library(MathFunctions mysqrt.cxx)

# 使用要求（requirement）可以更好地控制库或可执行文件的链接和包含行，同时还可以更好地控制 CMake 中目标的传递属性。

# state that anybody linking to us needs to include the current source dir
# to find MathFunctions.h, while we don't.
# 记住接口意味着消费者需要但生产者不需要的东西。
target_include_directories(MathFunctions
          INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}
          )
