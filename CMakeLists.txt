# cmake最低版本及工程名称
cmake_minimum_required(VERSION 3.14)
project(Detector)

# 选择要编译的源文件，凡是要编译的源文件都要列举出来
add_executable(Detector src/detector.cpp src/improcess.cpp) 

# 设置编译方式（"debug"  "release"）
set(CMAKE_BUILD_TYPE Release)

# 设置可执行文件与链接库保存的路径
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

# 设置头文件目录使得系统可以找到对应的头文件
include_directories(${PROJECT_SOURCE_DIR}/include)

#创建共享库
add_library(detector SHARED src/detector.cpp)
add_library(detector_static STATIC src/detector.cpp)

include_directories (
    /home/gaokechen/Detector-darknet/include
    /usr/local/lib
    /usr/local/cuda/lib64
    /usr/lib/x86_64-linux-gnu
    /usr/local/cuda-10.1/targets/x86_64-linux/include
    /home/gaokechen/Downloads/opencv-3.3.1/include      
    /home/gaokechen/Downloads/opencv-3.3.1/include/opencv    
    /home/gaokechen/Downloads/opencv-3.3.1/include/opencv2  
)  
  
target_link_libraries(Detector
    /home/gaokechen/darknet/libdarknet.so
    /home/gaokechen/Downloads/opencv-3.3.1/build/lib/libopencv_core.so
    /home/gaokechen/Downloads/opencv-3.3.1/build/lib/libopencv_highgui.so
    /home/gaokechen/Downloads/opencv-3.3.1/build/lib/libopencv_imgcodecs.so
    /home/gaokechen/Downloads/opencv-3.3.1/build/lib/libopencv_imgproc.so
    /home/gaokechen/Downloads/opencv-3.3.1/build/lib/libopencv_videoio.so
    /usr/local/cuda-10.1/targets/x86_64-linux/lib/libcudnn.so
    /usr/local/cuda-10.1/targets/x86_64-linux/lib/libcudart.so
    /usr/lib/x86_64-linux-gnu/libcublas.so
    /usr/local/cuda-10.1/targets/x86_64-linux/lib/libcurand.so
)  




