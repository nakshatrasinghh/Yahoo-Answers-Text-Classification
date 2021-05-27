# Yahoo-Answers-Text-Classification
Text Classification using ULMFiT and BERT. Challenge solved for ML Fellowship program @Fellowship.ai

# ULMFiT
1. Language Model
- 1. AWD-LSTM - Architecture 
- 2. 0.3 - Dropout
- 3. 1e-2 -Learning Rate (One cycle policy with **2 epochs**, to avoid overfitting)
- 4. 1e-3 -Learning Rate (Unfreezing all layers)
2. Classification Model **`{To train the classifier, we will use a technique called gradual unfreezing. We can start by training the last few layers, then go backwards and unfreeze and train layers before. We can use the learner function learn.freeze_to(-2) to unfreeze the last 2 layers.}`**
- 1. AWD-LSTM - Architecture
- 2. 0.5 - Dropout
- 3. 1e-2 -Learning Rate(One cycle policy with **2 epochs**, to avoid overfitting)
- 4. 1. (5e-3, 2e-3) -Slice Learning Rate(Unfreeze last 2 layers) **`{Applying different lr for different groups is a technique called “discriminative layer training”}`**
- 4. 2. (0.8, 0,7) -Momentum **`{0.8 to 0.7 during the warmup then from 0.85 to 0.95 in the annealing}`**
- 5. 1. (2e-3/100, 2e-3) -Slice Learning Rate(Unfreeze all the layers)
- 5. 2. (0.8, 0,7) -Momentum
- 6. 64 -Batch Size

### How to improve performance (ULMFiT)?
1. Provide more data to ULTFiT language model (requires more computational resources)
2. Hyperparameter tuning using bayesian techniques (for language model and classification model)
3. Reduce dropout in language model (may lead to overfitting, so need to be careful)

# BERT
- 64 -Max Length
- 64 -Batch Size
- 2e-5 -Learning Rate
- 3 -Epochs

### How to improve performance (BERT)?
1. Increase max length parameter (requires more computational resources)
2. Reduce batch size (more execution time, may lead to overfitting)
3. Use regulazation techniques (L1 and L2) 

# RESULTS

\# | Model | Accuracy | Loss | Total Time
--- | --- | --- | --- | --- 
01 | ULMFiT | 0.753679 | 0.702299 | 11:06
02 | BERT | 0.8193 | 0.5698 | 13:06 
