# 文本生成图片  


文本转图像 (txt2img) 是指使用 AI 模型将文本输入生成图像。


模型：潜在空间中的噪声预测模型。
CLIP：语言模型对正向和反向提示进行预处理。
VAE：VAE在像素和潜在空间之间转换图像。
潜在图像的大小与像素空间中的实际图像成正比。


## 影响图片的因素

 
Checkpoint model: 稳定扩散模型对风格有显著的影响。
Prompt:  描述您希望在图像中看到的内容的文本输入
Negative prompt: 描述您不想看到的内容的文本输入。
Image Size: 图像大小应与 Checkpoint 模型匹配。对于 v1 模型，VAE 的大小为 512×512；对于 SDXL 模型，VAE 的大小为 1024×1024。
Sampler_name：在这里，您可以设置采样算法。
Sampling steps: 离散化去噪处理的步数。值越高，去噪过程越准确，质量也就越高。至少设置为 20。
CFG scale: 无分类器指导量表控制提示的遵循程度。
调度程序 (scheduler)：控制噪声水平在每个步骤中如何变化。
去噪 (denoise)：去噪过程应消除多少初始噪声。1 表示全部。

| Aspect ratio 长宽比|  	v1 models  v1 模型 |  	SDXL models  SDXL 模型| 
|:-:|:-:|:-:|
| 1:1| 	512×512	| 1024×1024 | 
| 3:2	| 768×512	| 1216×832  | 
| 16:9| 	910×512	| 1344×768 | 


## 风格

Anime style  动漫风格
Photorealistic style  写实风格
Landscape  景观
Fantasy  幻想
Artistic style  艺术风格
Animals  动物


## 工作流


[text2img.json](./text2img.json)


## prompt


### 姜饼屋


ptompt: gingerbread house, diorama, in focus, white background, toast , crunch cereal


## 参考

https://stable-diffusion-art.com/text-to-image/

