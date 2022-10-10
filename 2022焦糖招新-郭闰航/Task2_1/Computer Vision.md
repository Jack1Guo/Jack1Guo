# Task1_2做题前问答

## 计算机以怎样的方式存储一张图片，又是怎样显示它的？

- 图像以数字矩阵的形式存储在计算机中，其中这些数字称为像素值。
- 这些像素值代表每个像素的强度。
- 0代表黑色，255代表白色。
- 数字矩阵称为通道，对于灰度图像，只有一个通道。色彩图像有三个通道（R,G,B）

* 每张图片都是由像素块组成的，每个像素块都是可以由三原色组合而成的，三原色中的每一种颜色都可以用二进制来表示，不同的组合方案则显示不同颜色，在计算机显示图片当中会有压缩图片或解析图片的软件，于是计算机就能够显示图片了。 

## 作为一名 programmer，我们在代码中采用什么数据结构将图片读入？

OpenCV中的Mat

## 如今CV领域已然发展得非常成熟，有哪些研究领域（目标检测、图像生成……）？

图像分类，目标检测，目标追踪，语义分割，实例分割。

**************************************

# 库问题

(1)`Process finished with exit code 132 (interrupted by signal 4: SIGILL)`.  
复制相应的报错信息到CSDN，发现没有对应的版本，因为各个文章的发布时间太早，没有更新后的版本，keras和tensorflow版本对应不上会报错 。

(2)`No moudle named keras.emotion_models`or`moudle 'kreas' has not attribute 'emotion_models'`

(3)`Using tensorflow backend`

(4)` ImportError: Could not import PIL.Image. The use of load_img requires PIL.`

(5)`module ‘cv2‘ has no attribute ‘COLOR_BRG2GRAY_frame‘`or`ValueError: ('Invalid color mode:','gray_framescale', "; expected "rab", "raba", or "grayscale". ")`

(6)`This TensorFlow binary is optimized with oneAPI Deep Neural Network Library`

## 解决方案（Python3.10环境下）

(1) 在pycharm中安装对应库文件，避免了环境版本不同带来的影响。

(2) 经查询已安装keras版本中没有emotion_models这个模块，将`keras.emotion_models`更改为`keras.models`即可正常运行。

(3)tensorflow版本有更新，旧版本的内容不适用，更新至最新版本可以使用。

(4)文件路径有问题，更改文件路径后已解决问题。

(5) 更改色彩名称，该版本对应的黑度为`grayscale`

(6)添加

```
import os
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2'
```

**********************************

# GUI界面不显示

(1)人脸追踪文件路径更新

(2)标准样本图片路径更新

(3)摄像头调用更改为默认值0

```
img2=Image.fromarray(pic2) #这边有个错误（）里面内容应该是pic2
```

*****************************************

# train.py源码问答

### 如何载入数据

使用keras中的ImageDataGenerator函数帮助我们实现对图片数据的读取和处理的API。

flow_from_directory()通过文件夹路径采集数据和标签数组，生成批量增强数据

color_model颜色模式，默认RGB，设置为灰度为单通道的图片

class_model决定了返回的标签组的形式，默认为categorical

### 采用怎样的网络结构

采用卷积神经网络

```
emotion_model = Sequential()
# 第一层需要指出输入的形状(样本数，行，列，通道数)，只指出后三维即可，第一维按batch_size自动指定
# 卷积中滤波器的数量为32，即输出空间的维度
# kernel_size 卷积核大小
emotion_model.add(Conv2D(32, kernel_size=(3, 3), activation='relu', input_shape=(48,48,1)))
emotion_model.add(Conv2D(64, kernel_size=(3, 3), activation='relu'))
# 最大池化层
emotion_model.add(MaxPooling2D(pool_size=(2, 2)))
# 丢弃率
emotion_model.add(Dropout(0.25))

emotion_model.add(Conv2D(128, kernel_size=(3, 3), activation='relu'))
emotion_model.add(MaxPooling2D(pool_size=(2, 2)))
emotion_model.add(Conv2D(128, kernel_size=(3, 3), activation='relu'))
emotion_model.add(MaxPooling2D(pool_size=(2, 2)))
emotion_model.add(Dropout(0.25))

emotion_model.add(Flatten())
emotion_model.add(Dense(1024, activation='relu'))
emotion_model.add(Dropout(0.5))
#最终输出7类
emotion_model.add(Dense(7, activation='softmax'))
```

### 如何设计trainer

使用categorical_crossentropy损失函数和Adam优化器，并设置学习率和学习率衰减因子为1e-6，设置epoch为50，保存权重文件。
