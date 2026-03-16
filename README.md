# STA Power Saving Training Set – VLSI Domain

## Overview

This repository contains a **training dataset** for understanding and applying **power-saving techniques in the Static Timing Analysis (STA) domain** within VLSI (Very Large Scale Integration) design.

The dataset is intended for use as:
- An educational reference for VLSI engineers learning low-power design
- A training corpus for AI/ML models targeting VLSI EDA tool assistance
- A study guide for interviews and certifications in VLSI/chip design

---

## Dataset File

**`sta_power_saving_training_set.csv`**

### Columns

| Column       | Description |
|--------------|-------------|
| `id`         | Unique record identifier |
| `category`   | Topic area (see categories below) |
| `question`   | A question on the concept |
| `answer`     | Detailed answer/explanation |
| `difficulty` | `Beginner`, `Intermediate`, or `Advanced` |
| `tags`       | Comma-separated keywords for filtering/indexing |

### Categories

| Category | Description |
|---|---|
| **Fundamentals** | Core STA and CMOS power concepts |
| **Power Reduction Techniques** | Clock gating, Vt swapping, power gating, operand isolation, DVFS, body bias |
| **STA Timing Analysis for Power** | Corners, OCV/AOCV/POCV, slack-leakage trade-offs, cell sizing |
| **Clock Power** | Clock tree power, CTS, skew, useful skew, multi-cycle paths |
| **Power Domains** | UPF, level shifters, isolation cells, retention registers |
| **Leakage Power** | Subthreshold leakage, gate-oxide leakage, temperature effects, Liberty models |
| **Physical Design and Power** | IR drop, electromigration, wire length effects |
| **Low Power Design Methodologies** | RTL vs gate-level optimization, power-aware synthesis, VCD/SAIF, PrimeTime PX, UPF/CPF |
| **Metrics and Verification** | Power units, budgets, average vs peak power, signoff flow, EDA tools |

---

## Dataset Statistics

| Metric | Value |
|---|---|
| Total records | 50 |
| Beginner questions | 7 |
| Intermediate questions | 26 |
| Advanced questions | 17 |

---

## Key Concepts Covered

### Power Types
- **Dynamic power**: switching activity × capacitance × V² × frequency
- **Static / Leakage power**: subthreshold, gate-oxide, and junction leakage

### Major Power Saving Techniques

1. **Clock Gating** – disable clock to idle registers
2. **Multi-Vt Cell Assignment (Vt Swapping)** – use high-Vt cells on non-critical paths
3. **Operand Isolation** – gate combinational inputs when outputs are unused
4. **Power Gating** – shut off supply to entire idle blocks
5. **DVFS** – scale voltage and frequency with workload
6. **Body Biasing** – reverse body bias in standby to raise Vt and cut leakage
7. **Cell Downsizing** – use smaller cells on high-slack paths
8. **Useful Clock Skew** – relax critical paths via intentional skew

### STA Concepts Critical to Power

- Setup and hold time, slack, critical path
- PVT corners for power and timing sign-off
- OCV / AOCV / POCV derating
- Multi-cycle path (MCP) and false path exceptions
- IR drop back-annotation into timing

---

## How to Use This Dataset

### For Machine Learning / NLP Training
```python
import pandas as pd

df = pd.read_csv('sta_power_saving_training_set.csv')

# Filter by difficulty
advanced = df[df['difficulty'] == 'Advanced']

# Filter by category
clock_power = df[df['category'] == 'Clock Power']

# Create question-answer pairs for fine-tuning
qa_pairs = df[['question', 'answer']].to_dict(orient='records')
```

### For Study / Flashcards
Sort by `difficulty` (Beginner → Intermediate → Advanced) and use `question`/`answer` columns as flashcard fronts and backs.

### For Search / Retrieval
Use the `tags` column to build an inverted index for keyword-based search.

---

## Domain Glossary

| Term | Meaning |
|------|---------|
| STA | Static Timing Analysis |
| VLSI | Very Large Scale Integration |
| CMOS | Complementary Metal-Oxide-Semiconductor |
| Vt | Threshold Voltage |
| HVt | High Threshold Voltage cell |
| LVt | Low Threshold Voltage cell |
| DVFS | Dynamic Voltage and Frequency Scaling |
| OCV | On-Chip Variation |
| AOCV | Advanced / Distance-Based OCV |
| POCV | Parametric OCV |
| UPF | Unified Power Format (IEEE 1801) |
| CPF | Common Power Format (Cadence) |
| VCD | Value Change Dump (simulation activity file) |
| SAIF | Switching Activity Interchange Format |
| SPEF | Standard Parasitic Exchange Format |
| PnR | Place and Route |
| CTS | Clock Tree Synthesis |
| MCP | Multi-Cycle Path |
| IR Drop | Voltage drop across resistance in power grid |
| EM | Electromigration |
| EDA | Electronic Design Automation |

---

## References

- IEEE 1801 – Unified Power Format Standard
- Synopsys PrimeTime User Guide
- Cadence Tempus Timing Signoff Solution
- *Low Power CMOS VLSI Circuit Design* – Kaushik Roy & Sharat Prasad
- *Static Timing Analysis for Nanometer Designs* – J. Bhasker & Rakesh Chadha
