# Determining the Temperature of a Blackbody through the Monte Carlo Method

## Abstract

This Python code serves as an example of fitting a blackbody spectrum and can be adapted for fitting other types of spectral data. The Python code aims to determine the temperature (T) of a blackbody by fitting a spectrum to the Planck function using the Monte Carlo method. In the end, the goal is to identify parameters that best describe a blackbody, such as temperature and scale factor, while excluding identified absorption bands.

## About the Repository

- ‘corpo_negro.txt’: An example file containing blackbody spectrum data. The data is presented in two columns, where the first column represents the wavelength in micrometers, and the second column represents the spectral emissive power (W / (m^2 * micron)).

- ‘corpo_negro_fit.ipynb’: Python code performing the fitting.

## Dependencies

- NumPy
- Matplotlib
- SciPy

## How to Use the Code

Clone this repository or download the 'corpo_negro_fit.py' file to your working environment. Run the 'corpo_negro_fit.ipynb' Python code in your environment, such as Jupyter Notebook or an integrated development environment (IDE) of your choice.

First, ensure that the data file 'corpo_negro.txt' is present in the same directory as the Python file. The data in the 'blackbody_spectrum.txt' file must be formatted correctly, with two columns separated by spaces or commas. The required libraries must be installed in your Python environment.

## Methodology

The code follows the following methodology to fit the blackbody spectrum:

The fitting function is formulated based on Planck's Law, describing the spectral intensity of a blackbody in terms of temperature and wavelength. The 'planck_lambda' function is defined to calculate the theoretical spectral intensity using Planck's Law. Absorption bands in the spectrum are identified by finding local minima in emissive power, indicating where the intensity likely drops due to energy absorption. A boolean mask, [mask], is created to automatically exclude these bands from the fit. Subsequently, we use this same mask with the inverse goal, to identify and list these bands. The temperature uncertainty is calculated from the standard deviation of temperature samples.

The Monte Carlo method will estimate the fitting parameters (temperature and scale factor). One thousand samples are generated to perturb the initial parameters with random noise, and at each iteration, the perturbed data is fitted to the Planck function using the 'curve_fit' function from the SciPy library. The number of samples can be adjusted to balance precision and runtime, but more accurate results will sacrifice time, taking longer to generate outputs. The Chi² value is calculated for each set of estimated parameters, allowing a comparison of observed emissive power with theoretical emissive power.


## Outputs

The results include the following items:

- A plot with the fit compared to the original data and absorption bands within the sample
- Temperature values, uncertainty, Chi², and a list of identified absorption bands
