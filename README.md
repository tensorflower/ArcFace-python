# 虹软python api
## 1. 简介
python调用虹软人脸识别v2.2版本动态链接库完成人脸检测/跟踪，人脸识别，人脸3D角度识别，性别、年龄，RGB活体，IR活体识别

## 2. 使用
- 去官网下载人脸识别SDK，选择 `2.2` `c++` 版本 将以下两个文件放入到lib目录下

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

- 注意：测试图片的宽度需为4的整数倍

- demo 内容和提供的c++demo 基本类似，更多状态码内容对照下载的SDK文件中doc目录下的文档即可
