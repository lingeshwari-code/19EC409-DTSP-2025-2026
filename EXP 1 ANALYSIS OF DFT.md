# EXP 1 :  ANALYSIS OF DFT WITH AUDIO SIGNAL

# AIM: 

  To analyze audio signal by removing unwanted frequency. 

# APPARATUS REQUIRED: 
   
   PC installed with SCILAB/Python. 

# PROGRAM: 
```
import numpy as np
import matplotlib.pyplot as plt
from scipy.io import wavfile
from scipy.signal import butter, lfilter

# Load audio file
fs, data = wavfile.read("input_audio.wav")

# Design Low-Pass Filter (cutoff = 4000 Hz)
def butter_lowpass(cutoff, fs, order=5):
    nyq = 0.5 * fs
    normal_cutoff = cutoff / nyq
    b, a = butter(order, normal_cutoff, btype='low', analog=False)
    return b, a

def lowpass_filter(data, cutoff, fs, order=5):
    b, a = butter_lowpass(cutoff, fs, order=order)
    y = lfilter(b, a, data)
    return y

# Apply filter
filtered_signal = lowpass_filter(data, cutoff=4000, fs=fs)

# Save output
wavfile.write("output_audio.wav", fs, filtered_signal.astype(np.int16))

# Plot before and after
plt.figure(figsize=(12,6))
plt.subplot(2,1,1)
plt.plot(data, color='blue')
plt.title("Original Signal")

plt.subplot(2,1,2)
plt.plot(filtered_signal, color='red')
plt.title("Filtered Signal (Low-pass)")
plt.tight_layout()
plt.show()
```

# OUTPUT: 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c99bac52-0b7f-46af-a537-8ad17c1dac82" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/893a2d81-4626-4efd-a8bd-ffed11958c28" />

# RESULTS
 Hence verified the audio signal by removing unwanted frequency.
