The aim is to develop a model to sugment objects in video and track them based language queries based on SAM2

Interesting bit:

In pursuit of efficiency, reducing the frame number would limit the perception of temporal dynamics while down-sampling frame features would lose visual details that are essential for dense prediction tasks exemplified by segmentation. Our intuition
is that adjacent frames in videos usually share similar visual contents and features. Therefore, we leverage this inherent temporal redundancy in videos and propose the Sparse Dense Sampling strategy. It uniformly samples a set of dense frames, preserving full-resolution features (dense tokens), and down-samples the remaining interleaved frames to lower resolution (sparse tokens). Dense tokens provide detailed visual information needed for accurate segmentation, while sparse tokens capture the temporal context, ensuring that the model remains aware of motion and changes over time.


![[Pasted image 20241018153545.png]]

