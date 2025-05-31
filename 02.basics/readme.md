# 基础知识

## Load Checkpoint 节点


用于生成图像的 checkpoint 模型（ .safetensors, .ckpt ）。


有 3 个主要组成部分：

- CLIP 模型：将文本转换为 Unet 可以理解的格式
- Unet：执行“扩散”过程，即对图像进行逐步处理，我们称之为生成
- VAE：将图像从潜在空间解码到像素空间（在进行 img2img 时也用于将常规图像从像素空间编码到潜在空间）

## CLIP Text Encode 节点


Load Checkpoint 节点的 CLIP 输出连接到 CLIP Text Encode 节点。


CLIP 模型用于将文本转换为 Unet 可以理解的格式（文本的数字表示），我们称之为嵌入 ( Embeddings )。


CLIP Text Encode 节点将 Checkpoint 的 CLIP 模型作为输入，将提示（ positive 和 negative ）作为变量，执行编码过程，并将这些嵌入输出到下一个节点，即采样器 ( KSampler )。



## KSampler


在 Stable Diffusion 中，图像由称为采样的过程生成。


在 ComfyUI 中，这个过程发生在 KSampler 节点。这是实际的“生成”部分，因此您会注意到，当您排队提示时，KSampler 需要花费最多的时间来运行。


KSampler 接受以下输入：


- model：来自 Load Checkpoint 节点的 MODEL 输出（ Unet ）
- positive：来自 CLIP Text Encode 节点的 positive prompt
- negative：来自 CLIP Text Encode 节点的 negative prompt
- latent_image：潜在空间中的图像（ Empty Latent Image 节点）


由于我们仅从提示（ txt2img ）生成图像，因此我们使用 Empty Latent Image 节点。

您也可以将实际图像传递给 KSampler 而执行 img2img。


### Ksampler中的denoise

#### 在图生图（Image-to-Image）中：

当使用 ComfyUI 进行图生图操作时，Denoise 决定新生成的图像与原始图像的相似度。

Denoise = 0.2-0.4（低）：轻微修改，保留原始图像大部分内容，适合修复细节或微调色彩。例如：去除噪点、优化图像细节、颜色调整。
Denoise = 0.5-0.7（中）：适度更改，生成的图像在内容和风格上有一定变化。例如：更换背景、调整风格（如漫画风、油画风）。
Denoise = 0.8-1.0（高）：大幅度改动，生成的图像与输入图像差异较大，接近重新生成。适合进行创意生成或大幅度内容改造。

#### 在局部修复（Inpainting）中：

当使用遮罩（Mask）对图像进行局部修复时，Denoise 控制新内容的填充程度：

Denoise 低：适合补全缺失的细节，填充较小区域，如修复缺损部分。
Denoise 高：适合对局部区域进行完全替换，如更换人物面部或背景。


#### 在超分辨率（Upscaling）中：


在对低分辨率图像进行放大时，Denoise 控制放大后图像的锐化程度：

Denoise 低：仅对图像进行分辨率提升，保持原始内容。
Denoise 高：结合 AI 进行重新渲染，创造更多细节，适合风格化放大。


### 总结：

| 任务类型 | 推荐 Denoise 值 |  适用场景 | 
|:-:|:-:|:-:|
| 图像微调 | 0.2 - 0.4        | 颜色调整、修复模糊部分 | 
| 风格转换  | 0.5 - 0.7        |  生成不同风格或改变细节 | 
| 内容重塑  | 0.8 - 1.0        |  大幅度更改图像，几乎生成全新内容 | 
| 局部修复（Inpainting） | 0.3 - 0.6 | 局部修改或填充，保留整体风格 | 
| 生成新图像  |  1.0  |  依靠文本提示完全重新生成新图像  |


## CFG scale  CFG 尺度

分类器自由指导尺度是一个参数，用于控制模型应在多大程度上尊重您的提示。

1 – Mostly ignore your prompt.
1 – 基本上忽略您的提示。
3 – Be more creative.
3 – 更具创造力。
7 – A good balance between following the prompt and freedom.
7 – 遵循提示和自由之间取得良好的平衡。
15 – Adhere more to the prompt.
15 – 更多地遵循提示。
30 – Strictly follow the prompt.
30 –严格遵循提示。

