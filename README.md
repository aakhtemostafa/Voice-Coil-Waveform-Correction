# Voice Coil Waveform Correction

This repository contains a **Jupyter Notebook workflow** for generating, measuring, and iteratively correcting **voice coil waveforms** using the **Moku:Go Arbitrary Waveform Generator (AWG)** and **Oscilloscope**.

The notebook automates:
- Uploading initial or compensator waveforms to the AWG.
- Acquiring responses from the Oscilloscope.
- Normalizing, analyzing, and smoothing voltage signals.
- Iteratively generating compensators to correct distortions.
- Visualizing responses and compensators across iterations.

---

## Hardware

- [Moku:Go](https://apis.liquidinstruments.com/api/getting-started/starting-python.html) with:  
  - Arbitrary Waveform Generator (AWG)  
  - Oscilloscope  
- Voice coil setup  
- Position sensing detector assembly

---

## Setup Diagram

```
    ┌──────────────┐
    │  Moku:Go AWG │
    └──────┬───────┘
           │  (Drive Signal)
           ▼
    ┌──────────────┐
    │  Voice Coil  │
    └──────┬───────┘
           │  (Motion)
           ▼
    ┌────────────────────┐
    │   Position Sensor  │
    └──────┬─────────────┘
           │  (Feedback Signal)
           ▼
    ┌──────────────┐
    │ Moku:Go Scope│
    └──────┬───────┘
           │  (Processed Residuals / Compensation)
           └───────────────►
                   │
                   ▼
           ┌──────────────┐
           │  Moku:Go AWG │
           └──────────────┘
```

---

## Requirements

### Software  
Install Python dependencies:

```bash
pip install pandas numpy matplotlib scipy statsmodels moku
```

### Files  
- `initial_linear_waveform.txt` → starting waveform.  
- `Voice coil Waveform correction_MukoGo_automated.ipynb` → main notebook.

---

## Usage

1. Clone this repository:

   ```bash
   git clone https://github.com/<your-username>/voice-coil-waveform-correction.git
   cd voice-coil-waveform-correction
   ```

2. Place the `initial_linear_waveform.txt` in the project root.

3. Launch JupyterLab or Jupyter Notebook:

   ```bash
   jupyter lab
   ```

4. Open and run:

   ```
   Voice coil Waveform correction_MukoGo_automated.ipynb
   ```

5. Follow the iterative process in the notebook. Each iteration:
   - Sends a waveform to AWG.
   - Records the response from Oscilloscope.
   - Computes residuals and generates a new compensator.
   - Saves results as `.txt` files.

---

## Output

- `VC_respons#.txt` → measured responses.  
- `Compensator_it_#_#.txt` → generated compensators.  
- Plots embedded in the notebook.


---

## Citation

If you use this code in a publication or presentation, please cite:

> Aakhte, M., et al. (2025). *Isotropic, aberration-corrected light sheet microscopy for rapid high-resolution imaging of cleared tissue.* bioRxiv. https://doi.org/10.1101/2025.02.21.639411v2

---

## License

MIT License – free to use and modify.  
