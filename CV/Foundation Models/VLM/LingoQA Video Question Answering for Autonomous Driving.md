
The introduction part of paper outlines the importance of establishing trust between users and autonomous driving agents through communication, specifically highlighting the role of textual justifications in enhancing user confidence. The authors propose integrating Vision-Language Models (VLMs) into autonomous driving to achieve this trust.

The paper’s main contributions are:

- A novel dataset
- A novel evaluation metric (Lingo-Judge)
- A baseline vision-language model

Each contribution will be explained in more details.

# **A novel dataset**

The total dataset consists of 419.9k question-answer (QA) pairs, with each sample featuring a 4-second video clip at a 1Hz frame rate. It significantly surpasses the size of prior datasets like BDD-X in terms of scenarios and annotations.

The dataset covers a wide range of competencies critical for autonomous driving, including action (what the vehicle is doing), justification (why the action is taken), attention(what should be paid attention to in the current situation), identification(identifying an object given its description), localization, description, counting, anticipation, and reasoning with counterfactuals.

The questions span a diverse set of objects such as pedestrians, vehicles, cyclists, and road infrastructure, enhancing the realism and applicability of the dataset to real-world driving scenarios.

![](https://miro.medium.com/v2/resize:fit:1400/1*LF_-1CSmsd9wr5jB8ApaFg.png)

Dataset Statistics (source Lingo paper)

The labeled training dataset consists of two complementary parts: the **action dataset** and the **scenery dataset**.

**Action Dataset**:

- **Purpose**: Focuses on driving behaviors and interesting events requiring action changes (e.g., decelerations, accelerations, lane changes).
- **Content:** Includes labeled data by driving operators with very short high-level descriptions of the situations and behavioral policies (e.g. “following lane, pedestrian on a zebra crossing, should stop) and metadata from perception systems (e.g., traffic light presence, vehicle and pedestrian detectors) and other metadata (speed, steering wheel position, and road type from the map data).
- **Creation Method:** Utilized GPT-3.5 to rephrase and extend questions based on event descriptions and metadata, leading to 24,577 video snippets with 167,774 QA pairs.

**Scenery Dataset:**

- **Purpose:** Complements the action dataset by concentrating on perception-related questions and additional driving behaviors.
- **Creation Method:** Involves detailed and dense labeling of three 30-minute driving sessions, categorizing observations into various aspects like driver’s actions, vehicle descriptions, and environmental observations.
- **Utilization of GPT-4:** For generating diverse questions and answers, specifically targeting perception questions to enrich dataset diversity, resulting in approximately 43 QA pairs per video.

**Evaluation Dataset:**

- **Design:** A smaller, low-density dataset from in-house human labelers, creating both the questions and the answers associated with the short videos. It used for evaluating models on a broad spectrum of competencies relevant to autonomous driving, such as action, justification and perception.
- **Annotation Process:** Involved multiple human evaluators to ensure diversity and quality in the answers, resulting in 1k high-quality answers for 500 questions.

# A novel evaluation metric — Lingo-Judge:

- **Development:** Inspired by TruthfulQA GPT-Judge, Lingo-Judge is a text classifier designed to estimate the correctness of model answers based solely on textual responses, without video input. Lingo-Judge assesses answers by considering all possible combinations of the model’s predicted answers and the correct ground truth answers for each question. The highest correctness estimate from these combinations is taken as the score (S) for that particular sample.

![](https://miro.medium.com/v2/resize:fit:902/1*HYws969yhgt5sbPqJB9n1A.png)

Maximum correctness estimate (source Lingo Paper)

- **Architecture:** Utilizes a DeBERTa-V3 language model fine-tuned with LoRA, predicting correctness with a linear head on the output token.
- **Performance:** Achieves high correlation coefficients (Spearman and Pearson) with human ratings, demonstrating its efficacy in reflecting human judgment.
- The datasets and evaluation tools were released publicly to encourage community engagement and further advancement in the field.

# **A baseline vision-language model**

- **Model Name:** LingoQA Baseline.
- **Base Model:** Built on Vicuna v1.5, which has 7 billion parameters, designed to answer reasoning questions grounded in video outputs.