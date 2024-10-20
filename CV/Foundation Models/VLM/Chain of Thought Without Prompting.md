
Objective is to find if LLMs/VLMs can do reasoning without explicit prompting


CoT reasoning paths can be elicited from pre-trained LLMs by simply altering the
decoding process. Rather than conventional greedy decoding, we investigate the top-𝑘 alternative tokens, uncovering that CoT paths are frequently inherent in these sequences

![[Pasted image 20241018132946.png]]


This observation aligns with findings in (Cobbe et al., 2021a; Kojimaet al., 2022; Nye et al., 2021; Wei et al., 2022), which show that direct-answer prompts generally result in low accuracy on reasoning tasks even for large language models.![[Pasted image 20241018141050.png]]


Interestingly, upon examining the model's logits, we found that the presence of a CoT path typically leads to a more confident decoding of the final answer, characterized by a significant probability disparity between the top and secondary tokens:


Here x, and x? represent the top two tokens at the t-th decoding step in the k-th decoding path, chosen for their maximum post-softmax probabilities from the vocabulary, given x, being part of the answer tokens. This uncertainty measure is similar to the minimum-margin approach in (Jiang and Gupta,2019) and in our case, the model's overall confidence in decoding the final answer is approximated by averaging these probability differences for all relevant answer tokens xt. For example, for the GSM8K question in Table 1, given the answer "60".  we average the probability differences for all tokens in that answer, i.e., "6" and "0" ?


https://github.com/codelion/optillm/blob/main/optillm/cot_decoding.py#L14