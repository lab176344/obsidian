Abstract

Contrastive Language-Image Pre-training (CLIP) plays an essential role in extracting valuable content information from images across diverse tasks. It aligns textual and vi- sual modalities to comprehend the entire image, including all the details, even those irrelevant to specific tasks. How- ever, for a finer understanding and controlled editing of im- ages, it becomes crucial to focus on specific regions of in- terest, which can be indicated as points, masks, or boxes, by humans or perception models. To fulfill the requirements, we introduce Alpha-CLIP, an enhanced version of CLIP with an auxiliary alpha channel to suggest attentive regions and fine-tuned with constructed millions of RGBA region-text pairs. Alpha-CLIP not only preserves the visual recognition ability of CLIP but also enables precise control over the emphasis of image contents. It demonstrates effec- tiveness in various tasks, including but not limited to open- world recognition, multimodal large language models, and conditional 2D / 3D generation. It has a strong potential to serve as a versatile tool for image-related tasks.


![[Pasted image 20240621141058.png]]

Additional to the CLIP contrastive loss, the paper introduces an alpha channel combined with the images with an attention block to contrast with the text features using NCE loss

The data for the alpha channel training is generated using a data pipeline using SAM, CLIP and BLIP captioning methods

ALpha CLIP is shown to be a good backbone for image recognition, VQA, 2D and 3D generation tasks