![Python](https://img.shields.io/badge/python-v3.8-blue)
![Numpy](https://img.shields.io/badge/numpy-v1.20.2-brightgreen)
![Pandas](https://img.shields.io/badge/pandas-v1.4.2-orange)
![Scipy](https://img.shields.io/badge/scipy-v1.6.3-blueviolet)
![Spectral](https://img.shields.io/badge/spectral-v0.22.2-yellowgreen)
![ReleaseDate](https://img.shields.io/badge/release%20date-oct%202024-red)
![OpenSource](https://img.shields.io/badge/OpenSource-Yes!-6f42c1)

# Coupling hyperspectral imaging and deep learning to detect bloom-forming toxic cyanobacteria in mixed assemblages - code for hyperspectral image calibration and spectral extraction.

This is the official repository for the code accompanying the paper **"Coupling hyperspectral imaging and deep learning to detect bloom-forming toxic cyanobacteria in mixed assemblages."**

**Authors**: [Claudia Fournier<sup>1</sup>](https://www.linkedin.com/in/claudia-fournier/), 
[Samuel Cirés<sup>1</sup>](https://uam.es/Ciencias/Samuel-Cir%C3%A9s-G%C3%B3mez/1446778837268.htm?language=es&pid=1446767912028&s%20G?mez,%20Samuel), 
[Mohammadmehdi Saberioon<sup>2</sup>](https://www.gfz-potsdam.de/staff/mohammadmehdi.saberioon/sec14),
[Paula Martín-González<sup>1</sup>](https://www.linkedin.com/in/paula-mart%C3%ADn-gonz%C3%A1lez215/),
[Antonio Quesada<sup>1</sup>](https://uam.es/Ciencias/Antonio-Quesada-del-Corral/1446747451944.htm?language=es&pid=1446767912028&%20Antonio) <br />

<sup>1</sup> Departamento de Biología, Universidad Autónoma de Madrid, 28049 Madrid, Spain

<sup>2</sup> Section 1.4 Remote Sensing and Geoinformatics, German Research Centre for Geosciences (GFZ), Telegrafenberg, 14473 Potsdam, Germany

This repository contains Jupyter notebooks used for the calibration of hyperspectral images and the extraction of spectral data from the region of interest.

**For more details, please refer to the [paper(LINK)]** (paper available soon)


## Introduction

Cyanobacterial blooms in freshwater ecosystems pose risks to water quality and public health. This project applies hyperspectral imaging and deep learning techniques to detect and classify toxic cyanobacteria species in bloom-forming assemblages. Using machine learning models trained on hyperspectral data, this approach aims to distinguish cyanobacterial genera with high accuracy, even in mixed environments.

## Methodology: Hyperspectral Image Calibration and Spectral Extraction

### Hyperspectral Image Acquisition

The hyperspectral images used in this project were acquired using a line-scanning hyperspectral imaging (HSI) system with an internal push-broom configuration, operating in the visible to near-infrared (VIS-NIR) region. The system captured reflectance data across 204 spectral bands, ranging from 397 to 1004 nm, with a spectral resolution of 7 nm. Samples of cyanobacterial cultures were placed in Petri dishes, and the raw hyperspectral data, along with dark and white references, were collected for further processing.

### (1) Image Calibration

The first step in the hyperspectral image processing is calibration, which corrects the raw image data by removing noise and normalizing the spectral values based on the reference images. The calibration was performed using the following equation:

$I_i = (R_i - D_i) / (W_i - D_i)$

Where:
- $`I_i`$ is the corrected hyperspectral image,
- $`R_i`$ is the raw hyperspectral image,
- $`W_i`$ is the white reference image,
- $`D_i`$ is the dark reference image,
- $`i`$ corresponds to the pixel index.

### (2) Spectral Extraction

Once the images are calibrated, the spectral data is extracted from the **Region of Interest (ROI)**, which includes only the pixels containing cyanobacterial biomass. A mask is created by applying a ratio of reflectance between two key wavelengths (751 nm and 676 nm). Pixels with a ratio greater than 1.5 are considered to contain biomass, and only those pixels are included in the mask. Additionally, a quality filter is applied, where pixels with a mean reflectance below 0.01 are discarded to ensure only high-quality data is retained.

### (3) Spectral Grouping

To reduce noise and maintain the spectral variability, the extracted spectra are grouped into packages of 20 randomly selected spectra. This grouping helps avoid potential spatial biases and ensures a representative sample from each image. To prevent overfitting in subsequent analyses, only a small percentage (in this case 3%) of the spectral packages are retained for further processing (fewer than 30 spectral packages per image).


## Notebooks and usage

The `notebooks/` directory contains the following Jupyter notebooks:

1. **hsi_calibration_step-by-step.ipynb**: Applies the calibration equation ((raw_image - dark_ref) / (white_ref - dark_ref)) to obtain calibrated images, processed one hyperspectral image directory at a time.

2. **hsi_calibration_automated.ipynb**: Automates the calibration equation ((raw_image - dark_ref) / (white_ref - dark_ref)) to process multiple directories of hyperspectral images at once.

3. **hsi_spectral_extraction_step-by-step.ipynb**: Defines and applies the wavelength ratio for spectral extraction, followed by a quality filter, and creates spectral groups using a random pixel selection strategy. Processes one hyperspectral image directory at a time.

4. **hsi_spectral_extraction_automated.ipynb**: Automates the spectral extraction process by defining the wavelength ratio, applying quality filters, and creating spectral groups using random pixel selection. This notebook processes multiple directories of hyperspectral images.

**To run any notebook please open the files on Google Colab or Jupyter Notebook.**


## Data Availability

A demo dataset to run the code is provided at [Download the dataset from Google Drive](https://drive.google.com/drive/folders/1U7D0wilTyeWWNS8UFReOImpUR5D1l3zS?usp=drive_link)

Please download and add the `data` folder into the `notebook` folder.


## Contributors

The following authors were also responsible for the code in this repository:
- Claudia Fournier (https://github.com/ClaudiaFournier)
- Mohammadmehdi Saberioon (https://github.com/saberioon)


## Citation

If you find our work useful in your research, please consider citing:

INCLUDE CITATION (paper available soon)


## License

This project is licensed under the EUPL-1.2 License.


## Updates

* dd/mm/YYYY modification message
* 08/11/2024 publication date
