# Stable Cascade 文生图

Stable Cascade 是 stability.ai 在2024年2月份发布的文本转图像模型。  

这种创新的文本转图像模型引入了一种有趣的三​​阶段方法，为质量、灵活性、微调和效率设定了新的基准，重点是进一步消除硬件障碍。


stage c： the model generates a low resolution latent, the default compression of 42 means that the width and height of the stage c latent are 1024 divided by 42.
stage b where the low resolution stage c latent is passed to the stage b model as conditioning. Stage b takes the low resolution latent and upscales it to a higher resolution one. 




github: https://github.com/Stability-AI/StableCascade
huggingface: https://huggingface.co/stabilityai/stable-cascade


## 下载模型

首先下载 [stable_cascade_stage_b.safetensors](https://huggingface.co/stabilityai/stable-cascade/resolve/main/comfyui_checkpoints/stable_cascade_stage_b.safetensors?download=true) 和 [stable_cascade_stage_c.safetensors](https://huggingface.co/stabilityai/stable-cascade/resolve/main/comfyui_checkpoints/stable_cascade_stage_c.safetensors?download=true) 检查点并将它们放入 ComfyUI/models/checkpoints 文件夹中。  


另外还需要下载控制网络和内部绘制中需要使用得到的控制网络：[stable_cascade_canny.safetensors](https://huggingface.co/stabilityai/stable-cascade/blob/main/controlnet/canny.safetensors)、[stable_cascade_inpainting.safetensors](https://huggingface.co/stabilityai/stable-cascade/blob/main/controlnet/inpainting.safetensors)，并将其保存在 ComfyUI/models/controlnet 文件夹中。


## 下载工作流


工作流: [stable_cascade_text_to_image.json](./stable_cascade_text_to_image.json)  


## prompt  



### 瓶子


```prompt
evening sunset scenery blue sky nature, glass bottle with a fizzy ice cold freezing rainbow liquid in it
```


![](./txt2img_one.png)


### 洗澡自拍


```prompt
mirror selfie, Chinese beautiful girl taking a photo while showering, sitting on floor, legs apart,   phone not covering body, focuses on showing the legs and figure, the posture should be natural and in line with the logic of real selfies, the body proportions should not be too exaggerated, and the mobile phone should reflect the reality, and restore the real female skin texture.
```

![](./txt2img_two.png)


## Next 

[Next](../04.SC-img2img/readme.md)
