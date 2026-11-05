# Effect of Crystallite Size on the XRD Pattern of Hydroxyapatite

A computational study using Python (pymatgen), VESTA and the Scherrer equation.

## Purpose
To show how crystallite size changes what XRD measures, using hydroxyapatite (HA), a bioceramic used for implant coatings (relevant to AMASE Track 5: Bio/Nanomaterials).

## What I did
1. **Structure:** took the HA structure from the Crystallography Open Database (COD 1011242, Hendricks et al., 1932; space group P6_3/m, a = b = 9.4 Å, c = 6.93 Å) and visualised it in VESTA (`HA_structure.png`).
2. **Simulated XRD:** computed the Cu Kα pattern with pymatgen (`fig2_simulated_XRD.png`). Strongest peak at 31.82°.
3. **Size effect:** broadened the peaks with the Scherrer relation (K = 0.9, instrument width 0.10°) for different sizes (`fig3_size_effect.png`).
4. **Scherrer test:** fitted the (002) peak (25.71°) and recovered the crystallite size (`fig4_scherrer_test.png`, `scherrer_results.csv`).

## Results
| True size (nm) | FWHM (°) | Estimated (nm) | Error (%) |
|---|---|---|---|
| 5 | 1.553 | 5.3 | +5.2 |
| 10 | 0.867 | 9.5 | -5.4 |
| 20 | 0.490 | 17.0 | -15.0 |
| 50 | 0.193 | 49.4 | -1.3 |
| 100 | 0.128 | 102.8 | +2.8 |
| 200 | 0.107 | 213.5 | +6.8 |

The method recovers the size well overall, but the error is largest at 20 nm.

## Limitations
- The peak widths were generated with the Scherrer formula itself, so the test shows the effects of peak overlap, instrument broadening, noise and the fitting window, not whether Scherrer physics is correct.
- The CIF is old (1932): low-precision lattice values and no hydrogen positions (negligible for XRD, but the structure is simplified).
- Strain and crystal shape are not included.

## Tools
Python, Google Colab, pymatgen, numpy, scipy, matplotlib, VESTA, Crystallography Open Database.

## Files
`1011242.cif`, `HA_structure.png`, `fig2_simulated_XRD.png`, `fig3_size_effect.png`, `fig4_scherrer_test.png`, `scherrer_results.csv`, notebook (`.ipynb`).
