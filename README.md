# A Guide to DynamicPATH and Analyzing Change in Indonesia Mangroves
A step-by-step guide to using Aiyin Zhang's DynamicPATCH Python package, and a case study that applies DynamicPATCH to a Land Change Modeling  

## Please review the original [DynamicPATCH](https://github.com/zay1996/DynamicPATCH) repository to read the documentation and view the source code.

## Installation Instructions  
# How to Install DynamicPATCH (for Windows Users)  
1. Install the latest version of [miniconda](https://docs.anaconda.com/miniconda/install/)  
2. Open Windows Powershell and make a new directory called ```dynamicpatch``` We recommend creating the directory in ```C/Users/<yourusername>``` for a simple file structure.  
3. Create a new Conda environment for DynamicPATCH, specifying your Python version:  
   ```
   conda create  --name dynamicpatch python=<your_python_version>  
   ```  
   Note: you can run ```python --version``` to check the current installed version of Python  
5. Initialize the Conda environment:
   ```
   conda init
   ```  
7. Close and reopen powershell to ensure the changes have been made. Navigate back to the dynamicpatch directory  
8. Activate the dynamicpatch conda environment:
   ```
   conda activate dynamicpatch
   ```  
10. Install GDAL in order for DynamicPATCH to function correctly. Inside the dynamicpatch directory:
    ```
    conda install -c conda-forge gdal
    ```  
12. Install the DynamicPatch Python package:
    ```
    pip install git+https://github.com/zay1996/DynamicPATCH
    ```  
14. Clone the DynamicPATCH Github Repository:
    ```
    git clone https://github.com/zay1996/DynamicPATCH .
    ```
