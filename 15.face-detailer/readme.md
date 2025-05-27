# Face Detailer 重新生成脸部


Face Detailer 非常适合恢复照片、电影和动画中的人物面部




## Face Detailer (pipe)



- ComfyUI Impact Pack  ComfyUI 影响包
- Ultralytics Models  Ultralytics 模型
- https://github.com/ultralytics/assets/releases - download the additional model yolov8m-seg.pt
- EpiCRealism 模型下载地址 https://huggingface.co/philz1337x/epicrealism/blob/f22dc0ceeed8bd6d64a90b1e684ecd887aa37b40/epicrealism_naturalSinRC1VAE.safetensors?utm_source=chatgpt.com
- sam_vit_b_01ec64.pth: model 里搜索 sam，下载 ViT-B SAM model
- EfficientSAM： model 里搜索 EfficientSAM， 下载 efficient_sam_s_cpu.jit  和 efficient_sam_s_gpu.jit
- Face Detailer:  node 里搜索 ComfyUI Impact Pack 安装。
- face_yolov8m (bbox) : model 里搜索 face_yolov8m，安装
- person_yolov8m (segm) : model 里搜索 person_yolov8m，安装
- yolov8m-seg.pt : 下载地址 https://github.com/ultralytics/assets/releases， 放在  models/ultralytics/segm/ 目录中。



### 工作流


[face_detailer.json](./face_detailer.json)



### 错误


修改 comfyui-impact-subpack node 的 modules/subcore.py 代码，orig_torch_load 的第二个参数是 Dict，都加上 `load_kwargs['weights_only'] = False`。  

```
UltralyticsDetectorProvider
Weights only load failed. This file can still be loaded, to do so you have two options, [1mdo those steps only if you trust the source of the checkpoint[0m.
(1) In PyTorch 2.6, we changed the default value of the `weights_only` argument in `torch.load` from `False` to `True`. Re-running `torch.load` with `weights_only` set to `False` will likely succeed, but it can result in arbitrary code execution. Do it only if you got the file from a trusted source.
(2) Alternatively, to load with `weights_only=True` please check the recommended steps in the following error message.
WeightsUnpickler error: Unsupported global: GLOBAL getattr was not an allowed global by default. Please use `torch.serialization.add_safe_globals([getattr])` or the `torch.serialization.safe_globals([getattr])` context manager to allowlist this global if you trust this class/function.

Check the documentation of torch.load to learn more about types accepted by default with weights_only https://pytorch.org/docs/stable/generated/torch.load.html.
```


## Face Detailer + Ultimate SD Upscale



### 工作流


[face-detaile-upscaler.json](./face-detaile-upscaler.json)


### Installation  安装


- ComfyUI Impact Pack
- Ultimate SD Upscale
- 4x_foolhardy_Remacri.pth
- 


## Face Detailer (Double Pass)


### 工作流


[face-detailer-2pass.json](./face-detailer-2pass.json)


### Installation  安装

- ComfyUI Impact Pack
- Face Detailer 节点
- 


##  Face Detailer + SDXL




“Load Image”节点中的初始图像。
上方的Load Checkpoint节点中的 SDXL base model。
下方的Load Checkpint节点中的 SDXL refiner model。
新图像的正向提示和反向提示。



## Face Detailer (SD v1.5)


### 工作流

[face-detailer-txt2img.json](./face-detailer-txt2img.json)




## Face Detailer 和 ControlNet 

[face-detailer-ControlNet-txt2img.json](./face-detailer-ControlNet-txt2img.json)

模型需要选择 SD1.5

```
SEGSDetailer
linear(): input and weight.T shapes cannot be multiplied (77x2048 and 768x320)
```

## 参考


https://learn.thinkdiffusion.com/comfyui-face-detailer/

https://stable-diffusion-art.com/adetailer/
https://github.com/ZHO-ZHO-ZHO/ComfyUI-YoloWorld-EfficientSAM