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
5. Open the folder in Visual Studio Code (or the Python IDE of your choice):  
    ```bash
    python interface.py
    ```
