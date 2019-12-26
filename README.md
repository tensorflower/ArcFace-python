# 虹软python api(支持最新版本)
## 1. 简介
python调用虹软人脸识别v2.2版本动态链接库完成人脸检测/跟踪，人脸识别，人脸3D角度识别，性别、年龄，RGB活体，IR活体识别

## 2. 使用
- 去官网下载人脸识别SDK，选择 `c++`  2.2或者3.0版本进行下载，下载后将以下两个文件放入到lib目录下

&ensp;&ensp;&ensp;&ensp;https://ai.arcsoft.com.cn/product/arcface.html

&ensp;&ensp;&ensp;&ensp; 将下载sdk中lib目录下的:

&ensp;&ensp;&ensp;&ensp; `libarcsoft_face_engine.dll` `libarcsoft_face.dll` (windows)

&ensp;&ensp;&ensp;&ensp; `libarcsoft_face_engine.so` `libarcsoft_face.so` (linux)


- 修改 `demo.py` 文件中的 `APPID` 与 `SDKKey` 变量

```python
    APPID = b''
    SDKKey = b''
```

- 示例依赖 `opencv` ,安装`opencv`(若已有cv2模块则忽略)

```key
    pip install -i https://pypi.tuna.tsinghua.edu.cn/simple opencv-python
``` 

- 执行测试代码
`python demo.py`

<div align=center>
     <img src="./asserts/1.jpg"  />
     <img src="./asserts/2.jpg"  />
</div>

```key
    相似度:0.9455885291099548
```
## 注意

- demo 内容和提供的c++ demo 基本类似，更多返回状态码内容对照下载的SDK文件中doc目录下的文档即可

<<<<<<< HEAD
- demo 内容和提供的c++ demo 基本类似，更多状态码内容对照下载的SDK文件中doc目录下的文档即可

##### 3.虹软的配个函数都会返回一盒状态码，要做好状态码的判断工作，确保使用正确，如果状态码 返回值不是 MOK(值为0)，说明函数执行出错，可以对照 doc文档中的错误码解释对照 
##### 4. 第一次运行代码需要联网，因为会做激活操作，首次运行激活成功后会得到一个ArcFace64.dat文件，当有此文件以后，可以不用执行激活代码
##### 5.涉及到传入图片的函数操作，要确保送入的图片宽度为 4 的整数倍，如果不是则要提前做好裁剪，或者做resize操作。
##### 6.当需要运行视频人脸检测的话可以将 初始化引擎 函数中 ASF_DETECT_MODE_IMAGE 改为 ASF_DETECT_MODE_VIDEO即代表追踪模式，这样可以减少人脸检测的消耗，并且此时返回的人脸信息中的faceID 将会有值，这在视频人脸识别中很有用，可以减少人脸重复提取识别。
###### 7. 特征值和人脸属性检测可能会失败。虹软在做特征提取和属性提取这些功能时会对人脸区域有一个判断操作，如果人脸模糊，或者提供的人脸坐标位置不对有偏差，会返回81925(人脸特征检测结果置信度低)错误码。所以一定要对返回状态码引起重视。
###### 8.虹软有两个描述人脸检测位置和角度信息的对象`ASF_SingleFaceInfo `（单人脸信息）`ASF_MultiFaceInfo`（多人脸信息），人脸识别流程是先检测到人脸，再对人脸提取特征值信息，再用特征值信息比较相似度。虹软人脸检测时返回`ASF_MultiFaceInfo `对象（哪怕只检测到了一个人），   用于提取人脸特征信息的函数需要 输入 `ASF_SingleFaceInfo` 的对象，因此在提取特征信息时，需要根据 `ASF_MultiFaceInfo` 中的信息 构建 `ASF_SingleFaceInfo`对象来提取特征值，除了 提取特征值函数外，虹软的其他人脸属性 提取，比如：*年龄/性别识别，活体检测，人脸3D角度* 等功能都是要送入`ASF_MultiFaceInfo` 对象，但是其中活体检测又要求单张大图片中只能检测一个活体，超出返回未知，而3D角度检测单张大图时最多返回4个 人脸的3D角度值，这些地方可能不太好控制，需要注意。
=======
- 虹软的配个函数都会返回一盒状态码，要做好状态码的判断工作，确保使用正确，如果状态码 返回值不是 MOK(值为0)，说明函数执行出错，可以对照 doc文档中的错误码解释对照 

- 涉及到传入图片的函数操作，要确保送入的图片宽度为 4 的整数倍，如果不是则要提前做好裁剪，或者做resize操作。

- 当前默认为图片检测模式，人脸属性值中的faceID始终为空，当需要运行视频人脸检测的话可以将 初始化引擎 函数中 ASF_DETECT_MODE_IMAGE 改为 ASF_DETECT_MODE_VIDEO即代表追踪模式，这样可以减少人脸检测的消耗，并且此时返回的人脸信息中的faceID 将会有值，这在视频人脸识别中很有用，可以减少人脸重复提取识别。

- 特征值和人脸属性检测可能会失败。虹软在做特征提取和属性提取这些功能时会对人脸区域有一个判断操作，如果人脸模糊，或者提供的人脸坐标位置不对有偏差，会返回81925(人脸特征检测结果置信度低)错误码。所以一定要对返回状态码引起重视。

- 虹软有两个描述人脸检测位置和角度信息的对象`ASF_SingleFaceInfo `（单人脸信息）`ASF_MultiFaceInfo`（多人脸信息），人脸识别流程是先检测到人脸，再对人脸提取特征值信息，再用特征值信息比较相似度。虹软人脸检测时返回`ASF_MultiFaceInfo `对象（哪怕只检测到了一个人），   用于提取人脸特征信息的函数需要 输入 `ASF_SingleFaceInfo` 的对象，因此在提取特征信息时，需要根据 `ASF_MultiFaceInfo` 中的信息 构建 `ASF_SingleFaceInfo`对象来提取特征值，除了 提取特征值函数外，虹软的其他人脸属性 提取，比如：*年龄/性别识别，活体检测，人脸3D角度* 等功能都是要送入`ASF_MultiFaceInfo` 对象，但是其中活体检测又要求单张大图片中只能检测一个活体，超出返回未知，而3D角度检测单张大图时最多返回4个 人脸的3D角度值，这些地方可能不太好控制，需要注意。
>>>>>>> ded889fcdc4f53ba041d94a27a4e772a67cf9857
