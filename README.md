# oled-pholed-tadf-review

超高效率有机发光二极管（PHOLED 与 TADF）综述论文 + Lean 4 形式化核验骨架。

**English version: [README.en.md](./README.en.md)**

本仓库沉淀「磷光 OLED 与热活化延迟荧光：三态激子回收与超高效率 OLED」课题的
研究内容、结论与可机器核验的形式化命题，按语义化版本持续维护，
并提供中英双语论文与文档。

## 目录结构

```
oled-pholed-tadf-review/
├── paper/
│   ├── OLED_PHOLED_TADF_review.md    # 中文综述
│   └── OLED_PHOLED_TADF_review_en.md # English review
├── OledEfficiency.lean              # Lean 库根模块
├── OledEfficiency/
│   ├── Basic.lean
│   └── Proofs.lean                  # 激子统计 / 效率上限 / 时间线 / EQE 记录
├── lakefile.toml
├── lean-toolchain
├── lake-manifest.json
├── .github/workflows/               # Lean CI
├── CHANGELOG.md
└── README.md / README.en.md
```

## 论文要点

- **激子统计**：电注入复合形成单态 : 三态 = 1 : 3；荧光 OLED 仅利用单态，IQE 上限约 25%；磷光 / TADF 回收三态，IQE 上限 100%（4 倍）。
- **三代材料**：1987 年 Tang & Van Slyke 双层荧光 OLED（EQE ≈ 1%）；1998 年 Baldo 等首个 PHOLED（PtOEP，EQE ≈ 4%）；2001 年近 100% 内磷光效率（EQE ≈ 19%）；2012 年 Adachi 等无金属 TADF（RISC 上转换，EQE > 19%，PLQY > 90%）；后期 TADF EQE ≈ 29.6%。
- **机制**：PHOLED 靠重金属自旋轨道耦合解除三态跃迁禁阻；TADF 靠小 ΔE_ST 与反向系间窜越（RISC）实现无贵金属三态回收。
- **边界**：蓝光寿命、高亮度效率滚降、材料稳定性、出光耦合与长期可靠性仍待解决。
- **奖项潜质**：2026 科睿唯安引文桂冠物理方向 Forrest、Thompson、Adachi，表彰 PHOLED 与 TADF 开创性研究；人选拆分与授奖年份存在不确定性。

## Lean 形式化工程

工具链：`leanprover/lean4:v4.36.0`，仅依赖核心库，**无 Mathlib**。

构建：

```bash
lake build
```

形式化只覆盖论文中**可数值判定**的陈述：

1. 激子自旋统计：单态 1、三态 3、总数 4（`singlet_fraction_one_quarter`）；
2. 效率上限：全激子利用上限为荧光上限 4 倍（`harvested_four_times_fluorescent`）；
3. 发现史年份严格递增（`chronology_ordered`）；
4. 代表性 EQE 记录随代际提升（`eqe_records_ascending`）；
5. 发光材料代际、三态利用标志与 TADF RISC 通路的类型化定义。

> 光物理与材料结论以同行评审文献为准；本工程不把机理解释当作可由算术
> 证明的命题。工程内 `sorry` / `admit` / `axiom` 数量为 0。

## 双语版本管理

- 论文：`paper/OLED_PHOLED_TADF_review.md`（中文）与 `paper/OLED_PHOLED_TADF_review_en.md`（英文）内容对齐；
- 文档：`README.md`（中文）与 `README.en.md`（英文）互相链接；
- 变更日志：`CHANGELOG.md` 同时保留中英两段说明；
- 论文修订时应同步更新两个语言版本，提交信息在 subject 中注明 `docs(zh)` / `docs(en)`。

## 版本维护

- 遵循语义化版本（SemVer）：`MAJOR.MINOR.PATCH`。
- 所有显著变更记录于 [`CHANGELOG.md`](CHANGELOG.md)。
- `main` 为主干分支；论文修订、形式化补充、依赖升级分别提交，提交信息
  采用 Conventional Commits（`feat:` / `docs:` / `fix:` / `chore:` 等）。
- 每个发布基线打 Git tag：`vX.Y.Z`。

## 参考文献

见论文末尾「参考文献」一节。
