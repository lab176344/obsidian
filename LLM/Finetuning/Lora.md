![[Pasted image 20240124232620.png]]


For instance, whereas in regular finetuning, we compute the weight updates of a weight matrix _**W**_ as **_ΔW_**, in LoRA, we approximate **_ΔW_** through the matrix multiplication of two smaller matrices AB, as illustrated in the figure below. (If you are familiar with PCA or SVD, consider this as decomposing **_ΔW_** into **_A_** and **_B_**.)



Refernce

https://lightning.ai/lightning-ai/studios/code-lora-from-scratch