* Joint embedding prediction based framework
* Proposed as an alternative to using negative samples, reconstruction, etc as constrains to avoid collapse in the representation space
* Uses feature prediction the learning objective
* Uses a twin network with the second part being EMA updated from the og network
* Stop gradient is there for the EMA network similar to BYOL
* Prediction of the representation given the z which is information about the missing piece that is necessary for prediction is done
* Z is important as the prediction problem can have a large number of outcomes, giving a z constrains the search space for the features
* Masking is a stragegy generally shown to work in the paper