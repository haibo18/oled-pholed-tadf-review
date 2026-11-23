# oled-pholed-tadf-review

Ultra-high-efficiency OLEDs (PHOLED & TADF) review + Lean 4 formalization skeleton.

**中文版：[README.md](./README.md)**

This repository collects the research output, conclusions, and machine-checkable
formalization of "phosphorescent OLEDs and thermally activated delayed fluorescence:
triplet harvesting and ultra-high-efficiency OLEDs", maintained under Semantic
Versioning with bilingual Chinese/English documents.

## Layout

```
oled-pholed-tadf-review/
├── paper/
│   ├── OLED_PHOLED_TADF_review.md    # 中文综述
│   └── OLED_PHOLED_TADF_review_en.md # English review
├── OledEfficiency.lean              # Lean library root
├── OledEfficiency/
│   ├── Basic.lean
│   └── Proofs.lean                  # exciton statistics / efficiency ceiling / timeline / EQE records
├── lakefile.toml
├── lean-toolchain
├── lake-manifest.json
├── .github/workflows/               # Lean CI
├── CHANGELOG.md
└── README.md / README.en.md
```

## Highlights

- **Exciton statistics**: electrical injection forms singlet : triplet = 1 : 3. Fluorescent OLEDs use only singlets (IQE ceiling ≈ 25%); phosphorescent/TADF OLEDs harvest triplets, IQE ceiling 100% (4×).
- **Three material generations**: 1987 Tang & Van Slyke double-layer fluorescent OLED (EQE ≈ 1%); 1998 Baldo et al. first PHOLED (PtOEP, EQE ≈ 4%); 2001 near-100% internal phosphorescence (EQE ≈ 19%); 2012 Adachi et al. metal-free TADF (RISC up-conversion, EQE > 19%, PLQY > 90%); later TADF EQE ≈ 29.6%.
- **Mechanism**: PHOLED uses heavy-metal spin-orbit coupling to lift triplet prohibition; TADF uses small ΔE_ST and reverse intersystem crossing (RISC) for noble-metal-free triplet harvesting.
- **Boundaries**: blue-emitter lifetime, high-brightness efficiency roll-off, material stability, out-coupling, and long-term reliability remain open.
- **Prize case**: 2026 Clarivate Citation Laureates in Physics — Forrest, Thompson, Adachi — for pioneering PHOLED and TADF research; the exact split and award year carry uncertainty.

## Lean formalization

Toolchain: `leanprover/lean4:v4.36.0`, core library only, **no Mathlib**.

Build:

```bash
lake build
```

The formalization only covers **numerically decidable** claims:

1. Exciton spin statistics: singlets 1, triplets 3, total 4 (`singlet_fraction_one_quarter`);
2. Efficiency ceiling: full exciton harvesting is 4× the fluorescent ceiling (`harvested_four_times_fluorescent`);
3. Discovery chronology strictly increasing (`chronology_ordered`);
4. Representative EQE records rise across generations (`eqe_records_ascending`);
5. Typed definitions of emitter generations, triplet-harvest markers, and the TADF RISC pathway.

> Photophysics and materials conclusions are sourced from peer-reviewed
> literature; this project does not treat mechanistic interpretations as
> arithmetically provable. There are **zero** `sorry` / `admit` / `axiom`.

## Bilingual version management

- Papers: `paper/OLED_PHOLED_TADF_review.md` (Chinese) and `paper/OLED_PHOLED_TADF_review_en.md` (English) are kept in sync;
- Docs: `README.md` (Chinese) and `README.en.md` (English) cross-link each other;
- Changelog: `CHANGELOG.md` keeps both Chinese and English paragraphs;
- When revising the paper, update both language versions in the same commit, tagged `docs(zh)` / `docs(en)`.

## Versioning

- Semantic Versioning (`MAJOR.MINOR.PATCH`).
- All notable changes are recorded in [`CHANGELOG.md`](CHANGELOG.md).
- `main` is the trunk; commits use Conventional Commits.
- Each release baseline is tagged `vX.Y.Z`.

## References

See the "References" section at the end of the review papers.
