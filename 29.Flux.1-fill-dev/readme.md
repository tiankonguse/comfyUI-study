# Flux.1 fill dev


## 介绍

Flux.1 fill dev 是 Black Forest Labs 推出的 FLUX.1 Tools 套件中的核心工具之一，专为图像修复和去除而设计。  

Black Forest Labs: https://blackforestlabs.ai/
FLUX.1 Tools 套件: https://blackforestlabs.ai/flux-1-tools/


Flux.1 fill dev 的主要特点：

强大的图像修复和去除功能，效果仅次于商业版 FLUX.1 Fill pro。
卓越的快速理解和跟随能力，精准捕捉用户意图，同时与原始图像保持高度一致性。
先进的引导式蒸馏训练技术，使模型在保持高质量输出的同时更加高效。
友好的许可条款，生成的输出可用于个人、科学和商业目的，详情请参阅 FLUX.1 dev 非商业许可证 。

非商业许可证: https://huggingface.co/black-forest-labs/FLUX.1-dev/blob/main/LICENSE.md


## 目录


```
ComfyUI/
├── models/
│   ├── text_encoders/
│   │    ├── clip_l.safetensors
│   │    └── t5xxl_fp16.safetensors
│   ├── vae/
│   │    └── ae.safetensors
│   └── diffusion_models/
│        └── flux1-fill-dev.safetensors
```


## 模型下载


clip_l.safetensors https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/clip_l.safetensors?download=true
t5xxl_fp16.safetensors  https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp16.safetensors?download=true
ae.safetensors https://huggingface.co/black-forest-labs/FLUX.1-schnell/resolve/main/ae.safetensors?download=true
flux1-fill-dev.safetensors https://huggingface.co/black-forest-labs/FLUX.1-Fill-dev/resolve/main/flux1-fill-dev.safetensors?download=true



## inpainting


工作流: [flux_fill_inpaint.json](./flux_fill_inpaint.json)

prompt: A white translucent silk scarf is wrapped around the neck and flutters in the wind.

输入图片： ![](./flux_fill_inpaint_input.png)  


输出图片: ![](./flux_fill_inpaint_output.png)



## Outpainting


工作流: [flux_fill_dev_outpaint.json](./flux_fill_dev_outpaint.json)

prompt: A futuristic city under a glass shell in the center of the desert.

输入图片：  ![](./flux_fill_dev_outpaint_input.png)


输出图片: ![](./flux_fill_dev_outpaint_output.png)



