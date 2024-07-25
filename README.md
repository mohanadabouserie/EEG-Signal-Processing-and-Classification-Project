# EEG-Signal-Processing-and-Classification-SSVEP-Project

## Overview
This project aims to analyze Steady-State Visual Evoked Potentials (SSVEP) using digital signal processing techniques and machine learning methods. The analysis was conducted using Python libraries such as pandas, numpy, matplotlib, scipy, and sklearn.

## Data Preprocessing

1. **Data Import:**
   - Import EEG and stimulus data from CSV files into pandas DataFrames.

2. **Identifying Stimulus Ranges:**
   - Identify the time ranges during which the stimulus is active.

3. **Average Reference Calculation:**
   - Compute the average reference of the EEG data across all electrodes for common average referencing (CAR).

4. **Applying CAR:**
   - Subtract the average reference from each electrode's signal.

5. **FFT Computation:**
   - Define a function `compute_fft` to compute the Fast Fourier Transform (FFT) of an electrode signal.

6. **Extracting Electrode Data:**
   - Extract specific electrode data (O1 and O2) before and after CAR and compute the average of these signals.

7. **Frequency and Amplitude Analysis:**
   - Perform FFT on the extracted electrode data for the identified stimulus ranges and store the frequency and amplitude information.

8. **Visualization:**
   - Generate plots to visualize the frequency and amplitude of the EEG signals before and after CAR.

## Method 1: Frequency-Domain Analysis

1. **Cleaning Data:**
   - Apply CAR and average the combined signals from electrodes O1 and O2.
   
2. **FFT Application:**
   - Apply FFT on each trial's signals to obtain the frequency bins.
   
3. **Frequency Window:**
   - Average the frequency bins close to the ideal frequencies (6.66, 7.5, 8.57, 10, and 12 Hz) to identify the stimulus.

### Results
- **Electrode O1:**
  - Subject 1: 56.80%
  - Subject 2: 52.80%
- **Electrode O2:**
  - Subject 1: 71.20%
  - Subject 2: 77.60%
- **Combined O1 and O2:**
  - Subject 1: 64.00%
  - Subject 2: 70.40%

## Method 2: Machine Learning with K-Nearest Neighbors (KNN)

1. **Feature Extraction:**
   - Use frequency amplitude data from index 20 to 120 for each electrode as features.
   
2. **Data Preparation:**
   - Average features from electrodes O1 and O2, and create a combined feature set for all electrodes.
   
3. **Classification:**
   - Train and evaluate a KNN classifier using Leave-One-Out (LOO) cross-validation.

### Results
- **Electrode O1:**
  - Subject 1: Best K = 4 with 0.568 accuracy
  - Subject 2: Best K = 21 with 0.464 accuracy
- **Electrode O2:**
  - Subject 1: Best K = 7 with 0.904 accuracy
  - Subject 2: Best K = 7 with 0.928 accuracy
- **Combined O1 and O2:**
  - Subject 1: Best K = 8 with 0.84 accuracy
  - Subject 2: Best K = 1 with 0.88 accuracy
- **All Electrodes:**
  - Subject 1: Best K = 29 with 0.792 accuracy
  - Subject 2: Best K = 25 with 0.688 accuracy

## Conclusion
The project successfully applied digital signal processing and machine learning techniques to analyze SSVEP signals. The combination of frequency-domain analysis and KNN classification demonstrated effective methods for identifying visual stimuli frequencies from EEG data.
