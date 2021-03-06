# Wearable_Posture_Corrector

## Summary
> Wearable device that notifies the user when they are slouching for 7 seconds or more.


https://user-images.githubusercontent.com/84931559/156413828-600d1e9e-73e9-4acd-ada2-8e82b057e9b7.mp4
> Note: You may need to turn up volume to hear alarm in the video.

- Uses SEFR machine learning algorithm
- 600 training data samples (300 for slouch, 300 for non-slouch)
- Features of SEFR classifier include 
  - Mean x, y, and z acceleration
  - Mean x, y, and z RMS acceleration
- Piezo to notify user (can be replaced with vibration motor for less noise).
- 300 ms sampling interval

# Setup
## Get Training Data
1. Upload 'mpu' Arduino code to Uno board.
2. In MATLAB, have 'getTrainingData.m' and 'getFeatures.m' in the environment.

Setup the circuit as shown below.

<img src="https://user-images.githubusercontent.com/84931559/120691398-697d4580-c474-11eb-9fd0-e62b2ad93697.png" width="500">

3. Run 'getTrainingData.m'
4. The collected training data is stored in your workspace variable 'trainingData'. Copy the training data to a CSV file and manually input the label as 1 for slouching and 0 for non-slouching in the last column. My training data is included for reference.
5. Continue to run 'getTrainingData.m' to gather training data.


## Export SEFR to C++
1. Load 'sefr_ml' Python program.
2. Replace the path with your CSV path that contains your training data.
3. Run the Python script and the output is your SEFR classifier code in C++. 
4. Save the output code as a .h file.

## Deploy Classifier to Project
1. Upload "posture" Arduino code to Arduino IDE.
2. Include the SEFR .h file into the same folder as the "posture" Arduino code
3. Upload the code to Arduino Pro Mini board.
4. The schematic for my project is below. I used a 300 mAH battery. The power switch and charging module are different than what I  used, but equivalent in function.
<img src="https://user-images.githubusercontent.com/84931559/150038112-4ea1d3c6-2236-400d-b85c-bd8eabf97f7b.JPG" width="500px">

