<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a name="readme-top"></a>



<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="[https://github.com/captainbluebear/GEOL0069-ML-Inland-Water-Body-Detection]">
    <img src="images/title_banner.png" alt="Banner">
  </a>
</div>

<h1 align="center">Inland Water Body Detection with ML</h1>
<p align="center">
    Using k-means classification to analyse SENTINEL-2 satellite data for inland water bodies.
  </p>
<br />

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#background">Background</a></li>
        <li><a href="#the-sentinel-2-satellite">The SENTINEL-2 Satellite</a></li>
        <li><a href="#machine-learning-methodology-k-means-clustering">Machine Learning Methodology: K-Means Clustering</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#datasets-used">Datasets Used</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
      <ul>
        <li><a href="#references">References</a></li>
      </ul>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
# About The Project

This project is a final assignment for GEOL0069 at University College London, created to explore the usage of machine learning (ML) algorithms in Earth Sciences applications. It utilises unsupervised learning to detect and extract inland water bodies from satellite imagery. SENTINEL-2 data is used due to its high resolution and suitability. The algorithm used throughout this project is k-means classification.

## Background
Inland water bodies play a critical role in global ecology and climate. Consisting of lakes, reservoirs, rivers, and ephemeral waterbodies, they play an important role in many aspects of human society, including the economy, agriculture, and our environments. However, a combination of human activity and climate change has made these bodies of water highly susceptible to change in ways that may affect society. As a result, it is of great significance that inland water bodies are rapidly and accurately monitored (Zeng et al., 2023).

Remote sensing technology has been widely used in surface water body classification due to its global scale, availability, real-time nature, and low cost (Jiang et al., 2020). In comparison to traditional field methods, it is much less time-consuming and labour-intensive (Zeng et al., 2023). Much research has been conducted on how satellite imagery can best be utilised for effecting water body mapping. This project adds to that research by examining how data from the European SENTINEL-2 satellites can be utilised alongside machine learning algorithms to accurately detect inland water bodies.

### Normalized Difference Water Index (NDWI)

In 1996, an index was proposed by S.K. McFeeters called the Normalized Difference Water Index (NDWI), which is expressed as follows:

$$
\text{NDWI} = \frac{\text{Green} - \text{NIR}}{\text{Green} + \text{NIR}}
$$

where Green is a band of green light, and NIR is a Near Infrared Band. The index is designed to maximise values which indicate water while minimising values representing non-water features such as soil or vegetation (Xu, 2006). Since its proposal, this index has been adopted as a general approach for identifying water in satellite imagery. However, the NDWI fails to perform under certain conditions, including when imagery contains areas with built-up or urban land or if the water body has high sediment levels (Xu, 2006; Jiang et al., 2020). As a result, this index will be used as a baseline measurement against which the machine learning algorithms can be compared. However, the goal is to outperform the NDWI especially in cases where it performs poorly.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## The SENTINEL-2 Satellite 
SENTINEL-2 is a European multi-spectral imaging mission, the purpose of which is to support a wide variety of applications including land management, forestry, and humanitarian relief operations. It consists of two satellites SENTINEL-2A and SENTINEL-2B which fly in the same orbit separated by 180 degrees. Both of the SENTINEL-2 satellites carry a single payload called the Multi-Spectral Instrument (MSI), which is an optical instrument that samples 13 spectral bands: four at 10m, six at 20m, and three at 60m spatial resolution (_Sentinel-2 - Overview_, n.d.).

### Multi-Spectral Instrument (MSI)
The MSI utilises a push-broom sensor to capture its data. Push-broom sensors work by collecting horizontal bands of image data as the satellite moves forward, building a band of spectral data along the path of the satellite (*Instrument Payload*, n.d.)

Light reflecting from the Earth’s surface is captured by the sensor and focused onto two focal plane assembles, one for Visible and Near Infrared bands and one for Short Wave Infrared bands. Each focal plane assembly contains 12 detectors with strip filters mounted on top which separate the wavelengths for each of the 13 bands (*Instrument Payload*, n.d.; *Satellite Description,* n.d.).

