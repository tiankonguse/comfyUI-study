# Upscale Model 

将  ESRGAN 等高级模型放入 models/upscale_models 文件夹，然后使用 UpscaleModelLoader 节点加载它们，并使用 ImageUpscaleWithModel 节点使用它们。


Upscale 模型下载地址： https://openmodeldb.info/


也可以从 从Upscaler Wiki下载一个 upscaler 模型
https://upscale.wiki/w/index.php?title=Model_Database&oldid=1571

## 简单的放大


[./upscale.json](./upscale.json)  


## 文生图后高清修复


文生图后，将生成的图片放大修复。


参考 [2 Pass Txt2Img (Hires fix) ](../09.2-pass-txt2img/readme.md)


##  SD Ultimate Upscale


生成图片后，将图片分割为如干小块，分别放大修复。  

[Ultimate_upscale.json](./Ultimate_upscale.json)
