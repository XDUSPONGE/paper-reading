# paper-reading
## 2020.12.17
*IoU-balanced Loss Functions for Single-stage Object Detection*

还是针对的是目标检测中的loss的问题，argue的点一般one stage的目标检测算法是基于cls loss和loc loss做的，loc一般用的是smooth l1 loss，而cls一般用的是cross entropy loss，这两个loss之间缺少一定的interaction，这样就会导致如下的问题
* cls loss 会把高的IoU的给个低的cls score
* 会把低的IoU给个高的cls score

这就会损害location的精度，另外，标准的smooth l1 loss会由很差的loc的那种异常值主导，也会对location产生损害。于是作者为了解决以上的问题，就搞了一个IoU-balanced loc loss以及cls loss
* IoU balanced cls loss主要是对于那些有高的IoU值的positive样本赋予更多的权重
* IoU balanced loc loss主要是降低有低的IoU样本的gradient，提升有高的IoU样本的gradient

结合以上两者，在coco上有一个点的提升