## VAE


VAE Decode 节点需要 2 个输入：

- Checkpoint 模型自带的 VAE（您也可以添加自己的 VAE）
- KSampler 已完成去噪的潜在空间图像（ latent space image ）


VAE 用于将图像从潜在空间转换到像素空间。它将最终的像素图像传递给保存图像节点，用于展示图像并下载。


默认工作流程是 ComfyUI 中能找到的最简单的工作流程。


## Masked content  蒙面内容

Masked content controls how the masked area is initialized.
遮罩内容控制遮罩区域的初始化方式。

Fill: Initialize with a highly blurred of the original image.
填充：用原始图像的高度模糊进行初始化。
Original: Unmodified.  原文：未修改。
Latent noise: Masked area initialized with fill and random noise is added to the latent space.
潜在噪声：用填充和随机噪声初始化的掩蔽区域被添加到潜在空间。
Latent nothing: Like latent noise except no noise is added to the latent space.
潜在无：类似于潜在噪声，但潜在空间中没有添加任何噪声。


## 下载模型

### Checkpoint

将 checkpoint 模型放置在文件夹 ComfyUI/models/checkpoints：


SDXL 1.0 base checkpoint: https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0/resolve/main/sd_xl_base_1.0.safetensors
SDXL 1.0 refiner checkpoint: https://huggingface.co/stabilityai/stable-diffusion-xl-refiner-1.0/resolve/main/sd_xl_refiner_1.0.safetensors


### VAE


将 VAE 放入文件夹 ComfyUI/models/vae：



Fixed SDXL 0.9 VAE: https://huggingface.co/madebyollin/sdxl-vae-fp16-fix/resolve/main/sdxl_vae.safetensors


### LoRA

将 LoRA 放入文件夹ComfyUI/models/loras


SDXL Offset Noise LoRA: https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0/resolve/main/sd_xl_offset_example-lora_1.0.safetensors


### Upscaler


Upscaler 可以放大您的图像，将升级器放入文件夹 ComfyUI/models/upscaler：


4x_NMKD-Siax_200k.pth Upscaler: https://huggingface.co/uwg/upscaler/resolve/main/ESRGAN/4x_NMKD-Siax_200k.pth
4x-Ultrasharp.pth Upscaler: https://huggingface.co/uwg/upscaler/resolve/main/ESRGAN/4x-UltraSharp.pth  


## 工作流  


ComfyUI 的一大优点是它可以轻松下载并在工作流程之间切换。

这是官方 ComfyUI 仓库中的示例工作流程列表： https://github.com/comfyanonymous/ComfyUI_examples



## prompt


### Style:  风格


Define the aesthetic direction, such as illustration style, painting medium, digital art style, or photography. Experiment and blend styles such as line art, watercolor, oil painting, surrealism, expressionism, and product photography.
明确审美方向，例如插画风格、绘画媒介、数字艺术风格或摄影。尝试并融合线条艺术、水彩画、油画、超现实主义、表现主义和产品摄影等风格。


### Subject and Action:  主题和行动


If your image has a subject, the prompt should be written to amplify its presence first and any actions the subject takes afterward. Consider the images and prompts below.
如果你的图片有主体，提示应该先强调其存在感，然后再描述主体随后发生的动作



### Composition and Framing:  构图和取景

Describe the desired composition and framing of the image by specifying close-up shots or wide-angle views.
通过指定特写镜头或广角视图来描述所需的图像构图和取景。


### Lighting and Color:  灯光和颜色：


Describe the lighting or shadows in the scene using terms like "backlight", "hard rim light", and "dynamic shadows".
使用“背光”、“硬边缘光”和“动态阴影”等术语描述场景中的照明或阴影。


### Technical Parameters:  技术参数


