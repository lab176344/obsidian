
Abstract
The CLIP and Segment Anything Model (SAM) are remarkable
vision foundation models (VFMs). SAM excels
in segmentation tasks across diverse domains, while
CLIP is renowned for its zero-shot recognition capabilities.
This paper presents an in-depth exploration of integrating
these two models into a unified framework. Specifically,
we introduce the Open-Vocabulary SAM, a SAM-inspired
model designed for simultaneous interactive segmentation
and recognition, leveraging two unique knowledge transfer
modules: SAM2CLIP and CLIP2SAM. The former adapts
SAM’s knowledge into the CLIP via distillation and learnable
transformer adapters, while the latter transfers CLIP
knowledge into SAM, enhancing its recognition capabilities.

![[Pasted image 20240117173610.png]]

Problem the paper is solving
First, the requirement for two independent backbones in the combined model increases computational costs(Prob.1). 

Second, SAM and CLI ParetrainedwithdistinctobjectivesSAMthroughsupervisedlearningandCLIPviacontrastive learning–andthereislimitedresearchonknowledgetransferbetweensuchdiversearchitectures(Prob.2).

Third, despite adapter integration, significant performance gaps remain in recognizing small objects(Prob.3).

Fourth, there is a lack of exploration into integrating open-vocabulary capabilities for SAM and CLIP, particularly in the context of feature fusion and data scaling

(Prob.4).Our work aims to solve these problems in a unified yet effective framework



There are three possibilities to do clip and SAM knowledge transfer

a,b,c

![[Pasted image 20240117173709.png]]This paper uses a CLIP2SAM and CLIP2SAM module using adapters. 

The FPN network based CLIP2SAM is mainly done to avoid small objects