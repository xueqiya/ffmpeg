cmake_minimum_required(VERSION 3.17)
project(ffmpeg)

# 编译参数，可以加参数用来指定链接库路径，但要下面link_directories()方法二选一
# set(CMAKE_C_FLAGS...)如果项目只有.c; set(CMAKE_CXX_FLAGS...):只要你的项目中含有.cpp
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -L${CMAKE_SOURCE_DIR}/ffmpeg/lib")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -L${CMAKE_SOURCE_DIR}/ffmpeg/lib")

# 头文件路径
include_directories(${PROJECT_SOURCE_DIR}/ffmpeg/include)

# 链接库路径
# 与set(CMAKE_C_FLAGS...)/set(CMAKE_CXX_FLAGS...)二选一
link_directories(${PROJECT_SOURCE_DIR}/ffmpeg/lib)

# IDE自动添加新的项目文件进来
add_executable(ffmpeg main.cpp)

# 启用哪些FFMPEG库，第一个参数为target，即项目名称
target_link_libraries(ffmpeg avformat avcodec avfilter avutil swresample swscale)
