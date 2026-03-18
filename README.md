# MYC-PROTAC: AI-Designed Targeted Protein Degrader
 
A computational pipeline for designing stapled peptidomimetic PROTACs that degrade the MYC oncoprotein — one of the most common drivers of human cancer and historically considered "undruggable."
 
---
 
## What This Is
 
MYC drives uncontrolled cell growth in over 70% of cancers. It can't be targeted with conventional drugs because it has no binding pocket. This project uses AI-based protein design to build a molecule that:
 
1. Binds the MYC/MAX dimerization interface
2. Recruits an E3 ubiquitin ligase (Cereblon)
3. Tags MYC for destruction by the cell's own proteasome
 
---
 
## Pipeline Overview
 
```
Surface Fingerprinting (GNN)
        ↓
Generative Backbone Design (RFdiffusion)
        ↓
Sequence Design (ProteinMPNN)
        ↓
Physics Validation (OpenMM MD)
        ↓
Synthesis + Click Chemistry Conjugation
        ↓
Wet Lab Validation (BLI, Western Blot, Confocal)
```
 
---
 
## Current Status
 
| Phase | Description | Status |
|-------|-------------|--------|
| I | Surface fingerprinting + GNN motif prediction | ✅ Done |
| II | RFdiffusion generative design | 🔵 Next |
| III | Molecular dynamics simulation | ⬜ Upcoming |
| IV | Peptide synthesis | ⬜ Months 5–6 |
| V | Wet lab validation | ⬜ Months 7–8 |
 
The GNN reached **87.7% validation accuracy** and identified five fixed interface residues: `A901, A927, A929, A947, A950` on PDB structure `1NKP`.
 
---
 
## Stack
 
- **PyTorch Geometric** — GNN training
- **FreeSASA / MaSIF** — protein surface mesh generation
- **RFdiffusion** — backbone hallucination
- **ProteinMPNN** — sequence design
- **ESMFold** — structure prediction / folding check
- **OpenMM** — molecular dynamics
- **MARTINI 3.0** — coarse-grained membrane simulation
- **Biopython** — PDB handling
- **UCSF ChimeraX** — 3D visualization
 
All GPU-heavy steps run on **Google Colab Pro (A100)**.
 
---
 
## Key Files
 
| File | Description |
|------|-------------|
| `config/pipeline_config.json` | All parameters, motif residues, GNN scores, file paths |
| `checklist/myc_protac_checklist.html` | Interactive progress tracker — open in browser |
| `literature/literature_review.md` | Validation of GNN motif residues against published data |
 
---
 
## Authors
 
Mohammad Khanooni · Abhiram Jetty · Jason Pi
 