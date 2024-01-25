![[Pasted image 20240121172941.png]]


Taking a look at the architecture, the authors firstly do contrastive pre-training of a vision and a text encoder (just like CLIP). They take that model, remove the final pooling layer and attach a lightweight classification and box detection head and fine-tune.

During fine-tuning for object detection, they calculate the loss over bipartite matches. Simply put, loss is calculated over the predicted objects against ground truth objects and the goal is to find a perfect match of these two sets where each object is matched to one object in ground truth.

![[Pasted image 20240125224614.png]]
Code: 
https://colab.research.google.com/drive/10dAutMbC1ewRqgS3hqDyjOWOsJAv08E6?usp=sharing