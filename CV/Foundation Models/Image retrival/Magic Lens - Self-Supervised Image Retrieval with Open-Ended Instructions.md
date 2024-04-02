Magic lens is trained using a query image, instruction and target image dataset. The hypothesis behind that is an image search from web will also retrieve very close images. The relationship between the images can be extracted using captions, meta data and LLMs. 

The dataset mining is the main contribution. They also use CLIP to rank similar images and duplicates. The grouping logic after web search is not clearly explained but might be interesting.
Web data comes with alt data and cloud vision from GCP is used. Palma is used for captioning. 

![[Pasted image 20240402230056.png]]![[Pasted image 20240402230116.png]]![[Pasted image 20240402230142.png]]