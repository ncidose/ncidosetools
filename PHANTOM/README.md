<img width="385" height="129" alt="image" src="https://github.com/user-attachments/assets/6953bc8e-3627-48f9-b930-8c3b35106315" />

## Download

### [DOWNLOAD LINK](https://drive.google.com/drive/folders/1B2cI9eewJzRn5DJMaOGJ1RloNv0blxSF?usp=share_link)

Access to the download link is restricted to users with:
- an approved **Software Transfer Agreement (STA)** for non-commercial research use, or  
- a completed **commercial licensing agreement**.

Unlicensed access or redistribution is not permitted.

---

## Available Resources from the Download Link

### Download Folder Organization

The download folder is organized by **phantom library first**, then by **posture/resolution**, then by **file format**:

- **nci_size/**
  Body size–dependent phantom library:
  - `arm_highres/niigz`
  - `arm_lowres/{bin, niigz}`
  - `armless_highres/niigz`
  - `armless_lowres/{bin, niigz}`
  - `armless_xylow_zhigh/niigz` — xy-plane at low resolution, z-axis at high resolution

- **nci_reference/**
  Reference-size phantom library:
  - `arm_highres/{bin, niigz, mc-input}`
  - `armless_highres/{bin, dicomrt}`

- **nci_pregnant/**
  Pregnant woman phantom library:
  - `arm_highres/{niigz, dicomrt}`

- **icrp_reference/**
  ICRP reference phantom library:
  - `armless_highres/{dicomrt, mc-input}`

- **_mastertable_ref&size.xlsx**
  Master data table for the NCI reference and body size–dependent phantom library.

Within each posture/resolution folder, the following format subfolders may appear:

- **bin/** — legacy raw binary voxel files, retained for compatibility with existing workflows
- **niigz/** — compressed NIfTI (`.nii.gz`) voxel phantom files (recommended format)
- **dicomrt/** — DICOM-RT datasets (DICOM CT and RT STRUCTURE)
- **mc-input/** — Monte Carlo input files, code-specific. See **Monte Carlo Input Files** below.

### Monte Carlo Input Files

Monte Carlo input folders use code-specific names rather than the voxel-library
naming pattern:

- **nci_reference/arm_highres/mc-input/mcnp-nci-reference-arm/**
  MCNP input decks for the NCI reference-size phantoms with arms. The folder includes
  12 numbered input files (`01`–`12`) and 12 corresponding lattice files (`*.lat`).

- **icrp_reference/armless_highres/mc-input/geant4-icrp-noarm/**
  Geant4 input package for ICRP reference phantoms without arms. The folder includes
  `Ref_noa_icrp_bin_G4.tar.gz`.

These files are provided for established Monte Carlo workflows and may require local
path, source, scoring, compiler, or code-version adjustments before use.

### Folder Naming Convention

The download folder uses a phantom-library folder first, then a posture/resolution
subfolder, then a format subfolder:

**III_SSS/AAA_RRR/format**

- **III_SSS**: phantom library — one of `nci_size`, `nci_reference`, `nci_pregnant`,
  `icrp_reference`
- **AAA_RRR**: arm posture and voxel resolution, e.g. `arm_highres`, `armless_lowres`,
  `armless_xylow_zhigh`
- **format**: one of `bin`, `niigz`, `dicomrt`, `mc-input`

Examples: `nci_size/armless_lowres/niigz`, `nci_reference/arm_highres/bin`,
`icrp_reference/armless_highres/dicomrt`.

Not every posture/resolution folder includes every format — see **Download Folder
Organization** above for what is available per library.

### Available Phantom Libraries

| Institution | Size      | Arm Posture | Format   | Resolution |
|------------|-----------|-------------|----------|------------|
| nci  | reference | arm     | binary | high |
| nci  | reference | armless | binary | high |
| nci  | size-dependent | arm | binary | low |
| nci  | size-dependent | armless | binary | low |
| nci  | reference | arm | niigz | high |
| nci  | size-dependent | arm | niigz | high |
| nci  | size-dependent | arm | niigz | low |
| nci  | size-dependent | armless | niigz | high |
| nci  | size-dependent | armless | niigz | low |
| nci  | size-dependent | armless | niigz | xy-low / z-high |
| nci  | pregnant | arm | niigz | high |
| nci  | reference | arm | mc-input (MCNP) | high |
| icrp | reference | armless | mc-input (Geant4) | high |
| nci  | reference | armless | dicomrt | high |
| nci  | pregnant  | arm | dicomrt | high |
| icrp | reference | armless | dicomrt | high |

NIfTI (`.nii.gz`) is the recommended format for new downloads; raw binary voxel files
are retained under each library's **bin/** folder for compatibility with existing
Monte Carlo workflows.

### Master Table

- **#_mastertable_ref&size.xlsx**
  Master data table for the NCI reference & body size–dependent phantom library

---

## Version History

### 2026-07-01
- Added a new NCI size-dependent armless NIfTI dataset at **xy-low / z-high resolution** (`nci_size/armless_xylow_zhigh/niigz`, **362 phantoms**), voxelized from the source mesh library
- Reorganized the download folder from a format-first layout (`niigz/`, `dicomrt/`, `mc-input/`, `_archive/`) to a **phantom-library-first** layout (`nci_size/`, `nci_reference/`, `nci_pregnant/`, `icrp_reference/`), with format subfolders (`bin`, `niigz`, `dicomrt`, `mc-input`) nested under each posture/resolution folder; the `_archive` folder no longer exists as a separate top-level category
- Unified the smallest neonate phantom identifiers to **00f050005** / **00m050005** across the master table and all size-dependent libraries (previously inconsistently labeled **00f051004** / **00m051004** in some size-dependent tables)
- Corrected a voxel-count error in the **arm_lowres** and **armless_lowres** libraries for phantoms 00f050005/00m050005, where the z-axis voxel count had not been recomputed for low resolution, resulting in an incorrect (doubled) phantom height; both libraries were revoxelized at the correct low-resolution spacing
- Filled in previously missing **bin** files for 00f050005/00m050005 in `nci_size/arm_highres` and `nci_size/arm_lowres`

### 2026-05-31
- Added compressed NIfTI (`.nii.gz`) versions of the NCI reference-size, size-dependent, and pregnant phantom libraries
- Released the following NIfTI datasets through the download folder:
  - NCI reference-size phantoms with arms at high resolution
  - NCI pregnant woman phantoms at high resolution
  - NCI size-dependent phantoms with arms at high resolution
  - NCI size-dependent phantoms with arms at low resolution
  - NCI size-dependent armless phantoms at high resolution
  - NCI size-dependent armless phantoms at low resolution
- The reference-size NIfTI dataset includes **12 phantoms**; the size-dependent NIfTI datasets each include **362 phantoms**; the pregnant NIfTI dataset includes **8 phantoms**
- All NIfTI datasets preserve the voxelized organ-label data from the corresponding phantom library
- Moved legacy binary voxel files to the **_archive** folder for compatibility with existing workflows
- NIfTI (`.nii.gz`) is the recommended format for new downloads because it is smaller, includes header metadata, and can be read directly by common medical-imaging software
- The raw binary file size previously made it impractical to release the full high-resolution NCI size-dependent phantom library (**n = 362**) through Google Drive; compressed NIfTI now makes this release practical

### **2025-12-10 — Official Release**
- Expanded anatomical detail across the NCI reference-size and body size–dependent phantom libraries
- Added refined cardiac substructures, including heart chambers, myocardium, coronary arteries, cardiac valves, and conduction nodes
- Incorporated the full **362-phantom** body size–dependent library, including the 11 small pediatric phantoms added in the 2024-01-27 update
- Unified the reference-size and body size–dependent organ master tables to improve consistency in organ definitions, IDs, and metadata
- Recomputed voxel counts, organ volumes, and organ masses using a standardized workflow
- Updated skeletal dose-response functions for marrow and endosteum dose estimation using the latest ICRP-approved data

### **2024-12-14 — Official Release**
- Released the **362 size-specific phantoms** voxelized at low resolution
- Released DICOM-RT datasets (DICOM CT and RT STRUCTURE) for:
  - ICRP reference pediatric and adult phantoms  
  - UF/NCI pregnant women with fetus phantoms  
  - UF/NCI reference-size phantoms  

### 2024-01-27
- Added 11 phantoms to the size-specific phantom library  
  *(total size-specific library now **n = 362**)*

00f050005.3dm
00f065005.3dm
00m050005.3dm
00m065005.3dm
01f065010.3dm
01f075010.3dm
01f095010.3dm
01m065010.3dm
01m075010.3dm
01m095010.3dm
05f115015.3dm

### **2022-12-14 — Official Release**

### 2022-01-25
- Ovary locations adjusted using measurements from Kelsey et al. (2013)
- Breast locations adjusted using CT images from the NWTS cohort
- Updates applied to both reference-size and body size–dependent phantom libraries

### 2021-12-08
- ICRP reference pediatric and adult phantoms released in DICOM-RT format
- Versions available with and without arms

### 2019-01-01
- Methods developed to convert binary voxel phantoms to DICOM-CT and DICOM-STRUCTURE
- Reference-size and body size–dependent libraries converted

### 2018-11-13
- Gamma value adjusted to 1.0 for the following phantoms:

05f105020
05f105025
05m095020
30f165050
30f165100
30f170080
30m160055
30m160060
30m165080
30m165085
30m165090
30m170055
30m175055
30m175060
30m175070
30m175075
30m175085
30m175090
30m190075

### 2018–2014 (Selected Updates)
- Arm structures separated and revoxelized for armless phantoms
- Skeletal layers (cortical and spongiosa) refined
- Organ overlap issues (ovaries, uterus, colon) corrected
- Body size–dependent phantom library completed in collaboration with the University of Florida

### 2010-01-01
- Reference-size pediatric and adult male and female phantoms (n = 12) completed
- Phantoms released in binary voxel format
