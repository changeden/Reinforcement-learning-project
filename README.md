# Reinforcement-learning-project


#EEC256 Final Project - ATE Drift Prediction

This project simulates an ATE environment to test how drift affects the chip classifying quality and to find the recalibration strategy. Our goal is to minimize the misclassification rate and overall cost by choosing the optimal time to recalibrate.

##How to run
1. Upload EEC256_final_project.ipynb and README.md to Google Colab
2. pip install tqdm
3. Run the code cell by cell from top to bottom

##Run time
Roughly 15 minutes

##Overview
- Drift is modeled as a function of temperature, humidity, and chip age
- Each chip is evaluated based on its output voltage, leakage current, and propagation delay and is labeled as "good" or "bad"
- The project compares three strategies:
  1. Always testing (no recalibration)
  2. Double Q-learning
  3. Threshold-based recalibration

##Code
###1. ATE Environment
- Defines ATEEnv class:
  - Reset the drift after recalibration
  - Defines rewards
  - Defines when the simulation ends

###2. Chip Generating
- Defines ChipGenerating class:
  - Defines chip parameters(output voltage, leakage current, propagation delay)
  - Generates a batch of chips and classifies them as "good" or "bad" based on parameters

###3. Main Loop
- Learns optimal recalibration timing using Double Q-learning algorithm
- Selects actions based on epsilon-greedy policy
- Updates Q-values based on rewards and next states

###4. Result
- Run three models: Always testing(no recalibration), Double Q-learning, and Threshold-based recalibration
- Evaluate the performance of the models using confusion matrix and classification report
- Plots the drifts value (solid line) and the timing of recalibration (dotted line) over time for the first and last episodes
  - Green dotted line: too early
  - Blue dotted line: on time
  - Red dotted line: too late
