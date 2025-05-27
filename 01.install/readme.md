# 安装 comfyUI 


## 安装 Mac PyTorch


参考文档： https://developer.apple.com/metal/pytorch/


```bash
conda install pytorch torchvision torchaudio -c pytorch-nightly
```

## 安装 comfyUI 


```
git clone https://github.com/comfyanonymous/ComfyUI

cd ComfyUI

conda create -n ComfyUI python=3.12
conda activate ComfyUI
pip install torch torchvision torchaudio

pip install -r requirements.txt

./python main.py --force-fp16  --force-upcast-attention
```

## 模型下载

模型聚合网站: https://upscale.wiki/w/index.php?title=Model_Database&oldid=1571


## Next 

[Next](../02.basics/readme.md)


## 参考

https://stable-diffusion-art.com/comfyui/
