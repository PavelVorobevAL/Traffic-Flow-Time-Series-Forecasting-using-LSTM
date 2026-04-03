# Traffic-Flow-Time-Series-Forecasting-using-LSTM

This project implements a time series forecasting model using Long Short-Term Memory (LSTM) to predict traffic flow based on historical sensor data.

The model is trained on the PEMS-BAY dataset, learns traffic patterns over time and provides predictions.

## DATASET

The PEMS-BAY dataset is a real-world traffic dataset that contains time series measurements of traffic flow collected from highway sensors in the San Francisco Bay Area. The PEMS-BAY dataset contains information on 325 sensors installed on road networks. https://zenodo.org/records/5724362/files/PEMS-BAY.csv?download=1
The dataset contains approximately 52,000 time steps, recorded every 5 minutes. This is approximately 6 months of observation.

The general map:

![Sensor-distribution-of-the-PEMS-BAY-dataset](https://github.com/user-attachments/assets/9c936397-dd6e-4410-a9c8-145ecceead1f)

The data was cleaned and prepared before training.

## MODEL

Long Short-Term Memory (LSTM) is a specialized Recurrent Neural Network (RNN) designed to learn long-term dependencies in sequential data. It uses a memory cell to store information over time, solving the limitations of traditional RNNs. LSTM architectures involves the memory cell which is controlled by three gates (Input gate - controls what information is added to the memory cell, forget gate - determines what information is removed from the memory cell, output gate - controls what information is output from the memory cell)

![8a8ac7c1-8bac-4e89-ace8-9e28813ab635_3](https://github.com/user-attachments/assets/a2d68edd-9475-48ae-9842-16a5b8f11b14)

## TRAINING

The model is trained using sliding window sequences and optimized with Optuna to find the best hyperparameters. After tuning, the LSTM model is retrained on the training data using the Adam optimizer and MSE loss. 

Hyperparameters:

Window size: 6–24

Hidden size: 32–128

Batch size: 16, 32 or 64

Learning rate: 1e-4 to 1e-2

Optimizer: Adam

Loss function: Mean Squared Error

Number of epochs: 10 epochs during tuning and 30 for the final training after optimization with Optuna.

## RESULTS

Metrics: 

MSE (Mean Squared Error): 0.004446407780051231 

MAE (Mean Absolute Error): 0.03902002424001694  (≈4%) 

RMSE (Root Mean Squared Error): 0.06668139005788071 (≈6.6%)

Visualized predictions for one sensor (real traffic values vs. predicted traffic values):

<img width="1021" height="386" alt="Picture1" src="https://github.com/user-attachments/assets/8cd21b3f-4c7c-45b6-bc36-b6b217eed5fb" />



The LSTM model shows good performance with low error values (MAE ≈ 4%, RMSE ≈ 6.6%), indicating accurate predictions. The Model follows overall traffic trend. However, it has some difficulty in predicting sudden changes in traffic flow. 
For more detailed research, it is needed to compare the LSTM model with other models to evaluate and improve prediction performance. The goal of this project is to study the LSTM model and demonstrate how Optuna can be used to optimize the performance.

