# Digital snow melt - Automated forecasting from snow parameters

###### <h6 align="right"> - A group project by Florian Donhauser, Fabienne Greier, Md. Forhad Hossain, Robin Mittas, Wudamu from TU - Munich</h6>

## Table of Contents

1. [Introduction](#introduction)
2. [Abstract](#abstract)
3. [Dependencies](#dependencies)
4. [How to trigger the different scripts](#how-to-trigger-the-different-scripts)

--- 

## Introduction

This project took place in the winter semester of 2021 as part of the [TUM Data Innovation Lab](https://www.mdsi.tum.de/en/di-lab/tum-di-lab/) educational research experience at the Technical University of Munich. The program brings together master’s students to work on real-world, interdisciplinary data science challenges in collaboration with academic and industry partners, offering hands-on experience in AI and data-driven problem solving.

## Abstract
The forecast of seasonal snowmelt and inflow into water reservoirs based on automatic extraction of snow parameters plays a crucial role in the hydropower industry to plan and deliver energy more efficiently.
This project aims to research appropriate Machine Learning (ML) methods for predicting the water inflow of specific reservoir lakes, implement a model based on an open-source ML model, train it with Norwegian data, and optimize the model prediction performance.
To retrieve the Norwegian data, a DataLoader was created that downloads the weather station data from a website.
In the downloaded data, many measurements were missing. Therefore, several techniques were developed to fill in the missing values.
The target data of inflow into a water reservoir, provided by customers of the Norwegian startup ThinkOutside, had large fluctuations, so the temporal resolution had to be changed.
After cleaning up and restructuring the existing code that served as a basis for the model, hyperparameter tuning was performed using Optuna to find the best configurations.
Different prediction time frames were tested to evaluate the performance of the ML model. Overall, the accuracy of the predictions increased with tuned hyperparameters. However, some stations with noise in the year prior to the forecast showed poor performance. For these stations, it is recommended to use coarser methods for resampling the data.

## Dependencies
We have created a requirements.txt file which contains all python-packages needed to run the code.
To install these packages, we suggest creating a virtual environment to run all scripts.

## How to trigger the different scripts
- First of all, we need to download the data. For that, navigate into the /download_data folder and specify your configurations; afterwards, run download_data.py. Please make sure to have a good NA treatment. Default values will do so.
- As a next step, we can trigger the script /ResCNN_LSTM/hyperparameter_tuning.py which will find the best possible hyperparameters for the specified station, date setting in /ResCNN_LSTM/config.yaml
- Once this has run successfully, we can have a look at/ResCNN_LSTM/hypertune_configs/configs_evaluation.txt and find the best config setting
- Now we just have to modify the path to this specific setting in /ResCNN_LSTM/ResCNN_LSTM_fit.py in the very last line of the code

##### Disclaimer: Most of the data and some of the code are confidential and hence not included in the repository. 
