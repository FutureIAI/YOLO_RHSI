# YOLO-RHSI: 基于高光谱重建的FPC缺陷检测

## 1. 项目简介

本项目是一个结合了**光谱重建**与**目标检测**的缺陷检测方案，为柔性电路板（FPC）的缺陷检测而设计。

其核心流程是：首先利用光谱重建网络将常规的 **RGB 图像** 转换为信息更丰富的 **高光谱图像 (HSI)**，然后将其输入到 **YOLO-RHSI** 算法中进行缺陷检测。

## 2. 核心技术与致谢

本项目中的光谱重建模块基于以下优秀的开源工作，在此向原作者表示诚挚的感谢：

- **[MST++: Multi-Stage Spectral-wise Transformer for Spectral Reconstruction](https://github.com/caiyuanhao1998/MST-plus-plus)**

采用了其核心思想来完成从 RGB 到高光谱图像的转换。

## 3. 准备预训练权重

在开始之前，需要下载必要的预训练模型权重。

- **光谱重建模型权重**:
(1)  首先下载预训练权重 ([Google Drive](https://drive.google.com/drive/folders/1G1GOA0FthtmOERJIJ0pALOSgXc6XOfoY?usp=sharing) / [Baidu Disk](https://pan.baidu.com/s/14L6T5SsUejepsc63XS9Xsw), code: `mst1`) 
(2)  将预训练权重放在 MST_plus_plus/predict_code/model_zoo目录下


## 4. 准备数据集

1、按照YOLO官方结构组织数据集：
2、 在 `dataset.yaml` 文件中配置数据集路径和类别信息。

## 5. 模型训练

1、在训练的`yolov8s_RHSI.yaml`文件中 设置Spectral_Reconstruction为选用的光谱重建算法（默认为MST++）
2、设置`default.yaml`文件超参数 
3、运行`train.py`

## 6. 模型验证

使用 `val.py` 脚本来评估训练好的模型的性能。

## 7. 模型预测

使用 `predict.py` 对图像进行缺陷检测。
