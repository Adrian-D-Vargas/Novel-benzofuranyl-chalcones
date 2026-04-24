# Computational Studies: Benzofuranyl Chalcones as Antileishmanial Agents

This repository contains the **in silico** component of the research article:

> **"Novel benzofuranyl chalcones with antileishmanial activity: synthesis, structure-activity relationships, and target-oriented computational studies"**

The computational workflow includes molecular docking, molecular dynamics (MD) simulations, and trajectory analysis of chalcone derivatives against the *Leishmania* FAD-dependent reductase (FRD) enzyme.

> **⚠️ Important:** This repository contains **only Jupyter notebooks**. All data files (~8-10 GB) are hosted on **Zenodo** as compressed archives. Download and extract them following the [Quick Start](#-quick-start) instructions below.

---

## 📦 Data Distribution: GitHub vs Zenodo

Due to file size constraints, this project's data is split between **GitHub** (notebooks only) and **Zenodo** (all data files).

### 📁 **GitHub Repository** (this repo)
Minimal repository with code and structure reference:
- ✅ **Jupyter notebooks only** (`1_docking-analysis.ipynb`, `2_md-preparation.ipynb`, `3_md-analysis.ipynb`, `4_md-visualizations.ipynb`)
- ✅ **Documentation** (`README.md`, `LICENSE`)
- ✅ **Experimental data summary** (`results.csv` - biological activity and computational results)

### 🗄️ **Zenodo Repository** 
All data files compressed by directory (~8-10 GB total):

| **Archive File** | **Content Description** | **Compressed** |
|------------------|-------------------------|----------------|
| `docking.tar.xz` | Complete docking workflow: structures, poses, grids, results | ~2.7 MB |
| `md_trajs.tar.xz` | Aligned MD trajectories (15 × 100ns, 1 last 5 frames) + dry topologies | ~3.9 GB |
| `chalcone-13e.tar.xz` | System 13e: solvated topology + MD input files | ~3.1 MB |
| `chalcone-14c.tar.xz` | System 14c: solvated topology + MD input files | ~3.1 MB |
| `chalcone-14l.tar.xz` | System 14l: solvated topology + MD input files | ~3.1 MB |
| `md_initial_structures.tar.xz` | Initial structures for MD preparation | ~1 MB |


**⚠️ Note:** The `md_analysis/` directory is **NOT** in Zenodo - it will be created automatically when you run the analysis notebooks.

**Zenodo DOI:** [10.5281/zenodo.19711992](https://doi.org/10.5281/zenodo.19711992)

---

## ⚡ Quick Start

### **STEP 1: Clone GitHub Repository**

```bash
git clone https://github.com/Adrian-D-Vargas/Novel-benzofuranyl-chalcones.git
cd Novel-benzofuranyl-chalcones
```

### **STEP 2: Download and Extract Zenodo Data**

1. **Visit Zenodo:** DOI: [10.5281/zenodo.19711992](https://doi.org/10.5281/zenodo.19711992)
2. **Download all `.tar.xz` archives** to your repository root
3. **Extract each archive:**

```bash
# Extract all data files (run in repository root)
tar -xf docking.tar.xz
tar -xf md_trajs.tar.xz
tar -xf chalcone-13e.tar.xz
tar -xf chalcone-14c.tar.xz
tar -xf chalcone-14l.tar.xz
tar -xf md_initial_structures.tar.xz

# Verify directory structure
ls -d */
# Expected output: chalcone-13e/ chalcone-14c/ chalcone-14l/ docking/ md_initial_structures/ md_trajs/
```

### **STEP 3: What You Can Run**

**✅ Fully Executable Analyses:**

- `1_docking-analysis.ipynb` - Complete docking workflow and SAR analysis (reference)
- `2_md-preparation.ipynb` - System preparation walkthrough (reference, systems already built)
- `3_md-analysis.ipynb` - **Sections 2-5:** Trajectory analysis
  - RMSD calculations
  - Distance measurements (chalcone-Cys862)
  - Hydrogen bond analysis
  - Native contacts analysis
- `4_md-visualizations.ipynb` - Comprehensive visualization and summary report

**📖 Reference Only** (require full 100 ns production trajectories ~150 GB, not in Zenodo):

- `3_md-analysis.ipynb` - **Section 1:** Trajectory alignment (outputs already in `md_trajs/`)
- `3_md-analysis.ipynb` - **Section 6:** MM-PBSA free energy calculations

---

## 📁 Repository Structure

**After extracting Zenodo files, your directory will contain:**

```
Novel-benzofuranyl-chalcones/
├── 1_docking-analysis.ipynb           # Notebook: Docking analysis
├── 2_md-preparation.ipynb             # Notebook: MD preparation
├── 3_md-analysis.ipynb                # Notebook: Trajectory analysis
├── 4_md-visualizations.ipynb          # Notebook: Visualization & summary
├── results.csv                        # Summary: biological activity + computational results
├── README.md                          # This file
│
├── docking/                           # From docking.tar.xz
│   ├── results.csv                    # Docking results
│   ├── FAD.sdf, FRD-apo_H.mol2        # Structures
│   ├── good.prm, good.as, good_cav1.grd  # rDock files
│   ├── chalcone_preparation/          # Ligand library
│   ├── output_poses/                  # Final docked poses
│   └── output_rDock/                  # Raw rDock outputs
│
├── md_trajs/                          # From md_trajs.tar.xz
│   ├── 13e_rep1.nc ... 13e_rep5.nc    # Aligned trajectories 1 last 5 frames
│   ├── 14c_rep1.nc ... 14c_rep5.nc
│   ├── 14l_rep1.nc ... 14l_rep5.nc
│   ├── FRD-*_dry.pdb                  # Dry PDBs for reference
│   └── FRD-*_dry.parm7/.rst7          # Dry topologies
│
├── chalcone-13e/                      # From chalcone-13e.tar.xz
│   ├── FRD-13e.parm7/.rst7            # Solvated topology
│   ├── min/                           # Minimization inputs
│   ├── eq/                            # Equilibration inputs
│   ├── md1/ ... md5/                  # Production MD inputs
│   └── check_com.sh                   # Utility script
│
├── chalcone-14c/                      # From chalcone-14c.tar.xz
│   └── (same structure as 13e)
│
├── chalcone-14l/                      # From chalcone-14l.tar.xz
│   └── (same structure as 13e)
│
├── md_initial_structures/             # From md_initial_structures.tar.xz
│   ├── FAD.sdf                        # FAD cofactor
│   └── FRD-*_dry.parm7/.rst7          # Initial dry topologies
│
└── md_analysis/                       # Created by notebook 3
    ├── rmsd_distance/                 # RMSD & distance results
    ├── hbonds/                        # H-bond analysis
    └── contacts/                      # Contacts analysis
```

---

## 📓 Notebook Descriptions

### **1_docking-analysis.ipynb**
Complete molecular docking workflow for 34 chalcone derivatives against the FRD enzyme.

**Fully executable** - All analyses can be run with provided data.

**Key functions:**

- Molecular docking using **rDock**
- Energy-IC₅₀ correlation analysis
- Structure-activity relationship visualization
- Statistical analysis (Pearson correlation, regression)

**Inputs:** `docking/results.csv` (docking energies + experimental IC₅₀ data)  
**Outputs:** Correlation plots, statistical tables, top candidate rankings

---

### **2_md-preparation.ipynb**
Step-by-step system preparation for MD simulations using the AMBER suite.

**Purpose:** Reference for reproducibility - systems are already prepared in `chalcone-*/` directories.

**Workflow:**
1. **Structure conversion:** PDB → MOL2 using `antechamber`
2. **Protonation:** pH 7.4 adjustment with `obabel`
3. **Parameterization:** GAFF2 force field assignment (`parmchk2`)
4. **Complex building:** Ligand-protein assembly with `tleap`
5. **HMassRepartition:** Enables 4 fs timestep with `parmed`

**Inputs:** Docked chalcone structures (13e, 14c, 14l) from `docking/output_poses/`  
**Outputs:** Solvated systems in `chalcone-*/` directories (already provided)

---

### **3_md-analysis.ipynb**
Comprehensive trajectory analysis using **cpptraj** (AMBER).

**Executable Sections (use aligned trajectories from `md_trajs/`):**
1. **Section 2 - RMSD calculations:** Ligand structural stability monitoring
2. **Section 3 - Distance measurements:** Ligand–Cys862 distance tracking (key covalent residue)
3. **Section 4 - Hydrogen bonds:** Occupancy and dynamics analysis
4. **Section 5 - Native contacts:** Protein-ligand interaction persistence

**Reference Only (already done or require full trajectories):**
- **Section 1 - Trajectory alignment:** Scripts for centering, solvent removal, backbone alignment
  - Requires raw `chalcone-*/md*/md*.nc` files (~150 GB, not in Zenodo)
  - Outputs already provided in `md_trajs/` (aligned trajectories)
- **Section 6 - MM-PBSA:** Binding free energy calculations
  - Requires raw `chalcone-*/md*/md*.nc` files
  - Script provided for reference/reproducibility

**Inputs:** Aligned trajectories from `md_trajs/` (Sections 2-5) OR raw trajectories from `chalcone-*/md*/` (Sections 1, 6)  
**Outputs:** Analysis data in `md_analysis/` subdirectories

---

### **4_md-visualizations.ipynb**
Comprehensive statistical visualization and summary of MD trajectory analysis.

**Fully executable** - Uses outputs from notebook 3 analyses.

**Section 4.1** - RMSD and Distance Visualization

**Section 4.2** - Contacts and Hydrogen Bonds Heatmaps

**Section 4.3** - Comprehensive Final Summary

---

## ️ Software Requirements

### Molecular Docking
- **rDock** (v2013.1 or later)
- **Open Babel** (v3.1+)

### MD Simulation & Analysis
- **AmberTools** (v22+): `cpptraj`, `tleap`, `parmed`, `antechamber`, `parmchk2`
- **AMBER** (v22): For running MD simulations (optional if only analyzing)

**Key packages:**
- `pandas` (data handling)
- `matplotlib`, `seaborn` (visualization)
- `scipy.stats` (statistical analysis)
- `rdkit` (molecular structure processing)

---

## 🚀 Usage Workflow

### **Standard Workflow (Recommended)**

1. **Clone repository** → Get Jupyter notebooks
   ```bash
   git clone https://github.com/Adrian-D-Vargas/Novel-benzofuranyl-chalcones.git
   cd Novel-benzofuranyl-chalcones
   ```

2. **Download and extract Zenodo data** → See [Quick Start](#-quick-start) for detailed extraction instructions

3. **Run analysis notebooks in order:**
   ```bash
   jupyter notebook
   # Then open and run:
   # 1. 1_docking-analysis.ipynb
   # 2. 2_md-preparation.ipynb (reference/review only)
   # 3. 3_md-analysis.ipynb (Sections 2-5)
   # 4. 4_md-visualizations.ipynb
   ```

### **Advanced: Run MD Simulations from Scratch**

Only if you want to reproduce MD simulations (requires AMBER license + HPC cluster):

1. Extract `chalcone-*.tar.xz` → Get solvated topologies and MD input files
2. Run minimization/equilibration/production → Use AMBER with provided `.in` files
3. Generate aligned trajectories → `3_md-analysis.ipynb` (Section 1)
4. Perform all analyses → `3_md-analysis.ipynb` (Sections 2-6)

**Note:** Raw 100 ns production trajectories (~150 GB) are NOT in Zenodo. Only aligned trajectories for analysis are provided.

---

## � Key Results

### 📊 Experimental and Computational Summary

This study evaluated **35 benzofuranyl chalcones** against *Leishmania mexicana*. The complete dataset is available in [`results.csv`](results.csv).

#### **Top Performing Compounds (Highest Metabolic Inhibition)**

| Compound | Structure Type | IC₅₀ (μM) | Metabolic Inhibition (%) | SI | Docking (kcal/mol) | MM-PBSA (kcal/mol) |
|----------|----------------|-----------|-------------------------|-----|--------------------|-----------------|
| **13e*** | 2-Cl-phenyl | **90.87** | **90.9 ± 0.5** | 462.96 | 13.864 | **-22.27** |
| **14c*** | 3-F-phenyl | **91.15** | **91.2 ± 0.4** | 370.37 | 13.927 | **-16.13** |
| **13h** | 2-NO₂-phenyl | 91.22 | 91.2 ± 0.7 | 344.83 | 8.925 | - |
| **14b** | 2-F-phenyl | 90.36 | 90.4 ± 0.6 | 188.68 | 6.756 | - |
| **14l*** | 3-CF₃-phenyl | **90.82** | **90.8 ± 0.5** | 666.67 | 5.996 | **-15.86** |
| **13d** | 4-F-phenyl | 89.23 | 89.2 ± 0.9 | 149.25 | 7.373 | - |
| **13c** | 3-F-phenyl | 89.69 | 89.7 ± 0.6 | 210.97 | 15.814 | - |
| **13a** | phenyl | 89.31 | 89.3 ± 0.3 | 187.27 | 14.979 | - |
| **14p** | 3,4,5-tri-OMe-phenyl | 89.99 | 90.0 ± 0.3 | 314.47 | 1.403 | - |

**Legend:**  
- **Bold compounds (*)** = Selected for MD simulations  
- **SI** = Selectivity Index (CC₅₀ macrophages / IC₅₀ parasite)  
- **MM-PBSA** = Binding free energy from molecular dynamics (more negative = stronger binding)

---

### 🧬 Molecular Dynamics Simulations

**Selected systems** (3 compounds with highest metabolic inhibition):

| System | IC₅₀ (μM) | Docking Score | MM-PBSA ΔG |
|--------|-----------|---------------|------------|
| **Chalcone 13e** | 90.87 | 13.864 | **-22.27 kcal/mol** |
| **Chalcone 14c** | 91.15 | 13.927 | **-16.13 kcal/mol** |
| **Chalcone 14l** | 90.82 | 5.996 | **-15.86 kcal/mol** |

---


## 📚 Citation

If you use this code or data, please cite:

**Article:** *(to be published)*

**Zenodo Dataset:** DOI: [10.5281/zenodo.19711992](https://doi.org/10.5281/zenodo.19711992)

---

## 📧 Contact

For questions or issues regarding the computational workflow:
- **Email:** adv291882@gmail.com

---

## 📄 License

This project is licensed under the [MIT License](LICENSE) - see the LICENSE file for details.

---

**Last updated:** April 2026

