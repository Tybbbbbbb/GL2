cmake_minimum_required(VERSION 3.4.1)

# now build app's shared lib
PROJECT(GL2)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17 -Wall")

set(OpenCV_DIR "${CMAKE_CURRENT_SOURCE_DIR}/include/OpenCV-android-sdk/sdk/native/jni")
find_package(OpenCV REQUIRED)

#set(OpenCV_STATIC OFF)
#set(OpenCV_FOUND 1 )
include_directories( ./include ./include/glm ${OpenCV_INCLUDE_DIRS})

add_library(gl2jni SHARED
            gl_code.cpp)

target_include_directories(gl2jni PRIVATE
        ${OpenCV_DIR}/include/opencv2
        )

# add lib dependencies
target_link_libraries(gl2jni
                     ${OpenCV_LIBS}
                      log
                      EGL
                      GLESv3)

