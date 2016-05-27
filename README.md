# MeshMaterialCombine
很多时候我们需要把具有相同shader的材质球合并，从而减少drawcall的产生。  
比如九龙战里面，一个人物带有10个部位，10个部位各自来自不同的fbx文件，加上身体，就有11个材质球，占上11个drawcall。如果主城里面跑着10个角色，光人物就占了110个drawcall！所以这种时候材质球合并是必须的。

材质球合并，分以下几步走，首先我们讨论普通的MeshRenderer的材质球合并，然后再讨论SkinnedMeshRenderer的材质球合并。
普通的MeshRenderer的材质球合并：
1.合并所有材质球所携带的贴图，新建一个材质球，并把合并好的贴图赋予新的材质球。
2.记录下每个被合并的贴图所处于新贴图的Rect，用一个Rect[]数组存下来。
3.合并网格，并把需要合并的各个网格的uv，根据第2步得到的Rect[]刷一遍。
4.把新的材质球赋予合并好的网格，此时就只占有1个drawcall了。

详情请转移到博客：http://blog.csdn.net/dardgen2015/article/details/51517860
