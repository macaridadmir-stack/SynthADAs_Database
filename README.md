# SynthADAs_Database

[![DOI](https://doi.org/10.5281/zenodo.23548779)](https://doi.org/10.5281/zenodo.23548779)


SynthADAs is a synthetic database of multimodal physiological signals associated
with Anxious-Depressive Attacks (ADAs). It simulates 100 subjects across four
phases: Neutral, Transition, Induction, and Recovery.

The dataset is hosted on Zenodo: [https://doi.org/10.5281/zenodo.23548779]

This repository provides the MATLAB script used to load and structure the data.

## Data description

The data consist of 400 CSV files (100 subjects × 4 phases). Each file contains
12,000 samples across seven columns:

1. Timestamp
2. ECG
3. Respiration
4. EDA
5. Temperature
6. EMG (left trapezius)
7. EMG (right trapezius)

## Signal specifications

- Sampling frequency: 40Hz
- Duration per recording: 300 s (12,000 samples)
- CSV header row: yes/no

| Column | Signal              | Units |
|--------|---------------------|-------|
| 1      | Timestamp           | s     |
| 2      | ECG                 | mV    |
| 3      | Respiration         | a.u.  |
| 4      | EDA                 | µS    |
| 5      | Temperature         | °C    |
| 6      | EMG left trapezius  | mV    |
| 7      | EMG right trapezius | mV    |

## How to use DataExtraction.m

### Step 1. Prepare the data folder
Download the dataset from Zenodo and extract all 400 CSV files into a single
folder. Do not rename the files, since the script relies on the naming
convention `ID<subject>_<condition>.csv`.

### Step 2. Open the script
Open `DataExtraction.m` in MATLAB (R2019a or later).

### Step 3. Set the input folder
At the beginning of the script, edit the `inDir` variable so it points to the
folder containing the CSV files:

    inDir = 'C:\path\to\your\csv\folder';      % Windows
    inDir = '/home/user/SynthADAs/csv';         % Linux / macOS

### Step 4. Set the output location (optional)
The output file `DataADA.mat` is saved in MATLAB's current folder. To save it
elsewhere, change the current folder before running the script:

    cd('C:\path\to\output\folder')

### Step 5. Run the script
Press **Run** or type in the Command Window:

    DataExtraction

The console prints a message each time a condition finishes loading:

    Neutral loaded (100 files)
    Transition loaded (100 files)
    Induction loaded (100 files)
    Recovery loaded (100 files)

### Step 6. Load the result
Once finished, load the generated file in any MATLAB session:

    load('DataADA.mat')        % creates the 400 x 1 cell array DataADA

See **Accessing the data** for examples of how to index subjects, conditions,
and individual signals.
