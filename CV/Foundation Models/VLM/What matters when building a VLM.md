
The paper studies the imapct of all the design choices when building the VLM

The main findings are as follows:

(a) the progress of vision-language models is in large part driven by the progress of pre-trained unimodal backbones, 

(b) the more recent fully autoregressive architecture outperforms the cross-attention architecture, although it requires modifications to the optimization procedure to ensure a stable training,

(c) adaptation of the pre-trained vision backbone and the modules connecting the text and vision modalities allow for more efficiency at inference time on one side, and handling images in their original ratio and size without harming downstream performance on the other side, and 

(d) modifications to the image processing enables trading inference cost for downstream performance.


**Finding 1. For a fixed number of parameters, the quality of the language model backbone has a higher impact on the performance of the final VLM than the quality of the vision backbone.**


**Finding 2. The cross-attention architecture performs better than the fully autoregressive one when unimodal pre-trained backbones are kept frozen. However, when training the unimodal backbones, the fully autoregressive architecture outperforms the cross-attention one, even though the latter has more parameters.**

**Finding 3. Unfreezing the pre-trained backbones under the fully autoregressive architecture can lead to training divergences. Leveraging LoRA still adds expressivity to the training and stabilizes it.**


**Finding 4. Reducing the number of visual tokens with learned pooling significantly improves compute efficiency at training and inference while improving performance on downstream tasks.**

**Finding 5. Adapting a vision encoder pre-trained on fixed-size square images to preserve images’ original aspect ratio and resolution does not degrade performance while speeding up training and inference and reducing memory.**

**Finding 6. Splitting images into sub-images during training allow trading compute efficiency for more performance during inference. The increase in performance is particularly noticeable in tasks involving reading text in an image.** This is helping is benchmarks like DocVQA and TextVQA. This strategy is adopted during the fine-tuning stage