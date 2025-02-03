# Metabolex-1D

Metabolex-1D is a collection of 1D NMR experiments designed for metabolomics studies. These experiments utilize novel WAter irradiation DEvoid (WADE) pulses to efficiently suppress the water signal while preserving the intensities of exchangeable protons. This capability is especially useful when analyzing biofluids such as urine, plasma, and tissue extracts where traditional water suppression methods may compromise quantitative accuracy.



---

## Files

| File Name                                | Type                  |
| ---------------------------------------- | --------------------- |
| `wade90noesy1d.mpp`                      | Bruker Pulse Sequence |
| `wade180noesy1d_B1.mpp`                  | Bruker Pulse Sequence |
| `wade39997_rf0.0_74.0p1_bw2.8B1.mrf`     | RF Shape              |
| `wade39997_rf0.0_74.0p1_bw2.8B1_neg.mrf` | RF Shape              |
| `p90xb10_rf0.0_17.2p1_bw1.32B1.mrf`      | RF Shape              |
| `wade90_rf0.0_61.1p1_bw3.88B1_neg.mrf`   | RF Shape              |

---

## Experimental Setup

The experimental setup is driven by a Python script that configures a Bruker spectrometer with a set of parameters based on the chosen experiment. Below are the details for two of the setups: **Noesy1D-WADE180** and **Noesy1D-WADE90**.

### 1D NOESY-WADE-180  

- **Pulse Sequence:**  
  Uses the pulse program defined in `wade180noesy1d_B1.mpp`.

- **RF Shapes:**  
  - `p90xb10_rf0.0_17.2p1_bw1.32B1.mrf`  
  - `wade39997_rf0.0_74.0p1_bw2.8B1_neg.mrf`

- **Gradient Settings:**  
  - `gpz1`: 50  
  - `gpz2`: -20  
  - `gpz3`: 87  
  - Gradient shape names set to `SMSQ10.100` for `gpnam1`, `gpnam2`, and `gpnam3`.

- **Delay Parameters and Others:**  
  - `p16`: 1000  
  - `p17`: 500  
  - `p11`: 10000  
  - RF pulse shape `spnam1`: `Sinc1.1000`  
  - p62 is set as 50 µs (users are advised to adjust this delay to 100 µs or 150 µs when peaks near the water signal need to be better resolved).

- **Additional Setup Commands:**  
  The script also sets the calibrated 1H pulse width and power level using user inputs, applies receiver gain settings, and resets parameters using commands like `rpar P3919GP all` before executing the sequence.

### 1D NOESY-WADE-90

- **Pulse Sequence:**  
  Uses the pulse program defined in `wade90noesy1d.mpp`.

- **RF Shapes:**  
  - `p90xb10_rf0.0_17.2p1_bw1.32B1.mrf`  
  - `wade90_rf0.0_61.1p1_bw3.88B1_neg.mrf`

- **Gradient Settings:**  
  - `gpz1`: 34  
  - `gpz2`: 11  
  - `gpz3`: 25  
  - Gradient shape names set to `SMSQ10.100` for `gpnam1`, `gpnam2`, and `gpnam3`.

- **Delay Parameters and Others:**  
  - `p16`: 1000  
  - `p17`: 2500  
  - `p11`: 10000  
  - RF pulse shape `spnam1`: `Sinc1.1000`  
  - p62 is set as 50 µs (users are advised to adjust this delay to 100 µs or 150 µs when peaks near the water signal need to be better resolved).
  - **Note:** A broader water peak in this setup might result in digital overflow; it is recommended to consider reducing `p11` (for example, to 3 ms) if such issues arise.



---
#### Copyright & License Statement

RF pulse shapes are copyrighted by Regents of the University of Minnesota and the software for generating RF shapes covered by US patent 11,221,384. Regents of the University of Minnesota will license the use of RF shapes solely for educational and research purposes by non-profit institutions and government agencies only. For other proposed uses, contact umotc@umn.edu. The software may not be sold or redistributed without prior approval. One may make copies of the software for their use provided that the copies, are not sold or distributed, are used under the same terms and conditions. As unestablished research software, this code is provided on an "as is'' basis without warranty of any kind, either expressed or implied. The downloading, or executing any part of this software constitutes an implicit agreement to these terms. These terms and conditions are subject to change at any time without prior notice.



