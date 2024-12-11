# A Guide to DynamicPATCH and Analyzing Change in Indonesia Mangroves  

A step-by-step guide to using Aiyin Zhang's DynamicPATCH Python package, along with a case study that applies DynamicPATCH to Land Change Modeling.

## Please review the original [DynamicPATCH](https://github.com/zay1996/DynamicPATCH) repository to read the documentation and view the source code.

## Installation Instructions  

### How to Install DynamicPATCH (for Windows Users)

1. Install the latest version of [Miniconda](https://docs.anaconda.com/miniconda/install/).  
2. Open Windows PowerShell and create a new directory called `dynamicpatch`. We recommend creating the directory in `C/Users/<yourusername>` for a simple file structure.  
3. Create a new Conda environment for DynamicPATCH, specifying your Python version:
    ```bash
    conda create --name dynamicpatch python=<your_python_version>
    ```
   *Note: You can run `python --version` to check the currently installed version of Python.*  
5. Initialize the Conda environment:
    ```bash
    conda init
    ```
6. Close and reopen PowerShell to ensure the changes have been made. Navigate back to the `dynamicpatch` directory.  
7. Activate the `dynamicpatch` Conda environment:
    ```bash
    conda activate dynamicpatch
    ```  
8. Install GDAL to ensure DynamicPATCH functions correctly. Inside the `dynamicpatch` directory:
    ```bash
    conda install -c conda-forge gdal
    ```  
9. Install the DynamicPATCH Python package:
    ```bash
    pip install git+https://github.com/zay1996/DynamicPATCH
    ```  
10. Clone the DynamicPATCH GitHub repository:
    ```bash
    git clone https://github.com/zay1996/DynamicPATCH .
    ```

### Important Considerations Before Executing DynamicPATCH  
#### Data Format  
1. The input data for DynamicPATCH should include only presence and absence data for the category of interest. Users should follow best practices in creating a boolean map, in which presence=1 and absence=0. See the example below:  
<p align="left">
  <img src="Muna%20Island%20Case%20Study/images/bool.png" alt="Boolean map of mangrove absence/presence" width="250">
</p>  

2. Any noData values in the extent should be reclassified to a value of -1. In our tests, dynamicPATCH raised errors with a noData value of -9999, which is common in other GIS software.
3. A consistent file naming structure should be followed for each .tif file containing a time point in the analysis. A best practice is to simply name the file in order of year, such as '1990_presence', '2000_presence', '2010_presence'.  

### Running DynamicPATCH (for Windows Users)  
#### Option 1: Using the Graphical User Interface
1. Open Windows Powershell    
2. Change your directory to the `dynamicpatch` folder created in step 2 of the installation instructions:
   ```bash
   cd dynamicpatch
   ```  
4. Change your directory to the ```tests``` folder:
    ```bash
    cd tests
    ```  
5. Run the GUI interface Python script:  
    ```bash
    python interface.py
    ```
<p align="center">
  <img src="Muna%20Island%20Case%20Study/images/gui.png" alt="Muna Island Change" width="500">
</p>  

#### Option 2: Using the Command Line Interface and a Python Interpreter (IDE)  
*We recommend that users download and install the latest version of [Visual Studio Code](https://code.visualstudio.com/download) to successfully run the program and easily view the output.*  
1. 1. Open Windows Powershell    
2. Change your directory to the `dynamicpatch` folder created in step 2 of the installation instructions:
   ```bash
   cd dynamicpatch
   ```  
4. Change your directory to the ```tests``` folder:
    ```bash
    cd tests
    ```  
5. Open the folder in Visual Studio Code (or the Python Interpreter of your choice):  
    ```bash
    python interface.py
    ```
6. In your Interpreter, select the ```command.py``` python file.
<p align="left">
  <img src="Muna%20Island%20Case%20Study/images/cmd.png" alt="Muna Island Change" width="1000">
</p>  

### How to Visualize Output Maps Outside of DynamicPATCH  
DynamicPATCH offers users the ability to export output maps as a .geotiff, which can be opened in a variety of GIS software for visualization or further analysis.  
#### Visualizing in QGIS  
1. The resulting maps of DynamicPATCH for each time interval are stored as individual bands in the .geotiff file. Band 1 stores the first time interval (e.g. 2000-2010), while Band 2 stores the second time interval (e.g. 2010-2020). This pattern continues for the number of time intervals you have. The number of bands corresponds to the number of specified time intervals.  
2. In QGIS, you can create layers for indivudal time intervals by making copies of the file for each time interval, changing the the symbology to unique values, and selecting the corresponding band for each time interval.
3. Note: Ensure that the transparency band is set to "none." by default, QGIS may select a band that interferes with visualization.
4. A custom color palette must be created in order to distinguish between categories defined by DynamicPATCH. You can create this yourself, or use the ```colorramp.clr``` file on our repository to automatically load this palette in QGIS.

<div align="center">
    Number of Transition Patches for Each Transition Type (Top: 4 Connectivity, Bottom: 8 Connectivity)  
<br /> 
<br /> 
  <tr>
    <td><img src="Muna%20Island%20Case%20Study/images/QGIS_1.png" alt="Each band must be a unique value in QGIS" width="500"></td>  
    <td><img src="Muna%20Island%20Case%20Study/images/QGIS_2.png" alt="Example of color ramp to symbolize DynamicPATCH results" width="500"></td>  
    <td><img src="Muna%20Island%20Case%20Study/images/QGIS_3.png" alt="The transparency band in QGIS must be set to None" width="500"></td>  
  </tr>  
  <br />  
  <br /> 

# Case Study: Coastal Mangroves in Indonesia Using DynamicPATCH  
This case study serves as a practical example to using the tools provided in DynamicPATCH, in addition to analysis and interpretations of the package's output.  

## Background  
In the global tropics, including in Indonesia, the expansion of shrimp aquaculture in brackish coastal ponds has led to the loss of essential mangrove ecosystems. Mangroves provide coastal protection, carbon sequestration, and fish nurseries (Eastman et al, 2015). Noting the importance of mangroves, there are many people and organizations slowing the loss of and restoring mangroves.
One such organization is Blue Forests, an Indonesia-based organization dedicated to understanding and restoring watersheds. The organization also relies heavily on mapping to understand coastal ecosystems and target their work. They utilize Clark Labs data to understand where Mangroves used to be, and then target those former sites for restoration. We contacted Blue Forests to see if our research  might support their work and they suggested we focus on Muna Island, which is located in the Southeast Sulawesi province of Indonesia.  

## Study Area: Muna Island, Southeast Sulawesi, Indonesia  
<p align="left">
  <img src="Muna%20Island%20Case%20Study/images/blue_forests.png" alt="Muna Island Change" width="1000">
</p>  
Credit: Map Created by Blue Forests  


## Data  
Our primary dataset is the Clark Labs Aquaculture Land Cover for Indonesia. The dataset includes 5 time points: 1999, 2014, 2018, 2020, and 2022. Each land cover raster is classified into 5 main categories, including Mangrove, Coastal Wetland, Pond Aquaculture, Water, and Other. We have clipped the dataset to Muna Island. We will focus on examining the dynamics of land change for the Mangrove category. 

<table align="center">
  <thead>
    <tr>
      <th><b>Name</b></th>
      <th><b>Source</b></th>
      <th><b>Resolution</b></th>
      <th><b>Type</b></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Aquaculture Land Cover: Indonesia</td>
      <td><a href="https://www.aquaculture.earth/coastal/index.html">Clark Labs</a></td>
      <td>15 meters</td>
      <td>.geotiff</td>
    </tr>
  </tbody>
</table>

<p align="center">
  <img src="Muna%20Island%20Case%20Study/images/muna_island_change.gif" alt="Muna Island Change" width="400">
</p>  

## Workflow  
1. Followed steps from the "Installation Instructions" (see above) to set up DynamicPATCH on our computers.  
2. Downloaded Mangrove data from Clark Labs  
3. Reclassified raw data to show Mangrove presence (1) and absence (0) for all time intervals. NoData values were reclassified to 2.  
4. Clipped the data to the extent of Muna Island
5. Ran DynamicPATCH according to the "Running DynamicPATCH section" (see above)
   
## Output Maps (Using 8-Connectivity)  

<div align="center">
Results of DynamicPATCH - Full Extent (Muna Island) 1999-2014  
<br /> 
<br /> 
  <tr>
    <td><img src="Muna%20Island%20Case%20Study/output/Connectivity%208/1999_2014_con8.png" alt="DynamicPATCH results from 1999 to 2014 using 8-Connectivity" width="400"></td>
    <td><img src="Muna%20Island%20Case%20Study/images/table_90_14.png" alt="2014_2018_con4" width="400"></td>
  </tr>  
  <br />  
  <br /> 
  Results of DynamicPATCH - Full Extent (Muna Island) 2014-2018  
  <br />  
  <br /> 
  <tr>
    <td><img src="Muna%20Island%20Case%20Study/output/Connectivity%208/2014_2018_con8.png" alt="DynamicPATCH results from 2014 to 2018 using 8-Connectivity" width="400"></td>
    <td><img src="Muna%20Island%20Case%20Study/images/table_14_18.png" alt="2020_2022_con4" width="400"></td>
  </tr>
  <br />   
  <br /> 
  Results of DynamicPATCH - Full Extent (Muna Island) 2018-2020  
  <br />
  <br /> 
    <tr>
    <td><img src="Muna%20Island%20Case%20Study/output/Connectivity%208/2018_2020_con8.png" alt="DynamicPATCH results from 2018 to 2020 using 8-Connectivity" width="400"></td>
    <td><img src="Muna%20Island%20Case%20Study/images/table_18_20.png" alt="2020_2022_con4" width="400"></td>
  </tr>
  <br />  
  <br /> 
  Results of DynamicPATCH - Full Extent (Muna Island) 2020-2022  
  <br />
  <br /> 
    <tr>
    <td><img src="Muna%20Island%20Case%20Study/output/Connectivity%208/2020_2022_con8.png" alt="DynamicPATCH results from 2020 to 2022 using 8-Connectivity" width="400"></td>
    <td><img src="Muna%20Island%20Case%20Study/images/table_20_22.png" alt="2020_2022_con4" width="400"></td>
  </tr>
  <br />
  <br /> 

## Output Graphs

<div align="center">
    Number of Transition Patches for Each Transition Type (Top: 4 Connectivity, Bottom: 8 Connectivity)  
<br /> 
<br /> 
  <tr>
    <td><img src="Muna%20Island%20Case%20Study/Graphs/con_4_num_patch.png" alt="Number of Transition Patches for Each Transition Type (4 Connectivity)" width="500"></td>
    <td><img src="Muna%20Island%20Case%20Study/Graphs/con_8_num_patch.png" alt="Number of Transition Patches for Each Transition Type (8 Connectivity)" width="500"></td>
  </tr>  
  <br />  
  <br /> 
  Distribution of Transition Patch Sizes (Top: 4 Connectivity, Bottom: 8 Connectivity) 
  <br />  
  <br /> 
  <tr>
    <td><img src="Muna%20Island%20Case%20Study/Graphs/con_4_dist_patch.png" alt="Distribution of Transition Patch Sizes (4 Connectivity)" width="500"></td> 
      <td><img src="Muna%20Island%20Case%20Study/Graphs/con_8_dist_patch.png" alt="Distribution of Transition Patch Sizes (8 Connectivity)" width="500"></td>
  </tr>
  <br />   
  <br /> 
  Annual Gross Loss and Gross Gain by Transition Types (Top: 4 Connectivity, Bottom: 8 Connectivity) 
  <br />
  <br /> 
    <tr>
    <td><img src="Muna%20Island%20Case%20Study/Graphs/con_4_gross_types.png" alt="Annual Gross Loss and Gross Gain by Transition Types (4 Connectivity)" width="500"></td>
    <td><img src="Muna%20Island%20Case%20Study/Graphs/con_8_gross_types.png" alt="Annual Gross Loss and Gross Gain by Transition Types (8 Connectivity)" width="500"></td>
  </tr>
  <br />  
  <br /> 
  Annual Gross Increase and Decrease in Number of Patches (Top: 4 Connectivity, Bottom: 8 Connectivity) 
  <br />
  <br /> 
    <tr>
    <td><img src="Muna%20Island%20Case%20Study/Graphs/con_4_gross_num_patch.png" alt="Annual Gross Increase and Decrease in Number of Patches (4 Connectivity)" width="500"></td>
    <td><img src="Muna%20Island%20Case%20Study/Graphs/con_8_gross_num_patch.png" alt="Annual Gross Increase and Decrease in Number of Patches (8 Connectivity)" width="500"></td>
  </tr>
  <br />
  <br />
