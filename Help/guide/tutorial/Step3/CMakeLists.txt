cmake_minimum_required(VERSION 3.10)

# set the project name and version
project(Tutorial VERSION 1.0)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# should we use our own math functions
# 默认为自定义的库
option(USE_MYMATH "Use tutorial provided math implementation" ON)

# configure a header file to pass some of the CMake settings
# to the source code
configure_file(TutorialConfig.h.in TutorialConfig.h)

# 下一个更改是使 MathFunctions 库的构建和链接成为有条件的。
# add the MathFunctions library
if(USE_MYMATH)
  # add the MathFunctions library
  add_subdirectory(MathFunctions)

  # 请注意使用变量 EXTRA_LIBS 来收集任何可选库，以便稍后链接到可执行文件中。
  list(APPEND EXTRA_LIBS MathFunctions)

  # 变量 EXTRA_INCLUDES 类似地用于可选头文件。
  list(APPEND EXTRA_INCLUDES "${PROJECT_SOURCE_DIR}/MathFunctions")
endif()

# add the executable
add_executable(Tutorial tutorial.cxx)

target_link_libraries(Tutorial PUBLIC ${EXTRA_LIBS})

# 使用要求（requirement）可以更好地控制库或可执行文件的链接和包含行，同时还可以更好地控制 CMake 中目标的传递属性。

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
target_include_directories(Tutorial PUBLIC
                           "${PROJECT_BINARY_DIR}"
                           ${EXTRA_INCLUDES}
                           )
