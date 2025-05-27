# 模型


## Base models  基础模型


基础模型是使用数十亿张不同主题和风格的图像训练的 AI 图像模型。
创建这些模型需要投入大量资金和专业知识，而且数量有限。

最受欢迎的基础模型是：

Stable Diffusion v1.5  稳定扩散 v1.5
Stable Diffusion XL  稳定扩散 XL
Flux.1 dev  Flux.1 开发

## Stable diffusion v1.5  稳定扩散 v1.5


下载地址: https://huggingface.co/stable-diffusion-v1-5/stable-diffusion-v1-5/blob/main/v1-5-pruned-emaonly.safetensors


Stability AI 的合作伙伴 Runway ML 于 2022 年 10 月发布了 Stable Diffusion 1.5。
Stable Diffusion v1.5 是一个通用模型，默认图像大小为 512×512 像素。

## Stable Diffusion XL  稳定扩散 XL


SDXL 模型是对著名的 v1.5 和被遗忘的 v2 模型的升级。

The improvements of SDXL base model are
SDXL 基础模型的改进包括

Higher native resolution – 1024×1024 pixels compared to 512×512 pixels for v1.5
更高的原始分辨率 – 1024×1024 像素，而 v1.5 版本为 512×512 像素
Higher image quality (compared to the v1.5 base model)
更高的图像质量（与 v1.5 基础模型相比）
Capable of generating legible text
能够生成清晰的文本
It is easy to create darker images
很容易创建较暗的图像


## Flux.1 dev  Flux.1 开发


The Flux AI model was released by the Black Forest Labs, where many researchers were the original creators of Stable Diffusion 1.5.
Flux AI 模型由黑森林实验室发布，该实验室的许多研究人员都是 Stable Diffusion 1.5 的原始创建者。


The improvements of the Flux AI base model are:
Flux AI 基础模型的改进包括：

Legible text generation  生成清晰的文本
Excellent realistic images 出色的逼真图像
Excellent prompt adherence 出色的快速依从性


The default image size of Flux.1 dev is 1024×1024 pixels.
Flux.1 dev 的默认图像大小为 1024×1024 像素。


## Fine-tuned models  微调模型

### What is fine-tuning?  什么是微调？

Fine-tuning is a common technique in machine learning. It involves taking a base model and training it more on a narrow dataset.
微调是机器学习中的一种常见技术。它涉及采用基础模型并在较窄的数据集上对其进行更多训练。

A fine-tuned model generates images similar to those used in the training. For example, the Anything v3 model is trained with anime images. So, it creates anime-style images by default.
经过微调的模型会生成与训练中使用的图像类似的图像。例如，Anything v3 模型是使用动漫图像进行训练的。因此，它默认会创建动漫风格的图像。


Realistic Vision: Realistic photo style.
逼真的视觉：逼真的照片风格。
Anything v3: Anime style.
任何东西 v3：动漫风格。
Dreamshaper: Realistic painting style.
梦想塑造者：现实主义的绘画风格。


Using a model is an easy way to achieve a particular style.
使用模型是实现特定风格的一种简单方法。



## Popular Stable Diffusion Models 流行的稳定扩散模型


### Realistic Vision  现实愿景

Base Model: Stable Diffusion 1.5 基础模型：稳定扩散 1.5
模型下载地址: https://civitai.com/api/download/models/29460
Realistic Vision v5 适合生成任何逼真的东西，无论是人物、物体还是场景。

### DreamShaper  梦想塑造者

Base model: Stable Diffusion 1.5 基础模型：稳定扩散 1.5
模型下载地址: https://civitai.com/models/4384/dreamshaper

Dreamshaper 模型经过精心调校，打造出一种将照片级写实元素与计算机图形相结合的肖像插画风格。


### Juggernaut XL  巨无霸 XL

Base model: Stable Diffusion XL 基础模型：稳定扩散 XL
下载地址: https://civitai.com/models/133005/


Juggernaut XL 模型是一款经过精心调优的 SDXL 模型，尤其擅长生成逼真风格的照片。此外，它还使用了多样化的高质量图像进行训练，以创建各种风格。它是 SDXL 基础模型的良好替代品。


### Pony Diffusion  小马扩散


Base model: Stable Diffusion XL 基础模型：稳定扩散 XL
下载地址: https://civitai.com/models/257749/pony-diffusion-v6-xl


Pony Diffusion 是一个 SDXL 模型，使用大量动漫和卡通风格的图像进行训练。它是生成非现实内容的首选模型。该模型极具创造力，并且能够很好地遵循提示。


### Anything V3  任何东西 V3


Base model: Stable Diffusion 1.5 基础模型：稳定扩散 1.5

下载地址: https://huggingface.co/Linaqruf/anything-v3.0


Anything V3 是一款经过训练的专用模型，用于生成高质量的动漫风格图像。您可以在文本提示中使用 danbooru 标签（例如 1girl 、white hair）。


### Deliberate v2  故意 v2

Base model: Stable Diffusion 1.5 基础模型：稳定扩散 1.5
下载地址： https://huggingface.co/XpucT/Deliberate/blob/main/Deliberate_v2.safetensors


Deliberate v2 是另一个必备模型（太多了！），它可以渲染逼真的插图。效果可能会出乎意料地好。每当你遇到好的提示时，就切换到这个模型，看看会得到什么！


### F222

Base model: Stable Diffusion 1.5 基础模型：稳定扩散 1.5


下载地址: https://huggingface.co/acheong08/f222/blob/main/f222.ckpt

