# Reference-only ControlNet workflow  


## 简介

你在实际工作中可能还会遇这样的情况：你的客户给了一些参考图给你，让你参考这些图来设计某样东西，比如 logo。  
那么在这种情况下，除了直接让 AI 生成外，你还可以拿这些参考图来让 AI 生成新的 logo。


## 依赖

ComfyUI_experiments Node: https://github.com/comfyanonymous/ComfyUI_experiments


## ReferenceOnlySimple 节点

只需要在原有的 ControlNet workflow 中，将 Empty Latent Image 替换为一个参考图片。  


首先双击空白处，搜索 Reference 即可看到 ReferenceOnlySimple 的节点，添加该节点，并将与 Ksampler 连接起来。  
因为这个节点仅支持导入 latent，所以你还需要使用 VAE Encode 将图片转成 latent



## 工作流

[](./controlnet-canny-reference.json)  


## 效果


![](./canny-reference-001.png)  






## 参考

https://www.comflowy.com/zh-CN/expert/controlnet-advanced#reference-only-controlnet-workflow
https://www.comflowy.com/zh-CN/blog/generate-app-logo
