# Forecasting Mobile Network Traffic

In this homework, we addressed two main tasks using the telecommunications activity dataset for the city of Milan (20 Gb data), recorded over two months (November to December) during a data collection campaign. Below are the main steps for this homework (you are invited to read the homework and the report to better understand the overall tasks).
<img width="589" height="485" alt="image" src="https://github.com/user-attachments/assets/10e64b23-a0e4-4bd7-993f-bfa6b9990cb1" />

---

## Quick start

- Go to this link: https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/EGZHFV to progressively download the TXT files (e.g., 62 TXT files providing information about telecommunications activity over the city of Milan)  
- Load them into *dataset1/*  
- Generate one CSV file from the 62 TXT files to make processing easier:
  - Run *load_csv_from_txt_files.ipynb*  
  - This function will preprocess the TXT files and generate `internet_traffic_milano_nov-dec-2013.csv`  
  - This CSV file will be used in Task I and II to deduce relevant datasets  
- Use the Python environment defined in `environment.yml`, where all the required libraries to run this project are included  

---

## Time series analysis using pandas

- We plotted internet traffic activity distribution over two months for a geographical area  
- We plotted the time series of the first two weeks for three different geographical areas (e.g., hourly and daily basis)  
- We added some additional plots to strengthen our analysis (e.g., heatmap of two months traffic per geographical area, average hourly usage in a day for the first two weeks)  
- We discussed the results  
- **Code**: *task_I_data_characterization.ipynb*  

---

## One-step prediction algorithm using LSTM and a recursive method to predict multi-step predictions

- We had several options for the model choice, from classical models to machine learning or deep learning models  
- Since I have experience with deep learning, I decided to develop the prediction algorithm with a simple LSTM architecture  
- We trained an LSTM model to predict the next hour of traffic activity in a given area using 24 hours of past history  

---

## How to run the prediction algorithm

### 1. One-step prediction (e.g., test the algorithm)

- Go to *Task_II_time_series_forecasting.ipynb* in the principal working directory  
- Load the minimum dataset for the three areas (e.g., `data_task_II.csv`) first  
- Call `x_hat_next(a, x_t)` with:
  - **a**: Square ID (geographical area)  
  - **x_t**: Array of 24 past hourly traffic values, scaled using the MinMaxScaler fitted on the training data  

---

### 2. Multi-step prediction (recursive) (e.g., the week of Dec 16–22)

- Go to *Task_II_time_series_forecasting.ipynb* in the principal working directory  
- Run the function `multi_step_prediction(a)` for one of the three geographical areas  
