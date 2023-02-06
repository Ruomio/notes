# OpenCV

## CMakeLists.txt

```cmake
cmake_minimum_required(VERSION 3.25)

project(OpenCV_Demo)

# set the directory of executable files
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)
# set bulid addr
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/build)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/build)
# 打印控制台信息
MESSAGE(STATUS "Current path : ${PROJECT_SOURCE_DIR}")

set(CMAKE_CXX_STANDARD 17)

set(OpenCV_DIR /usr/lib/opencv4)

include_directories(${OpenCV_INCLUDE_DIRS})
find_package(OpenCV REQUIRED)


set(PROJECT_SOURCE_DIR ./src)

set(PROJECT_SOURCES 
    ${PROJECT_SOURCE_DIR}/QuickDemo.h
    ${PROJECT_SOURCE_DIR}/QuickDemo.hpp
    ${PROJECT_SOURCE_DIR}/QuickDemo.cpp
)

add_executable(${PROJECT_NAME} ${PROJECT_SOURCES})

link_directories(${OpenCV_LIBRARY_DIRS})
target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBS})

```

```cmake
#以下四行是新建工程之后自动添加的
project(test_camera)                    #工程名称
cmake_minimum_required(VERSION 2.8)         #cmake版本要求
aux_source_directory(. SRC_LIST)            #添加源文件，把存储源文件的变量赋值给SRC_LIST
add_executable(${PROJECT_NAME} ${SRC_LIST})     #生成执行文件


if( CMAKE_BUILD_TYPE STREQUAL "Release")
  SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O3 -std=c++11 -fPIC")
else()
  SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -O0 -std=c++11 -fPIC")#设置寻找外部库的cmake参数的
endif()
message("*** ${PROJECT_NAME}: Build type:" ${CMAKE_BUILD_TYPE} ${CMAKE_CXX_FLAGS} "***")
#设置cmake位置，
set( CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmakes)
#设置opencv的位置
set(OpenCV_DIR ~/opencv-3.2.0/build)
find_package(OpenCV REQUIRED)

#-------------------------------------- 包含头文件 --------------------------------------
include_directories(${OpenCV_INCLUDE_DIRS})#设置opencv头文件包含路径，类似vs中的include路径
include_directories(${Qt5Widgets_INCLUDE_DIRS})
include_directories(${Boost_INCLUDE_DIRS})
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)


#-------------------------------------- -添加项目- --------------------------------------
#file(GLOB_RECURSE HEADER_FILES ${CMAKE_CURRENT_SOURCE_DIR}/include/*.*h)可以用来添加头文件和源文件
#file(GLOB_RECURSE SOURCE_FILES ${CMAKE_CURRENT_SOURCE_DIR}/src/*.c*)



#-------------------------------------- -添加链接库- --------------------------------------
TARGET_LINK_LIBRARIES(${PROJECT_NAME}
${OpenCV_LIBS}
${Qt5Widgets_LIBRARIES}
${Boost_LIBRARIES}
)
```



## 语法

### size()

> Size(int width,int high) 即 
>
> 而Mat img;对象 img.cols是宽度,  img.rows是高度

### 图像混合 blending

* dst = src1 * a+src2 * (1-a) + gamma;
* a = [0,1]
* addWighted(src1,a,src2,1-a,0.0.dst); 两张原图大小要一样 

### rotate_mirror

* rorate(src,dst,type); -ROTATE_180, -ROTATE_90_CLOCKWISE, -ROTATE_90)COUNTERCLOCKWISE
*  flip(src,dst,type); // type 0(对x轴镜像),1(对y轴镜像),-1(同时镜像)  

### ROI 图像合并

* 把高的图像等比缩放，使之与低的图像高度一致

### ffmpeg处理音视频

抽取音频：

* ffmpeg -i  {imput} -vn {output}; -vn表示不要视频，-an表示不要音频

剪切音频：

* ffmpeg -ss 0:0:30 -t 0:0:20 -i {input} -c {copy output}; 表示从第30秒开始，剪切20秒， -c表示生成额外文件，保留源文件

### 视频处理

#### read 

* 表示解码和转格式显示，可分为两个步骤，读帧解码（grab）和转换颜色格式示（retrieve）

```c++
inline void QuickDemo::video_demo(VideoCapture video){
    if(!video.isOpened()){
        cout<<"open video failed!"<<endl;
        getchar();      // 使程序停住
    }
    cout<<"open video success!"<<endl;
    Mat frame;
    while(true){
        // 解码和转换
        // if(!video.read(frame)) break;
        // 单独解码 grab
        if(!video.grab()) break;
        // 转换颜色格式 retrive
        if(!video.retrieve(frame)) break; 
        imshow("video",frame);
        waitKey(200);
    }
    getchar();
}
```

#### 视频、相机属性

cv::set(); cv::get();

> CAP_PROP_FPS 帧率
>
> CAP_PROP_FRAME_COUNT 总帧数
>
> CAP_PROP_POS_FRAMES 播放帧的位置
>
> CAP_PROP_FRAME_WIDTH/HEIGHT 视频帧的宽度和高度

* 设置播放进度最好使用帧位置，可减少一次转换，因为毫秒位置会转化为帧位置

读视频文件要主动release，来释放内存

open

> open(const String& filename, 
>
> ​    int fourcc, 
>
> ​	double fps, Size franeSize, bool isColor = true)
>
> release



## Qt OpenCV显示的图片向右倾斜且灰色的错误

> Mat和QImage的数据不相互对应，如果从Mat转换到QImage的过程中参数设置不对，数据就会出问题
>
> 在QImage中增加step的参数即可
>
> ```c++
> QImage disImage_1 = QImage((const unsigned char*)(srcImage_1.data), srcImage_1.cols, srcImage_1.rows,srcImage_1.step, QImage::Format_RGB888);
> ```
