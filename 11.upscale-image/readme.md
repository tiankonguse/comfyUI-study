# Upscale Image

将  ESRGAN 等高级模型放入 models/upscale_models 文件夹，然后使用 UpscaleModelLoader 节点加载它们，并使用 ImageUpscaleWithModel 节点使用它们。


Upscale 模型下载地址： https://openmodeldb.info/


也可以从 从Upscaler Wiki下载一个 upscaler 模型
https://upscale.wiki/w/index.php?title=Model_Database&oldid=1571

## 原理


Upscale pixel：将可视的图直接 upscale。如果拿 ComfyUI 节点解释，这个节点输入的是 image，输出的是 upscale 后的 image。
Upscale latent：另一种是将不可视的潜空间图像 upscale，如果拿 ComfyUI 节点解释，这个节点输入的是 latent 输出的是 upscale 后的 latent，最后需要经过 decode 才能变成可视的图片。


## 常见算法

双三次插值算法：它通过使用周围像素的数值来模拟新像素的值，从而填充缺失的像素信息。这种方法看起来比较自然，但放大后的图像可能会显得模糊，因为算法在像素化和平滑之间寻求一种折中。

Lanczos 插值算法：它是一种更高级的算法，它试图保留图像中的边缘和纹理，但它们通常缺乏通用性，难以处理不同类型的图像。

基于神经网络训练后的模型：它则是一种新兴的 Upscale 方法，它利用深度学习技术，通过训练神经网络来理解图像的纹理和对象，从而在放大图像时生成更加真实和富有细节的图像。


| 选项名                    | 算法类型                   | 优缺点                             | 适用场景           |
| ---------------------- | ---------------------- | ------------------------------- | -------------- |
| `nearest`              | 最近邻插值                  | ✅ 速度最快<br>❌ 锯齿严重，图像块状感强         | 像素画、复古游戏风格图像   |
| `bilinear`             | 双线性插值                  | ✅ 平滑，速度快<br>❌ 模糊，细节丢失           | 快速预览、实时图像处理    |
| `bicubic`              | 双三次插值                  | ✅ 比 bilinear 更清晰<br>❌ 有轻微模糊     | 通用图像放大，质量中等    |
| `lanczos`              | Lanczos 插值             | ✅ 保留细节好，锐利<br>❌ 运算稍慢，有振铃效应      | 高清图像放大，追求质量    |
| `area`                 | 像素区域平均                 | ✅ 缩小时最优，保细节<br>❌ 不适合放大，放大模糊     | 缩图、图像下采样       |
| `ESRGAN`               | GAN 超分辨率               | ✅ 清晰、锐利，适合艺术图像<br>❌ 偶尔过度锐化或产生伪影 | 艺术图、动漫图像放大     |
| `Real-ESRGAN`          | GAN 超分辨率（实景优化）         | ✅ 适合真实照片，抗噪<br>❌ 速度较慢           | 高清照片放大，人像、自然图像 |
| `Latent Upscaler`      | Stable Diffusion 潜空间放大 | ✅ 生成式放大，可修图美化<br>❌ 有风格变化，不保真    | AI 图像再创作、艺术化放大 |
| `SwinIR`               | Transformer 超分模型       | ✅ 清晰自然、细节强<br>❌ 对低质量输入恢复有限      | 高质量自然图像超分，通用放大 |
| `R-ESRGAN 4x+`         | 实用 GAN 模型              | ✅ 良好细节恢复，适合多类型图像<br>❌ 可能锐化过头    | 写实风格图像、通用照片    |
| `R-ESRGAN 4x+ Anime6B` | 动漫优化版 GAN 模型           | ✅ 二次元图效果好，细节强<br>❌ 不适合实景图       | 动漫、插画图像放大      |
| `Bsrgan`               | 超分 GAN 模型              | ✅ 高质量图像恢复<br>❌ 稍慢               | 高分辨率自然图恢复      |
| `UltraMix Balanced`    | 多模型融合                  | ✅ 效果平衡，适配性强<br>❌ 模型较大，速度中等      | 通用图像放大，质量和速度折中 |



## 简单的放大


[./upscale.json](./upscale.json)  


## 文生图后高清修复


文生图后，将生成的图片放大修复。


参考 [2 Pass Txt2Img (Hires fix) ](../09.2-pass-txt2img/readme.md)


##  SD Ultimate Upscale


生成图片后，将图片分割为如干小块，分别放大修复。  

[Ultimate_upscale.json](./Ultimate_upscale.json)