Specify technical parameters using cinematic terms to guide the desired perspective and framing. Terms like “bird’s eye view,” “close-up,” “crane shot,” and “wide-angle shot” can help direct the composition effectively.
使用电影术语指定技术参数，以指导所需的视角和取景。“鸟瞰图”、“特写”、“摇臂镜头”和“广角镜头”等术语有助于有效地指导构图。
 Consider using terms like “fish-eye lens” for a curved look to achieve unique visual effects.
考虑使用“鱼眼镜头”等术语来呈现弯曲的外观，从而实现独特的视觉效果。


### Text:  文本：


The SD3.5 models can incorporate text into images. To achieve the best results, enclose the text in “double quotes” and keep the desired words or phrases short.
SD3.5 型号支持将文本合并到图像中。为了获得最佳效果，请将文本括在“双引号”中，并保持所需的单词或短语简短。


### Negative Prompting:  负面提示：

Negative prompting allows precise control over colors and content. While the main prompt shapes the general image, negative prompts refine it by filtering out unwanted elements, textures, or hues, helping to achieve a focused, polished result.
负面提示可以精确控制颜色和内容。主提示塑造了整体形象，而负面提示则通过过滤掉不想要的元素、纹理或色调来完善形象，从而达到聚焦、精致的效果。
 This enables more control over the final image, ensuring that distractions are minimized and that the output aligns closely with your intended vision.
这样可以更好地控制最终图像，确保最大限度地减少干扰，并确保输出与您的预期视觉紧密一致。


## prompt 提示词的基本结构


### 主体描述（Subject）

定义图像的主要内容，如人物、动物、风景等。例子：a beautiful sunset over the mountains（一场美丽的山脉日落）

### 细节描述（Details）

增加对主体的详细描述，例如姿势、颜色、特征等。例子：golden lighting, vibrant colors, high resolution, ultra-detailed（金色光线，鲜艳色彩，高分辨率，超细节）

### 风格描述（Style）

控制图像的艺术风格，例如写实、动漫、油画等。例子：cinematic, cyberpunk, fantasy, 8K resolution（电影级，赛博朋克，幻想风，8K分辨率）


### 氛围和情绪（Mood & Atmosphere）

设定图像的整体氛围，如温暖、黑暗、梦幻等。例子：dramatic lighting, moody, serene（戏剧性光影，情绪化，宁静）


### 摄影/艺术相关（Camera & Art References）

通过相机参数或艺术流派描述拍摄方式。例子：soft focus, DSLR, film grain, Rembrandt style（柔焦，单反，胶片颗粒，伦勃朗风格）

## 编写提示词的常见技巧

### 从一般到具体

提示词的编写应遵循 “从整体到细节” 的原则，先描述大场景，再添加细节


### 使用逗号分隔

在 ComfyUI 中，提示词通常使用 逗号 , 分隔不同的描述元素，以提高解析清晰度


### 强调关键部分

使用括号 `()` 可以增加某个描述的权重，而 `[]` 则可以降低其权重


### 避免过度堆砌

虽然可以添加多个细节描述，但过多的提示词可能导致模型混淆，影响图像生成的质量。保持简洁清晰，通常 10-20 个关键字最佳。


### 提示词示例

主题：a beautiful woman

细节：blonde hair, blue eyes

风格：cinematic photography

质量：4K resolution, highly detailed


### Lora触发词


LoRA 触发词用于激活特定的 LoRA 微调权重，例如特定的绘画风格或人物特征

轻量级模型微调技术，允许用户在不重新训练整个模型的情况下，通过加载小型的额外权重来适配特定风格或对象


## 附录


动画教程: https://comfyanonymous.github.io/ComfyUI_tutorial_vn/


Stable Diffusion ComfyUI 入门介绍 https://blog.yanghong.dev/stable-diffusion-comfyui-introduction/

https://stability.ai/

https://stability.ai/learning-hub/stable-diffusion-3-5-prompt-guide
https://stable-diffusion-art.com/prompt-guide/
https://stable-diffusion-art.com/how-to-come-up-with-good-prompts-for-ai-image-generation/

https://stable-diffusion-art.com/how-stable-diffusion-work
https://stable-diffusion-art.com/comfyui/
https://stable-diffusion-art.com/beginners-guide/


## Next 

[Next](../03.SC-txt2img/readme.md)
