# OpenCV

**源码位置**：在/usr/share/opencv4中，具体如果不知道的话可以通过以下指令找到他sudo pacman -Ql opencv-samples。
**头文件位置**：在/usr/include/opencv4
**依赖库**：在/usr/lib64。

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

## bug排查

### Qt OpenCV显示的图片向右倾斜且灰色的错误

> Mat和QImage的数据不相互对应，如果从Mat转换到QImage的过程中参数设置不对，数据就会出问题
>
> 在QImage中增加step的参数即可
>
> ```c++
> QImage disImage_1 = QImage((const unsigned char*)(srcImage_1.data), srcImage_1.cols, srcImage_1.rows,srcImage_1.step, QImage::Format_RGB888);
> ```

## 滤波处理

```c++
// 锐化
Mat kernel = Mat_<char>(3,3)<< 0,-1,0,-1,5,-1,0,-1,0);
// 模糊
Mat kernel = Mat::ones(5,5,CV_32F)/(float)(25); 
// 边缘处理
Mat kernel = (Mat_<int>(2,2)<< 1,0,0,-1);

//调用处理
filter2D(src,dst,src.depth(),dst);
```

## PCA 原理和应用

### 概念

*  principal component analysis（主成分分析）, 通过线性变换将原始数据变换为一组各维度线性无关的表示，可用于提取数据的主要特征分量，常用于高维数据的降维处理。

+ PCA过程

  将n维特征映射到k维上(k<<n 降维) , k维是一个全新的正交特征，这个k维成为主成分。   



### 原理

```markdown
PCA（Principal Component Analysis）是一种常用的降维算法，它的主要原理如下：

数据中心化：首先对数据进行中心化处理，即将每个特征的平均值都减去，使得每个特征的均值为0。

计算协方差矩阵：然后计算样本的协方差矩阵。协方差矩阵描述了不同特征之间的关系，其对角线上的元素表示每个特征的方差，非对角线上的元素表示不同特征之间的协方差。

特征值分解：对协方差矩阵进行特征值分解，得到特征值和特征向量。特征值表示数据在特征向量方向上的方差大小，特征向量表示数据在该方向上的投影。

选取主成分：根据特征值的大小，选择前k个最大的特征值对应的特征向量作为主成分。这些主成分构成了新的特征空间。

投影到新空间：将原始数据投影到新的特征空间中，得到降维后的数据。

通过PCA算法可以将高维数据降维到低维，并且保留了原始数据的主要信息。PCA在数据压缩、图像处理、信号处理等领域有着广泛的应用。

```



## Fisher算法

### 原理

```markdown
Fisher算法（又称为线性判别分析，LDA）是一种常用的分类算法，它的主要原理如下：

计算类内散度矩阵和类间散度矩阵：对于给定的训练集，首先计算每个类别的均值向量和协方差矩阵。然后，计算类内散度矩阵Sw和类间散度矩阵Sb，其中类内散度矩阵描述了同一类别内部数据点之间的距离，类间散度矩阵描述了不同类别之间的距离。

计算投影向量：通过计算Sw-1Sb的特征向量，可以得到一个或多个投影向量。这些投影向量被称为“判别向量”，它们被用来将数据点从原始空间映射到新的低维空间。

选择最佳投影向量：通常情况下，我们只选择第一个判别向量作为投影向量，因为它具有最大的判别能力。具体来说，我们将Sw-1Sb的特征向量按照对应的特征值大小排序，选择对应最大特征值的特征向量作为投影向量。

投影到新空间：将原始数据点投影到新的低维空间中，得到降维后的数据。对于新的测试样本，也可以使用同样的投影向量将其映射到低维空间中，并进行分类。

Fisher算法与PCA类似，都是一种降维算法。但是它们的目标不同：PCA主要用于保留原始数据的主要信息，而Fisher算法则更加注重在低维空间中最大化类别之间的距离，从而提高分类性能。
```



## LBP算法

### 原理

```markdown
LBP（Local Binary Pattern）算法是一种用于纹理分析的图像处理算法，其主要原理如下：

选择像素点：对于图像中的每个像素点，选择其周围的若干个像素点（通常是8个或16个），并计算它们与该像素点的灰度值差异。

计算二进制码：将这些灰度值差异与该像素点的灰度值进行比较，将大于等于该像素点灰度值的像素点标记为1，否则标记为0。得到一个二进制码，例如"11010111"。

转换为十进制数：将得到的二进制码转换为十进制数，作为该像素点的LBP值。

统计LBP直方图：对于整张图像，统计每个像素点的LBP值，并生成一个LBP直方图。LBP直方图表示了图像中不同LBP值出现的频率。

应用于纹理分析：LBP算法可以用于纹理分类、纹理识别和纹理检索等领域。通过比较不同图像的LBP直方图，可以判断它们之间的相似度。

LBP算法简单、高效、易于实现，因此在图像处理领域有着广泛的应用。它可以用于人脸识别、行人检测、物体识别等任务中，提高分类和识别的准确率。
```



## LDA

+ 与PCA对所有样本数据求平均值不同的是，LDA是对每一类样本求平均值，在一定程度上减少光照和人脸姿态带来的影响，有助于提升识别效果。但对上下偏转比较敏感。

## LBPA

+ 局部二值模式直方图的人脸世界算法，进行的大多是整数计算，效率较高，且对光照具有比较好的鲁棒性。对轮廓和姿态检测较好，对颜色不敏感。

## 人脸识别流程

1. 图像采集，静态图片，视频文件，摄像头，流媒体
   + imread)() 
 2. 图像预处理，简化图像，缩放，二值化，灰度图，滤波处理

    + equalizeHist() 直方图均值化处理
 3. 特征提取，HARR, HOG, LBP...

    + CascadeClassifier 级联分类器
 4. 匹配识别，分类对比
	+ EigenFace, featureFace(更好)

## 活体检测

1. 动作配合
2. 热成像
3. 近红外光
4. 光流判断 



# Dlib 另一个深度学习开源库

包含高效的残差神经网络



# 机器学习

## 分类

1. 监督学习：计算机从带标签的数据中学习，找到输入数据与标签之间的关系映射
2. 无监督学习： 发现给定数据的输入结构
3. 强化学习：计算机与环境互动，从而实现目标并从错误中吸取教训。可分为一下几类：
   1. 分类：输入的空间可以分为N类，给定的样本的预测结果则是这些被训练的类之一。
   2. 回归：输出是连续值，而不是像分类那样的离散值。
   3. 聚类：输入被分为N组，通常通过无监督训练完成。
   4. 密度估计：找出输入的分布。

## 方法

> 1. 支持向量机（SVM）
> 2. 人工神经网络（ANN）
> 3. 聚类
> 4. k-最近邻
> 5. 决策树
> 6. 深度学习（DNN）

## OpenCV 机器学习方法

OpenCV实现了其中的八种机器学习算法，所有算法都继承自StatModel类：

+ 人工神经网络
+ 随机树
+ 期望最大化
+ k-最近邻
+ 逻辑回归
+ 朴素贝叶斯分类器
+ 支持向量机
+ 随机梯度下降SVM