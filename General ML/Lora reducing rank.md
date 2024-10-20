
Lora enables training adapters, the low in the lora stands for the lora weights being low rank. But the low rank depends on the size of the model. If it is required to have large models with many adapters the memory with relatively low rank might be high. Reducing the rank of existing lora adapters might be beneficial to solve
1. Memory requirements issues
2. Use of torch.compile which requres are adapters to be of same rank to avoid re compilation


Two options are available:
1. Random projections
2. SVD

Upsampling is also possible

https://huggingface.co/sayakpaul/flux-lora-resizing