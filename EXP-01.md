
## EXPERIMENT 1: Measurement of Fiber Optic Loss

## AIM
To measure propagation loss and bending losses for two different wavelengths in plastic optical fiber using Python simulation.

## SOFTWARE REQUIRED
- Python 3.x
- Python IDE

## PROCEDURE

1.Import the required Python libraries, namely NumPy, Pandas, and Matplotlib, for calculations, tabulation, and plotting graphs.

2.Define the fiber lengths, input and output amplitudes, and bending diameters with their corresponding input and output amplitudes.

3.Calculate propagation loss for different fiber lengths using the input and output amplitudes.

4.Calculate bending loss for different bending diameters using the corresponding input and output amplitudes.

5.Display the calculated propagation and bending losses in tabular form using Pandas DataFrames.

6.Generate sinusoidal waveforms to compare input and output signals for different fiber lengths and bending diameters.

7.Plot the graphs with appropriate titles, axis labels, legends, and grid lines, and observe the variation in optical signal loss.

## PROGRAM
```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Change these values whenever you want
frequency = 1000

# Propagation loss values
length = [1, 2, 3, 4]
input_amp = [5.0, 5.0, 5.0, 5.0]
output_amp = [4.5, 4.2, 3.9, 3.6]

# Bending loss values
diameter = [30, 25, 20, 15]
bend_input = [5.0, 5.0, 5.0, 5.0]
bend_output = [4.8, 4.5, 4.0, 3.2]

# Calculate propagation loss
prop_loss = [
    20 * np.log10(i / o)
    for i, o in zip(input_amp, output_amp)
]

# Calculate bending loss
bend_loss = [
    20 * np.log10(i / o)
    for i, o in zip(bend_input, bend_output)
]

# Display propagation table
print("PROPAGATION LOSS")
display(pd.DataFrame({
    "Length (m)": length,
    "Input (V)": input_amp,
    "Output (V)": output_amp,
    "Loss (dB)": np.round(prop_loss, 2)
}))

# Display bending table
print("BENDING LOSS")
display(pd.DataFrame({
    "Diameter (mm)": diameter,
    "Input (V)": bend_input,
    "Output (V)": bend_output,
    "Loss (dB)": np.round(bend_loss, 2)
}))

# Generate graphs
t = np.linspace(0, 4 / frequency, 1000)

plt.figure(figsize=(10, 5))
for i in range(4):
    plt.plot(t, input_amp[i] * np.sin(2*np.pi*frequency*t),
             label=f"Input {length[i]} m")
    plt.plot(t, output_amp[i] * np.sin(2*np.pi*frequency*t),
             "--", label=f"Output {length[i]} m")

plt.title("Propagation Loss")
plt.xlabel("Time (s)")
plt.ylabel("Voltage (V)")
plt.grid(True)
plt.legend(ncol=2)
plt.show()

plt.figure(figsize=(10, 5))
for i in range(4):
    plt.plot(t, bend_input[i] * np.sin(2*np.pi*frequency*t),
             label=f"Input {diameter[i]} mm")
    plt.plot(t, bend_output[i] * np.sin(2*np.pi*frequency*t),
             "--", label=f"Output {diameter[i]} mm")

plt.title("Bending Loss")
plt.xlabel("Time (s)")
plt.ylabel("Voltage (V)")
plt.grid(True)
plt.legend(ncol=2)
plt.show()
```
## TABULATION:

<img width="1600" height="1446" alt="image" src="https://github.com/user-attachments/assets/617bc146-de17-4b87-ba0c-c30db47eb454" />

<img width="1600" height="1168" alt="image" src="https://github.com/user-attachments/assets/a809e884-9a49-4e18-a9e1-e18b52278714" />


## OBSERVATION:
<img width="844" height="470" alt="image" src="https://github.com/user-attachments/assets/7d989dff-eec5-454e-8528-92b9863cfe4a" />
<img width="844" height="470" alt="image" src="https://github.com/user-attachments/assets/eb6b8948-4d4e-488d-a592-e2fc098bb9cd" />


## RESULT:
Propagation loss and bending losses for 660nm wavelength is measured.

Attenuation values compared and bending loss characteristics plotted.



