* Extends [[JEPA]] to videos
* Use a VQ VAE like network taking two frames at a time to convert the video into space and time patches
* Some of the patches are masked
* The masked patches are the target for prediction
* Network is shown to have good features learning ability for downstream task like classification, action recognition, etc
* Evaluation of masking with diffusion is interesting 