# Signals-system
Code 1 for filtering the signal
This MATLAB code is designed to read audio data from one or more WAV files provided by the user and then perform the Discrete Fourier Transform (DFT) on the audio signals to obtain their frequency spectra. The code plots the magnitude spectra of the audio signals on separate subplots, with each subplot corresponding to one input WAV file.

Here's a step-by-step description of the code:

1. Initialize variables:
   - `num_inp`: Number of WAV files that the user wants to process. In this code, it is set to 1.
   - `filenames`: A cell array to store the names of the WAV files.
   - `audio_data`: A cell array to hold the audio data read from each WAV file.
   - `fs_all`: A numeric array to store the sample rate of each WAV file.

2. Loop through each input:
   - A `for` loop is used to iterate through each input (in this case, it runs only once since `num_inp` is 1).
   - The user is prompted to enter the name of the WAV file. The entered filename is stored in the `filenames` cell array.

3. Read audio data and sample rate:
   - The code uses the `audioread` function to read the audio data and the sample rate from the WAV file specified by the user.
   - The audio data is stored in the corresponding index of the `audio_data` cell array.
   - The sample rate is stored in the corresponding index of the `fs_all` numeric array.

4. Calculate the frequency axis:
   - The length of the audio data (`N`) is calculated.
   - A frequency axis (`freqs`) is created from 0 Hz to the Nyquist frequency (half the sample rate) with a frequency resolution of `fs_all(i)/N` Hz. The frequencies are evenly spaced.

5. Perform the Discrete Fourier Transform (DFT):
   - A nested `for` loop is used to calculate the DFT of the audio data.
   - For each frequency index `k`, the DFT is computed using the formula involving a summation over all audio samples at index `n`. This calculation finds the complex amplitude of each frequency component in the audio signal.

6. Calculate the magnitude spectrum:
   - The magnitudes of the complex amplitudes (`mags`) are computed by taking the absolute values of the DFT coefficients.
   - Only the positive half of the spectrum is kept since the negative half is symmetrical due to the nature of real-valued audio signals.

7. Plot the magnitude spectrum:
   - A subplot is created for each input WAV file.
   - The frequency axis (`freqs`) is plotted on the x-axis, and the magnitude spectrum (`mags`) is plotted on the y-axis.
   - The title of each subplot shows the index of the input (`i`) and the filename of the corresponding WAV file.

Note: The code uses the complex exponential in the DFT calculation, which is the direct implementation of the DFT equation but not the most efficient method. The Discrete Fourier Transform can also be efficiently computed using the Fast Fourier Transform (FFT) algorithm, which is available in MATLAB and other programming languages. Using FFT would significantly improve the performance of the code, especially for larger audio signals.
