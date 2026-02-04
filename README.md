[![Issues][issues-shield]][issues-url]

[![alt_text](https://vinepair.com/wp-content/uploads/2015/08/hops-and-beer-social.jpg)](https://vinepair.com/wp-content/uploads/2015/08/hops-and-beer-social.jpg)
<br/>*Image Source: VinePair*
<br />
<!---
<div align="center">
  <a href="https://github.com/rc-9/tools1_project">
    <img src="beerhops.png" alt="Logo" width="80" height="45">
  </a>
-->



<h1 align="center">BrewModel: Hops Flavor & Aroma Profiler</h1>
  <p align="center">
    Tomer D. & Romith C.
    <br />
    <br />
    <a href="https://github.com/rc-9/Beer_Hops_Analysis/issues">Report Bug</a>
    ·
    <a href="https://github.com/rc-9/Beer_Hops_Analysis/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a>Prerequisite Installations</a></li>
        <li><a>Repository Cloning</a></li>
        <li><a>Environment Setup</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
      <ul>
        <li><a>Scraper</a></li>
        <li><a>Cleaner</a></li>
        <li><a>EDA</a></li>
        <li><a>Classifier</a></li>
        <li><a>Analyzer</a></li>
      </ul>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



## About The Project

Hops are primarily used as a bittering, flavoring, and stabilizing agent in beer. 
In recent years, hops have become the center of attention in the beer industry, as hop-forward beers have become one of the most popular styles of beer. 
Hops varieties are developed and grown in moderate climates around the world. 
Every branded hop variety has a unique flavor and aroma profile. 
This makes for an exciting and delicious reason to explore what flavor and aroma a hop can offer on its own, or together with other hops to bring waves and layers of flavor and aromas. 

The purpose of this project is to build a processed dataset to explore some definitive hop characteristics, draw initial insights into geographical relationships between hops, and lay the groundwork for further model-building in future studies. 
The first step was to compile a comprehensive dataset that consists of these characteristics, with both numeric brew values, as well as an aroma profile for each hop.
This was achieved through scraping BeerMaverick's database of a diverse set of 300+ hops from around the world. 
This raw data was thoroughly processed for exploratory studies, and feature-engineered to create insightful visualizations & prepare for initial model-building.
Using a supervised tree-based ensemble methods (XG-Boost & Random Forest), these preliminary models were built for a deeper look into classification techniques of beer hops.


<p align="right">(<a href="#top">back to top</a>)</p>



## Getting Started

This section walks through the steps to download a local copy of the project and reproduce the findings.

### Prerequisites

Python 3.X and a means of accessing iPython notebook files is assumed. Links below walk through the necessary steps to fulfill these prerequisites.

Windows:
<br/>
https://medium.com/@kswalawage/install-python-and-jupyter-notebook-to-windows-10-64-bit-66db782e1d02
<br/>
MacOS:
<br/>
https://docs.python-guide.org/starting/install3/osx/
<br/>
https://medium.com/@blessedmarcel1/how-to-install-jupyter-notebook-on-mac-using-homebrew-528c39fd530f

### Repository Cloning

1. Navigate to a directory to save the repo through a Terminal.
   ```
   cd c:\path\to\directory
   ```
2. Clone the repo
   ```
   git clone https://github.com/rc-9/tools1_project.git
   ```
   
### Environment Setup

1. Install virtual environment capability.
    ```
    pip install virtualenv
    ```
2. Navigate to directory of the cloned repo and create a virtual environment for the project.
    ``` 
    python -m venv c:\path\to\directory\venvname
    ```
3. Activate virtual environment for the project.
    ``` 
    .\venv\Scripts\activate
    ```
4. Install necessary modules from the provided requirements file.
    ``` 
    pip install -r requirements.txt
    ```
5. Launch Jupyter through virtual environment to view and execute codeblocks or run scripts directly in Terminal for outputs files.

<p align="right">(<a href="#top">back to top</a>)</p>


## Usage

This section outlines the order to execute iPython scripts to retrieve & clean the necessary data, generate visuals, perform analysis, and build basic classification models.
<br/> <br/>

1. Execute ```step1_scraper.ipynb``` to collect the info from BeerMaverick's Hops Database.
This script is designed to take **40+ minutes** to fully execute and scrape all the necessary data. 
As the database contains over 300+ hops, each with individual webpages for detailed info, the scraper is set up with a wait-time to ensure the scraping can be fully completed without running into automatic IP blocks. 
**This step is optional and can be skipped to avoid the long run-time as the output ```raw_data.csv``` is already provided in the repository.**
<br/> <br/>
The raw data is stored in the ```raw_data``` directory consisting of the following ```csv``` files:
    - ```raw_hops_main.csv```: primary data file to be used for cleaning & analysis
    - ```raw_ref_aroma_types.csv```: reference document for metadata info on aroma types
    - ```raw_ref_brew_values.csv```: reference document for metadata info on brew values
    - ```raw_ref_hops_substitutions.csv```: reference document for metadata info on pre-determined hop substitutions
<br/> <br/> <br/>

2. Execute ```step2_cleaner.ipynb``` to wrangle and feature-engineer the raw data files from ```raw_data``` and store cleaned data into ```clean_data```.
<br/> <br/>
The ```clean_data``` directory consists of the following ```csv``` files:
    - ```cln_hops_brewvalues.csv```: processed numerical data for various brew values for each hop
    - ```cln_hops_profile.csv```: processed categorical & boolean data of country, purpose, aroma info for each hop
    - ```cln_ref_aroma_types.csv```: processed reference document for metadata info on aroma types
    - ```cln_ref_brew_values.csv```: processed reference document for metadata info on brew values
    - ```cln_ref_hops_substitutions.csv```: processed reference document for metadata info on pre-determined hop substitutions
<br/> <br/> <br/>

3. Execute ```eda_and_summary_visuals.ipynb``` which uses the processed data files from ```clean_data``` to perform exploratory analysis, develop insights into our dataset, and provide summary visualizations that present the data.
<br/> <br/>
The ```images``` directory generated from execution will consist of all the ```png``` output files from our script.
<br/> <br/> <br/>

4. Execute ```region_classifier.ipynb``` to construct two tree-based ensemble models using XG-Boost & Random Forest classification algorithms to classify hop region.
<br/> <br/>
In this script, we attempt to classify geographical regions based on various hop characteristics.
The processed data from ```clean_data``` undergoes further feature-engineering to prepare to be fed into a model that can carry out this task. This script is self-contained and will consist of the resulting confusion matrix from the model predictions.
<br/><br/>
Additionally, a tool was also built to take in input data of various hop characteristics from the user, and execute the classifier model to predict the correct region to which the hop belongs to.
<br/> <br/> <br/>

5. Execute ```purpose_classifier.ipynb``` to construct two tree-based ensemble models using XG-Boost & Random Forest classification algorithms to classify hop purpose.
<br/> <br/>
In this script, we attempt to classify hop purpose (Dual vs Aroma vs Bittering) based on various hop characteristics.
The processed data from ```clean_data``` undergoes further feature-engineering to prepare to be fed into a model that can carry out this task. This script is self-contained and will consist of the resulting confusion matrix from the model predictions.
<br/><br/>
Additionally, a tool was also built to take in input data of various hop characteristics from the user, and execute the classifier model to predict the correct purpose of the hop.
<br/> <br/> <br/>

<p align="right">(<a href="#top">back to top</a>)</p>


## Acknowledgments

* Data source: [https://beermaverick.com/hops/](https://beermaverick.com/hops/)

<p align="right">(<a href="#top">back to top</a>)</p>





<!-- MARKDOWN LINKS & IMAGES -->
[issues-shield]: https://img.shields.io/github/issues/rc-9/Beer_Hops_Analysis.svg?style=for-the-badge
[issues-url]: https://github.com/rc-9/Beer_Hops_Analysis/issues


















