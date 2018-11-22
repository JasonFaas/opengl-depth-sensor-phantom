cmake_minimum_required(VERSION 3.11)
project(Phantom)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(OpenCV_Main "C:/Users/jason/Desktop/OpenCV/opencv-3.4.3")
set(OpenCV_DIR "${OpenCV_Main}/build/install/x86/vc15/lib")

set(OpenCL_Main "C:/Intel/OpenCL/sdk")
set(OpenCL_DIR "${OpenCL_Main}/lib/x86")

set(Kinect_Main "C:/Program Files/Microsoft SDKs/Kinect/v2.0_1409")
set(Kinect_DIR "${Kinect_Main}/Lib/x86")

set(Glfw_Main "C:/Users/jason/Desktop/libraries/glfw/glfw-3.2.1.bin.WIN32")
set(Glfw_DIR "${Glfw_Main}/lib-vc2015")

set(Glad_Main "C:/Users/jason/Desktop/libraries/glad")
set(Glad_DIR "${Glad_Main}")

find_package( OpenCV REQUIRED )
find_package( OpenCL REQUIRED )
#find_package( Kinect REQUIRED )
include_directories(Phantom "${OpenCV_Main}/build/install/include")
include_directories(Phantom "${OpenCL_Main}/include")
include_directories(Phantom "${Kinect_Main}/inc")
include_directories(Phantom "${Glad_Main}/include")
include_directories("glad" PRIVATE "${Glfw_Main}/include")
include_directories(Phantom "${Glfw_Main}/include")

add_library("glad" "${Glad_DIR}/src/glad.c")

#add_executable(Phantom Phantom/HelloWorld/HelloWorld.cpp)
#add_executable(Phantom Phantom/HelloWorld/HelloGlfw.cpp)
#add_executable(Phantom Phantom/HelloWorld/HelloTriangle.cpp)
add_executable(Phantom Phantom/HelloWorld/HelloShaders.cpp)


target_link_libraries (Phantom "${OpenCV_DIR}/opencv_calib3d343.lib" "${OpenCV_DIR}/opencv_core343.lib" "${OpenCV_DIR}/opencv_dnn343.lib" "${OpenCV_DIR}/opencv_features2d343.lib" "${OpenCV_DIR}/opencv_flann343.lib" "${OpenCV_DIR}/opencv_highgui343.lib" "${OpenCV_DIR}/opencv_imgcodecs343.lib" "${OpenCV_DIR}/opencv_imgproc343.lib" "${OpenCV_DIR}/opencv_ml343.lib" "${OpenCV_DIR}/opencv_objdetect343.lib" "${OpenCV_DIR}/opencv_photo343.lib" "${OpenCV_DIR}/opencv_shape343.lib" "${OpenCV_DIR}/opencv_stitching343.lib" "${OpenCV_DIR}/opencv_superres343.lib" "${OpenCV_DIR}/opencv_video343.lib" "${OpenCV_DIR}/opencv_videoio343.lib" "${OpenCV_DIR}/opencv_videostab343.lib")
target_link_libraries (Phantom "${OpenCL_DIR}/OpenCL.lib")
target_link_libraries (Phantom "${Kinect_DIR}/Kinect20.Face.lib" "${Kinect_DIR}/Kinect20.Fusion.lib" "${Kinect_DIR}/Kinect20.lib" "${Kinect_DIR}/Kinect20.VisualGestureBuilder.lib")
target_link_libraries (Phantom "${Glfw_DIR}/glfw3.lib")


target_link_libraries (Phantom "glad")
#target_link_libraries (Phantom "opengl32.lib")