![how_sen2_works](https://github.com/captainbluebear/GEOL0069-ML-Inland-Water-Body-Detection/assets/59548582/b0ee89f0-dc7c-4f6a-8d12-c1edc238c521)


<p align="right">(<a href="#readme-top">back to top</a>)</p>


## Machine Learning Methodology: K-Means Clustering
The algorithm used throughout this project is K-means clustering, which works by partitioning a dataset into k clusters (groups), where k is some number set by the user. The basic idea is to define k centroids and assign each data point in the dataset to its nearest centroid in such a manner as to keep them as compact as possible within their respective clusters (*Unsupervised Learning — GEOL0069 Guide Book*, n.d.).

K-means is particularly well-suited for applications where the structure of the data is not known. Because K-means does not require any knowledge or input about the data, it is ideal for exploratory analysis. This makes it an ideal choice for this project.

![how_kmeans_works](https://github.com/captainbluebear/GEOL0069-ML-Inland-Water-Body-Detection/assets/59548582/c7beb505-69c3-42bf-b0e3-a65138cd22f2)

### Key Components of K-Means

1. **Choosing K** - the number of centroids must be set before the algorithm can be applied.
2. **Centroid Initialisation** - How the centroids are initially placed can affect the result.
3. **Assignment** - Each data point in the dataset gets assigned to its nearest centroid based upon a calculation of squared Euclidian distance.
4. **Update** - The centroids are recomputed to fit the data points assigned to their respective cluster.
5. **Iterate** - The assignment and update steps are repeated until the centroids no longer move significantly, ensuring that the algorithm converges to a result.


<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- GETTING STARTED -->
# Getting Started

This project was created using [Google Colab]([https://colab.research.google.com/]), a cloud-based platform for modifying and sharing code. To get a copy of this project up and running, follow these steps:
1. Download `ML Detection of Inland Water Bodies.ipynb` from this repository to get started.
2. Download datasets to use. See below for how to acquire datasets.
3. Modify file paths in the Colab notebook to match the location where the dataset was saved. 
    1. If using the same datasets as the original notebook, no other changes are necessary.
    2. If using a different dataset, filenames will also have to be modified where they are used; simply copy the corresponding filename from your dataset and replace the one in the notebook.
4. Run the cells of the notebook sequentially. Further instructions can be found in the notebook.

## Datasets Used

The datasets used for this project are Sentinel-2 L2A datasets, which have been atmospherically corrected. Two areas were examined: a snapshot of an area within the Great Lakes region of North America, and a snapshot of the Ganges River Delta in South Asia. These regions were chosen for their unique geographic characteristics:

- **The Great Lakes** - high concentration of rivers and water bodies in a relatively small area, with many being small in size. As a result, ML algorithms are challenged to be capable of fine discernment between water and land.
- **The Ganges River Delta** - heavily sediment laden, with water appearing tan or brown in RGB satellite imagery. Research has shown that NWDI indexing struggles to detect water with a high sediment concentration, so this dataset was chosen to be more challenging to classify (Jiang et al., 2020).

### Downloading Datasets
The datasets have not been included here due to their size, but individuals interested in using the same data can visit the [Copernicus Dataspace Browser](https://browser.dataspace.copernicus.eu/) to download it. Note that a free account is required for access. To retrieve the data, visit the dataspace browser, switch to the search tab, and enter the following filenames in the search bar:

- `S2B_MSIL2A_20240426T162829_N0510_R083_T16TGS_20240426T204803.SAFE` (Great Lakes region)
- `S2A_MSIL2A_20240427T082601_N0510_R021_T36RUU_20240427T125051.SAFE` (Ganges Delta region)

Download the files and unzip them in your file system.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- LICENSE -->
# License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTACT -->
# Contact

Fiona McKee - [fiona.mckee.23@ucl.ac.uk](mailto:fiona.mckee.23@ucl.ac.uk) / [mckee.c.fiona@gmail.com](mailto:mckee.c.fiona@gmail.com) / [www.linkedin.com/in/fiona-mckee](http://www.linkedin.com/in/fiona-mckee)

Project Link: https://github.com/captainbluebear/GEOL0069-ML-Inland-Water-Body-Detection

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
# Acknowledgments
This project was created for GEOL0069 at University College London, taught by Dr. Michel Tsamados and Weibin Chen.

## References
*Instrument Payload*. (n.d.). Sentinel Online. https://sentinels.copernicus.eu/web/sentinel/missions/sentinel-2/instrument-payload

Jiang, W., Ni, Y., Pang, Z., He, G., Fu, J., Lu, J., Yang, K., Long, T., & Lei, T. (2020). A NEW INDEX FOR IDENTIFYING WATER BODY FROM SENTINEL-2 SATELLITE REMOTE SENSING IMAGERY. *ISPRS Annals of the Photogrammetry, Remote Sensing and Spatial Information Sciences*, *V-3–2020*, 33–38. https://doi.org/10.5194/isprs-annals-v-3-2020-33-2020

*Overview*. (n.d.). Sentinel Online. https://sentinels.copernicus.eu/web/sentinel/missions/sentinel-2/overview

*Satellite Description*. (n.d.). Sentinel Online. https://sentinels.copernicus.eu/web/sentinel/missions/sentinel-2/satellite-description

*Unsupervised Learning — GEOL0069 Guide Book*. (n.d.). https://cpomucl.github.io/GEOL0069-AI4EO/Chapter1%3AUnsupervised_Learning_Methods.html

*What is unsupervised learning? | IBM*. (n.d.). https://www.ibm.com/topics/unsupervised-learning

Xu, H. (2006). Modification of normalised difference water index (NDWI) to enhance open water features in remotely sensed imagery. *International Journal of Remote Sensing*, *27*(14), 3025–3033. https://doi.org/10.1080/01431160600589179

Zeng, F., Song, C., Cao, Z., Xue, K., Lu, S., Tan, C., & Liu, K. (2023). Monitoring inland water via Sentinel satellite constellation: A review and perspective. *ISPRS Journal of Photogrammetry and Remote Sensing*, *204*, 340–361. https://doi.org/10.1016/j.isprsjprs.2023.09.011

<p align="right">(<a href="#readme-top">back to top</a>)</p>
