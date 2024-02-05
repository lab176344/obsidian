The You Only Look Once (YOLO) series of detectors
have established themselves as efficient and practical tools.
However, their reliance on predefined and trained object
categories limits their applicability in open scenarios.
Addressing this limitation, we introduce YOLO-World,
an innovative approach that enhances YOLO with openvocabulary
detection capabilities through vision-language
modeling and pre-training on large-scale datasets. Specifically,
we propose a new Re-parameterizable Vision-
Language Path Aggregation Network (RepVL-PAN) and
region-text contrastive loss to facilitate the interaction between
visual and linguistic information. Our method excels
in detecting a wide range of objects in a zero-shot manner
with high efficiency.


![[Pasted image 20240205133441.png]]
![[Pasted image 20240205133502.png]]
Method

YOLO-World follows the standard YOLO architecture [19] and leverages the pre-trained CLIP [36] text encoder to encode the input texts.

Uses GLIP and CLIP for generating image text pairs

Uses n-gram to filter out only the nouns from the prompts

For efficiency an offline vocabulary is constructed and used during inference

Contrastive, IoU and focal loss are used for training 



