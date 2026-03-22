# Cosmic Rhythm Consistency (CRC) — Web Interface

**Official web platform for the CRC Framework: a physics-driven, instrument-aware transient rejection pipeline for high-precision cosmology.**

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Zenodo](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.19021194-blue)](https://doi.org/10.5281/zenodo.19021194)
[![Notebook](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/zmem-lab/crc/blob/main/notebooks/CRC_Framework_Validation.ipynb)

---

## 🌐 What is CRC?

The **Cosmic Rhythm Consistency (CRC)** framework is a two-stage signal-processing pipeline that identifies and rejects impulsive transients — radio-frequency interference, instrumental artefacts, and astrophysical transients such as Fast Radio Bursts — from Time-Ordered Data (TOD) streams in cosmological surveys.

The central principle is **temporal persistence**: any event whose duration satisfies

$$\Delta t < \tau_{\text{dwell}}$$

is classified as an impulsive transient and rejected. The threshold

$$\tau_{\text{dwell}}$$

is derived directly from the instrument's physical dwell time — the duration for which a sky pixel remains within the telescope beam — rendering the criterion physics-driven and content-agnostic: it does not rely upon spectral, morphological, or source-specific assumptions.

Validated against three survey instruments (BINGO, Simons Observatory, and Rubin/LSST) and empirically tested against the CHIME/FRB First Catalogue (CHIME/FRB Collaboration 2021), the framework achieves greater than 99% rejection efficiency on simulated impulsive transients and 100% rejection of real FRB events in the BINGO frame.

---

## 🖥️ Web Platform

This repository hosts the web interface at [crc.zmem.org](https://crc.zmem.org), which provides:

- **Interactive τ_dwell Calculator** — computes the temporal persistence threshold for any drift-scan or constant-elevation survey instrument, given beam FWHM, declination, and scan speed
- **Rejection Visualiser** — enables inspection of TOD segments, flagged candidates, and IEP tag metadata from the validation pipeline
- **Survey Comparison** — presents a side-by-side view of BINGO, Simons Observatory, and Rubin/LSST rejection boundaries on a logarithmic duration scale

---

## 📓 Scientific Validation Notebook

The full validation pipeline is implemented in a reproducible Jupyter notebook. It comprises the following sections:

| Section | Content |
|---------|---------|
| 1 | Environment setup |
| 2 | Survey selection and instrument parameters |
| 3 | Synthetic sky simulation (lognormal HEALPix, TOD generation) |
| 4 | CRC algorithms: event detection and temporal persistence filter |
| 5 | Output, diagnostics, and manuscript summary |
| 6 | Publication-quality figures |
| 7 | Stage-IV validation (optional; requires external sky maps) |
| 8 | Empirical validation against the CHIME/FRB First Catalogue |

See [`notebooks/`](notebooks/) for the full pipeline, empirical results, and execution instructions.

---

## 🔐 Instrumental Event Provenance (IEP)

Every rejected event generates a cryptographically verifiable **IEP tag** at two levels of detail:

- **Level 1** — lightweight provenance record for all rejections: event identifier, UTC timestamp, rejection criterion, Δt, τ_dwell ratio, and SHA-256 hash of the TOD segment
- **Level 2** — full provenance record for borderline events (Δt/τ_dwell > 1%): instrument parameters, SNR estimate, scan geometry, and ED25519 signature placeholder

IEP tags enable post-hoc cross-matching with public transient catalogues (CHIME/FRB, ASKAP) for the scientific recovery of rejected astrophysical events.

---

## 📄 Licence

This website and its contents are licenced under a [Creative Commons Attribution 4.0 International Licence (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

---

## 📚 Citation

If you use the CRC framework in your research, please cite:

```bibtex
@software{savieira2026crc,
  author    = {Sá Vieira, Alexandre de},
  title     = {Cosmic Rhythm Consistency: A Physics-Driven, Content-Agnostic Transient Rejection Framework for High-Precision Cosmology},
  year      = {2026},
  month     = {March},
  publisher = {Zenodo},
  version   = {1.0.0},
  note      = {Submitted to Cosmic Rhythms Workshop 2026, CBPF, Rio de Janeiro},
  doi       = {10.5281/zenodo.19021194},
  url       = {https://doi.org/10.5281/zenodo.19021194}
}
```

---

*ZMEM Research Initiative | [GitHub](https://github.com/zmem-lab/crc) | [crc.zmem.org](https://crc.zmem.org)*

