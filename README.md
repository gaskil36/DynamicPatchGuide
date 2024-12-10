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
1. The input data for DynamicPATCH should include only presence and absence data for the category of interest. Users should follow best practices in creating a boolean map, in which presence=1 and absence=0
2. Any noData values in the extent should be reclassified to a value of -1. In our tests, dynamicPATCH raised errors with a noData value of -9999, which is common in other GIS software.
3. A consistent file naming structure should be followed for each .tif file containing a time point in the analysis. A best practice is to simply name the file in order of year, such as '1990_presence', '2000_presence', '2010_presence'.  

### How to Run DynamicPATCH (for Windows Users)  
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

# Case Study: Coastal Mangroves in Indonesia Using DynamicPATCH  
This case study serves as a practical example to using the tools provided in DynamicPATCH, in addition to analysis and interpretations of the package's output.  

## Background  
In the global tropics, including in Indonesia, the expansion of shrimp aquaculture in brackish coastal ponds has led to the loss of essential mangrove ecosystems. Mangroves provide coastal protection, carbon sequestration, and fish nurseries (Eastman et al, 2015). Noting the importance of mangroves, there are many people and organizations slowing the loss of and restoring mangroves.
One such organization is Blue Forests, an Indonesia-based organization dedicated to understanding and restoring watersheds. The organization also relies heavily on mapping to understand coastal ecosystems and target their work. We contacted Blue Forests to see if our research  might support their work and they suggested we focus on Muna Island, which is located in the Southeast Sulawesi province of Indonesia.  

## Data
[Visual Studio Code](Muna%20Island%20Case%20Study/images/muna_island_change.gif)


Our primary dataset is the Clark Labs Aquaculture Land Cover for Indonesia. The dataset includes 5 time points: 1999, 2014, 2018, 2020, and 2022. Each land cover raster is classified into 5 main categories, including Mangrove, Coastal Wetland, Pond Aquaculture, Water, and Other. We have clipped the dataset to Muna Island. We will focus on examining the dynamics of land change for the Mangrove category. 





<div style="width:100%; text-align:center;">
  <table style="margin:auto;">
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
</div>

<div style="text-align:center;">
  <img src="Muna%20Island%20Case%20Study/images/muna_island_change.gif" alt="Muna Island Change" width="400">
</div>


