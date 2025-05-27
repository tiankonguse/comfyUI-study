# 嵌入（embeddings）


要在 ComfyUI 中使用嵌入（embedding，也称为文本反转），请在正向或反向提示框中输入 embedding: 。


要使用嵌入，请将文件放入 models/embeddings 文件夹中，然后在提示中使用它。  


```
embedding：BadDream
```


请注意，您可以省略文件扩展名，因此这两个是等效的：


```
embedding:SDA768.pt
embedding:SDA768
```

由于嵌入只是关键字，因此您可以以类似的方式将关键字权重应用于嵌入。
这会使嵌入权重增加 20%。

```
(embedding: BadDream:1.2)
```




## 嵌入自动完成功能


但查找文件名需要做很多工作。相反，您可以通过安装ComfyUI-Custom-Scripts自定义节点来启用嵌入名称的自动完成功能。
输入提示后embedding:，将出现可用嵌入的列表。选择您要使用的嵌入。




## 参考

https://comfyanonymous.github.io/ComfyUI_examples/textual_inversion_embeddings/
