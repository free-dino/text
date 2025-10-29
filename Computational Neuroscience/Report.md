### 1. The DICOM to BIDS tool
This tool provides a graphical interface for converting DICOM datasets into the BIDS format. It is built in Python with `dcm2bids` as the backend conversion utility, and integrates with `Gooey` for a user-friendly GUI. The final program can be packaged as a standalone application using `PyInstaller`.
![[Pasted image 20250910230303.png]]
#### Key Features
- Graphical User Interface (GUI):  
    Implemented with `Gooey`, so users can select input/output folders and processing modes without using the command line.
- Two Processing Modes:
    1. Raw DICOM to BIDS: Takes a DICOM folder and converts it directly into BIDS.
    2. Excel to BIDS: Uses an Excel mapping file to control how DICOM data is organized in BIDS.
- Temporary File Cleanup:  
    After conversion, the tool automatically deletes any temporary folders (e.g., `tmp*`) in the output directory to keep the dataset clean.
- Error Handling:
    - Detects whether the user selected the correct input type (folder vs. file).
    - Provides informative error messages for missing or invalid inputs.
    - Catches unexpected errors and reports them gracefully.
- Standalone Application:  
    With `PyInstaller`, the program can be distributed as an executable (`.exe` or binary) without requiring users to install Python or dependencies.
#### **How It Works**
1. **User selects inputs via GUI**
    - Input DICOM folder (or Excel file).
    - Output BIDS folder.
    - Processing mode (Raw or Excel).
2. **Conversion Process**
    - Calls `run_dicom_to_bids()` if raw mode is chosen.
    - Calls `run_excel_dir()` if Excel mode is chosen.
    - Runs `dcm2bids` internally to perform the actual DICOM → NIfTI + JSON conversion.
3. **Post-processing**
    - Cleans up temporary folders.
    - Outputs a validated BIDS dataset ready for research pipelines.
### 2. The Data Received in the Hospital and Problems We’re Facing
1. Label heterogeneity: Different MRI scanners (brands and models) use inconsistent labeling conventions in the DICOM metadata, making automated mapping to BIDS challenging.
2. Spinal cord mislabeled as brain: Some spinal cord scans are stored in DICOM as if they were brain scans, and current simple algorithms cannot confidently distinguish between them.
3. Diffusion MRI inconsistencies: Certain diffusion scans have incorrect or inconsistent `b-value` labels (e.g., scans labeled _b1000_ and _b100_ appearing as separate series instead of one diffusion sequence with multiple `b-values` and `b-vectors`). This causes confusion when converting to BIDS format.

