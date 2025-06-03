# Flux.1 文本到图像


## 简介


Flux 是最大的开源文本转图像生成模型之一，拥有 120 亿个参数，原始文件大小约为 23GB。
它由 Black Forest Labs 开发，该团队由前 Stable Diffusion 团队成员创立。
Flux 以其出色的图像质量和灵活性而闻名，能够生成高质量、多样化的图像。


目前，Flux.1 模型主要有以下几个版本：

Flux.1 Pro： 性能最佳的模型，闭源，仅通过 API 调用可用。
Flux.1 dev： 开源但仅限于非商业用途，从 Pro 版本提炼而来，性能接近 Pro 版本。
Flux.1 schnell： 使用 Apache2.0 许可，仅需 4 个步骤即可生成镜像，适合低配置硬件。

Flux.1 Model Features  Flux.1 模型特点

混合架构： 结合 Transformer 网络和扩散模型的优势，有效地融合文本和图像信息，提高生成的图像与提示之间的对齐精度，对复杂提示具有出色的保真度。
参数规模： Flux 拥有 12B 个参数，可以捕捉更复杂的模式关系并生成更逼真、更多样化的图像。
支持多种风格： 支持多种风格，对各类图像均有出色表现。


## Flux.1 Dev

Flux 完整版： 性能最佳，但需要更大的 VRAM 资源和安装多个模型文件。

### 目录结构

```
ComfyUI/
├── models/
│   ├── text_encoders/
│   │   ├── clip_l.safetensors
│   │   └── t5xxl_fp16.safetensors
│   ├── vae/
│   │   └── ae.safetensors
│   └── diffusion_models/
│       └── flux1-dev.safetensors
```


### 下载地址


clip_l.safetensors https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/clip_l.safetensors?download=true
t5xxl_fp16.safetensors https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp16.safetensors?download=true
ae.safetensors https://huggingface.co/black-forest-labs/FLUX.1-schnell/resolve/main/ae.safetensors?download=true
flux1-dev.safetensors https://huggingface.co/black-forest-labs/FLUX.1-dev/resolve/main/flux1-dev.safetensors



### 工作流


[flux_dev_t5fp16.json](./flux_dev_t5fp16.json)


![](./flux_dev_t5fp16_output.png)



### 效果


prompt: beautiful girl, East Asian beauty, sitting on the floor





## Flux.1 Schnell

### 目录结构

```
ComfyUI/
├── models/
│   ├── text_encoders/
│   │   ├── clip_l.safetensors
│   │   └── t5xxl_fp8_e4m3fn.safetensors
│   ├── vae/
│   │   └── ae.safetensors
│   └── diffusion_models/
│       └── flux1-schnell.safetensors
```


### 下载地址

clip_l.safetensors https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/clip_l.safetensors?download=true
t5xxl_fp8_e4m3fn.safetensors https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp8_e4m3fn.safetensors?download=true
ae.safetensors https://huggingface.co/black-forest-labs/FLUX.1-schnell/resolve/main/ae.safetensors?download=true
flux1-schnell.safetensors https://huggingface.co/black-forest-labs/FLUX.1-schnell/resolve/main/flux1-schnell.safetensors


### 工作流


[flux_schnell_t5fp16.json](./flux_schnell_t5fp16.json)

### 效果


![](./flux_text2image_one.png)




## Flux FP8 

fp8 版本是原版 Flux.1 fp16 版本的量化版本，在一定程度上画质会低于 fp16 版本，但所需的 VRAM 也更少，并且只需安装一个模型文件即可尝试运行。


### Flux.1 Dev FP8


flux1-dev-fp8.safetensors https://huggingface.co/Comfy-Org/flux1-dev/resolve/main/flux1-dev-fp8.safetensors?download=true
目录: ComfyUI/models/checkpoints/

工作流: [flux_dev_fp8.json](./flux_dev_fp8.json)


效果：![](./flux_text2image_two.png)


### Flux.1 Schnell FP8

flux1-schnell-fp8.safetensors https://huggingface.co/Comfy-Org/flux1-schnell/resolve/main/flux1-schnell-fp8.safetensors?download=true
目录: ComfyUI/models/checkpoints/

工作流: [flux_schnell_fp8.json](./flux_schnell_fp8.json)

效果: ![](./flux_text2image_three.png)


## 参考

https://docs.comfy.org/tutorials/flux/flux-1-text-to-image

