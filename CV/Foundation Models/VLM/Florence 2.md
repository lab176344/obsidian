
Abstract:
We introduce Florence-2, a novel vision foundation model with a unified, prompt-based representation for a va- riety of computer vision and vision-language tasks. While existing large vision models excel in transfer learning, they struggle to perform a diversity of tasks with simple in- structions, a capability that implies handling the complex- ity of various spatial hierarchy and semantic granularity. Florence-2 was designed to take text-prompt as task instruc- tions and generate desirable results in text forms, whether it be captioning, object detection, grounding or segmen- tation. This multi-task learning setup demands large- scale, high-quality annotated data. To this end, we co- developed FLD-5B that consists of 5.4 billion comprehen- sive visual annotations on 126 million images, using an it- erative strategy of automated image annotation and model refinement. We adopted a sequence-to-sequence structure to train Florence-2 to perform versatile and comprehensive vi- sion tasks. Extensive evaluations on numerous tasks demon- strated Florence-2 to be a strong vision foundation model contender with unprecedented zero-shot and fine-tuning capabilities.

It uses a DaViT vision encoder to convert images into visual embeddings, and BERT to convert text prompts into text and location embeddings.

The pretraining cannot rely on single task this makes the model to constrain itself and cannot get the necessary spatial hierarchy and spatial granularity 

Image understanding necessitates capturing multiple levels of granularity, from global semantics to local details, and comprehending spatial relationships between objects and entities in their semantic context. To address these core aspects of image understanding, our approach incorporates a diverse set of annotations, effectively capturing visual un- derstanding nuances and bridging the gap between vision and language understanding.

The method focuses on three main diverse tasks

1. Image-level understanding
2. Pixel/Region recognition
3. Fine grained visual semantic alignment  
![[Pasted image 20240625095614.png]]The data annotation process is designed to support multitask learning through three categories of annotations: text, region-text pairs, and text-phrase-region triplets. This process involves three phases:

1. **Initial Annotation with Specialist Models**: Synthetic labels are generated using a combination of offline models and online cloud services, tailored to specific annotation types. Existing partial annotations in datasets like Object 365 are merged with synthetic labels to enhance coverage. Some annotations, particularly detailed text descriptions, are deferred to a later refinement phase due to the challenges in obtaining high-performance models for them initially.
    
2. **Data Filtering and Enhancement**: To address noise and imprecision in the initial annotations, a filtering process is employed. For textual annotations, a parsing tool based on SpaCy is used to extract and retain texts with a certain complexity, removing those with excessive objects. For region annotations, noisy bounding boxes are removed based on a confidence score threshold and non-maximum suppression is applied to reduce redundancy.
    
3. **Iterative Data Refinement**: A multitask model is trained on the filtered initial annotations and its predictions are evaluated. Enhanced annotations from this model are integrated back into the dataset, and the model is retrained in a cyclical process to incrementally improve data quality. For tasks initially skipped due to insufficient data, the iteratively refined model is used for pre-training, followed by fine-tuning with sparse datasets, resulting in superior performance. This process ensures comprehensive annotation coverage across the 126 million images in the dataset.
https://huggingface.co/blog/finetune-florence2