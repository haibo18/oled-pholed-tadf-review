# Changelog

本仓库所有显著变更均记录于此。格式遵循
[Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/)，
版本号遵循 [Semantic Versioning](https://semver.org/lang/zh-CN/)。

## [0.1.0] - 2026-11-19

### Added

- 综述论文 `paper/OLED_PHOLED_TADF_review.md`：OLED 电致发光基础与激子自旋统计、
  三代发光材料演进（荧光 → PHOLED → TADF）、代表性 EQE 记录、产业影响、
  未决问题与科学奖项潜质评估。
- Lean 4 形式化工程 `OledEfficiency/`（工具链 `leanprover/lean4:v4.36.0`，核心库）：
  - 激子自旋统计 `singletExcitons` / `tripletExcitons` / `totalExcitons` 与
    单态占比命题 `singlet_fraction_one_quarter`；
  - 效率上限基点定义与 4 倍关系命题 `harvested_four_times_fluorescent`、
    `fluorescent_below_harvested`；
  - 发现史年份链 `chronology_ordered`；
  - EQE 记录 `EqeRecord` 与代际提升命题 `eqe_records_ascending`；
  - 材料代际 `EmitterGen`、三态利用标志 `harvestsTriplet`、TADF RISC 通路
    `TadfPathway` / `riscPathway`；
  - 汇总命题 `paper_evidence_summary`。
- GitHub Actions Lean CI（`leanprover/lean-action`）。
- 仓库说明 `README.md` 与本变更日志。

### Verification

- `lake build`：`Build completed successfully`，`errors=0`，`warnings=0`。
- `sorry` / `admit` / `axiom`：0 处。
