# Project Plan

- Stage 1, Setup and Preparation: (Week 1-5, Deadline: 20.02.)
  - Create a project plan. (Deadline: 13.02.)
  - Create a working environment. 
  - Train a downstream ML model, representative of a defined subset of industry-relevant tasks,
  on uncompressed data to quantify loss in predictive utility.
    - => What downstream tasks? Goal: Find and define an anomaly task (which data/ columns/ ... to use) and build a small RNN model as baseline.
    - Anomaly Detection or Fuel Consumption is probably good. We need to wait for feedback from Szabolcs here.
  - Implement a baseline model based on established neural compression frameworks such as https://www.sciencedirect.com/science/article/pii/S1568494623008153.
    Why we use the TCN–RNN Autoencoder as a baseline:
    
    We include the TCN–RNN autoencoder as a representative of state-of-the-art continuous-latent neural time-series compression. Compared to vanilla autoencoders, TCN–RNN architectures are explicitly designed for long temporal dependencies and have demonstrated stronger rate–distortion performance in recent peer-reviewed work. As such, they provide a stronger and more relevant continuous-compression baseline than simpler LSTM- or CNN-based autoencoders, and allow us to evaluate our tokenizer-based approach against a competitive neural compressor rather than a toy model.
    
    ⸻
    
    How we measure “model weight”:
    
    Rather than using the term “heavyweight” informally, we operationalize it via explicit efficiency metrics, measured under identical input lengths and hardware conditions:
    	•	Parameter count: total number of trainable parameters
    	•	Computational cost: FLOPs per fixed-length input window
    	•	Inference latency: wall-clock encoding and decoding time
    	•	Memory footprint: peak memory usage during inference
    
    Together, these metrics capture model size, computational intensity, runtime efficiency, and resource requirements, providing a concrete and reproducible definition of model “weight”.
    
    ⸻
    
    Why we expect TCN–RNN AE to be more heavyweight:
    
    We hypothesize that the TCN–RNN autoencoder will exhibit higher computational and memory costs due to its architectural design: deep temporal convolutional stacks with large receptive fields, recurrent (often sequential) decoding, attention mechanisms, and dense continuous latent representations. These components typically lead to increased FLOPs, higher activation memory, and longer inference latency compared to discrete, token-based compression methods. Our experiments explicitly test this hypothesis by measuring efficiency at matched compression ratios.

- Stage 2, Development: (Week 6-10, Deadline: 27.03.)
  - Develop a learnable tokenization module that discretizes data into semantically meaningful
  units optimized for downstream tasks.
    - => Create a more detailed plan for this. 
  - Develop lightweight entropy modeling and coding schemes tailored to the tokenized representations.
    - => Create a more detailed plan for this.
  - Develop a decoder.
    - => Create a more detailed plan for this. 
  - Write the halftime report. 
  - Write the theory part of the final report.
- Stage 3, Experiments: (Week 11-13, Deadline: 17.04.)
  - Train the model from Task 1 on the compressed data using both compression methods. 
  - Evaluate baseline model and proposed tokenization + lightweight entropy model framework based on rate-utility and computational efficiency.
    - => Define metrics in more detail. 
- Stage 4, Finalizing: (Week 14-17, Deadline: 15.05.)
  - Ablation study of the proposed tokenization + lightweight entropy model framework. 
  - Write the methodology, results, discussion, and conclusion part fo the final report. 
