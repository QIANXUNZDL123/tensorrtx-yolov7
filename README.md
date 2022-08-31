# yolov7

The Pytorch implementation is [WongKinYiu/yolov7](https://github.com/WongKinYiu/yolov7).

## environment

### win10  vs2019 cuda10.2 cudnn7.6.5 tensorrt7.0

## Different versions of yolov7

Currently, we support yolov7 v1.0

- For yolov7 v1.0, download .pt from [yolov7 release v1.0](https://github.com/WongKinYiu/yolov7/releases/tag/v0.10), `git clone -b v1.0 https://github.com/WongKinYiu/yolov7` and `https://github.com/QIANXUNZDL123/tensorrtx-yolov7.git`, then follow how-to-run in current page.


## Config

- Choose the model tiny/v7/x/d6/w6/e6/e6e from command line arguments.
- Input shape defined in yololayer.h
- Number of classes defined in yololayer.h, **DO NOT FORGET TO ADAPT THIS, If using your own model**
- INT8/FP16/FP32 can be selected by the macro in yolov5.cpp, **INT8 need more steps, pls follow `How to Run` first and then go the `INT8 Quantization` below**
- GPU id can be selected by the macro in yolov5T.cpp
- NMS thresh in yolov5T.cpp
- BBox confidence thresh in yolov5T.cpp
- Batch size in yolov5T.cpp

## How to Run, yolov7-tiny as example

1. generate .wts from pytorch with .pt, or download .wts from model zoo

```
// download https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7-tiny.pt
cp {tensorrtx-yolov7}/gen_wts_trts.py {WongKinYiu}/yolov7
cd {WongKinYiu}/yolov7
python gen_wts_trtx.py -w yolov7-tiny.pt -o yolov7-tiny.wts
// a file 'yolov7-tiny.wts' will be generated.
```

2. to change your cuda path and opencv path also tensorrt path

```
cd {tensorrtx-yolov7}/
// update CLASS_NUM in yololayer.h if your model is trained on custom dataset
change model_check = "-s" -s is generate engine   also model_check = "-d" is run engine 
```


<p align="center">
<img src="https://github.com/QIANXUNZDL123/tensorrtx-yolov7/blob/master/result/yolov7x-car.jpg">
</p>

<p align="center">
<img src="https://github.com/QIANXUNZDL123/tensorrtx-yolov7/blob/master/result/yolov7e6e-car.jpg">
</p>