F222 最初被训练用于生成裸体照片，但人们发现它有助于生成具有正确身体部位关系的精美女性肖像。与你想象的相反，它在生成美观的服装方面相当出色。

F222 适合肖像画。它容易产生裸体。在题目中可以添加一些服装相关的词语，例如“连衣裙”和“牛仔裤”。


### ChilloutMix

Base model: Stable Diffusion 1.5 基础模型：稳定扩散 1.5


下载地址： https://civitai.com/models/6424/chilloutmix


ChilloutMix 是一款用于生成照片级亚洲女性模型的特殊模型。它类似于 F222 的亚洲版本。与韩语嵌入 ulzzang-6500-v1 配合使用，可以创建韩流女孩。

与 F222 类似，它有时会生成裸照。请在提示中使用“连衣裙”和“牛仔裤”等服装术语，并在否定提示中使用“裸体”来抑制它们。


### Protogen v2.2 (Anime)  Protogen v2.2（动漫）


Base model: Stable Diffusion 1.5 基础模型：稳定扩散 1.5


下载地址：https://civitai.com/api/download/models/4007


Protogen v2.2 非常出色。它能生成赏心悦目的插图和动漫风格的图像。


### GhostMix


Base model: Stable Diffusion 1.5
基础模型：稳定扩散 1.5


下载地址：https://civitai.com/api/download/models/59685


GhostMix 采用 90 年代经典动漫《攻壳机动队》的风格进行训练。您会发现它对于生成半机械人和机器人非常有用。


### Waifu-diffusion



Base model: Stable Diffusion 1.5
基础模型：稳定扩散 1.5

Download link  下载链接 https://huggingface.co/hakurei/waifu-diffusion

Waifu Diffusion is a Japanese anime style.
Waifu Diffusion 是一种日本动漫风格。


### Inkpunk Diffusion  墨水朋克的传播


Base model: Stable Diffusion 1.5
基础模型：稳定扩散 1.5

Model Page  模型页面 https://huggingface.co/Envvi/Inkpunk-Diffusion

Download link  下载链接 https://huggingface.co/Envvi/Inkpunk-Diffusion/blob/main/inkpunk-diffusion-v1.ckpt 

Inkpunk Diffusion is a Dreambooth-trained model with a very distinct illustration style.
Inkpunk Diffusion 是一个经过 Dreambooth 训练的模特，具有非常独特的插画风格。

Use keyword: nvinkpunk  使用关键字：nvinkpunk


## CLIP Skip  跳过片段


某些型号推荐使用不同的“片段跳过”设置。


CLIP Skip 是一项功能，可在 Stable Diffusion 的图像生成过程中跳过 CLIP 文本嵌入网络中的多个最后层。CLIP 是 Stable Diffusion v1.5 模型中使用的语言模型。它将提示中的文本标记转换为嵌入。它是一个包含多层的深度神经网络模型。CLIP Skip 指的是需要跳过的最后层数。


为什么要跳过一些 CLIP 层？神经网络在层层传递过程中会总结信息。越早的层，包含的信息就越丰富。


跳过 CLIP 层会对图像产生显著影响。许多动漫模型都是使用 CLIP Skip 为 2 进行训练的。


## Stable Diffusions model file formats 稳定扩散模型文件格式


### Pruned vs Full vs EMA-only models

一些稳定扩散检查点模型由两组权重组成：（1）最后一个训练步骤后的权重和（2）最后几个训练步骤的平均权重，称为 EMA（指数移动平均值）。

如果您想通过额外的训练来微调模型，那么您只需要完整的模型（即由两组权重组成的检查点文件）。
如果您想使用它来生成图像，请下载精简版或仅支持 EMA 的模型。这可以节省一些磁盘空间。相信我，您的硬盘很快就会被占满！


### Fp16 and fp32 models

FP 代表浮点数。它是计算机存储十进制数的方式。这里的十进制数是模型权重。FP16 每个数占用 16 位，称为半精度。FP32 每个数占用 32 位，称为全精度。


深度学习模型（例如稳定扩散）的训练数据噪声很大。你很少需要全精度模型。额外的精度只会存储噪声！


以，如果有的话，请下载 FP16 模型。它们大约只有原来的一半大小。这能帮你节省几 GB 的空间！


### Safetensor models


原始的 PyTorch 模型格式为 .pt 。这种格式的缺点是不安全的。有人可能会在其中打包恶意代码。当你使用该模型时，这些代码可能会在你的机器上运行。


Safetensors 是 PT 模型格式的改进版本。它的作用与存储权重相同，但不会执行任何代码。
因此，请尽快下载 safetensors 版本。如果没有，请从可靠的来源下载 PT 文件。


## Other model types


Checkpoint models： 检查点模型是真正的稳定扩散模型。它们包含生成图像所需的所有内容，无需任何额外文件。它们很大，通常为 2 到 7 GB。


Textual inversions (also called embeddings)： 文本反转（也称为嵌入）是定义新关键词以生成新对象或样式的小文件。它们很小，通常为 10 到 100 KB。您必须将它们与检查点模型一起使用。


LoRA models ：LoRA 模型是用于修改样式的检查点模型的小型补丁文件。它们通常大小为 10-200 MB。您必须将它们与检查点模型一起使用。


Hypernetworks ： 超网络是添加到检查点模型的附加网络模块。它们通常大小为 5 到 300 MB。您必须将它们与检查点模型一起使用。




## 参考

https://stable-diffusion-art.com/models/