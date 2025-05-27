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
