# ⚡ GDI vs CMOS Master-Slave D Flip-Flop @ 16nm

A full-custom IC design study comparing a **12-transistor GDI-based master-slave D flip-flop** against a conventional **24-transistor CMOS** implementation in 16nm CMOS technology at 0.7V. Both designs are implemented at schematic and layout level, with post-layout simulation and DRC/LVS verification.

## 📄 Paper

> *"A 12-Transistor GDI-Based Master-Slave D Flip-Flop with Diffusion-Sharing Layout Optimization in 16nm CMOS for Ultra-Low-Power Digital Systems"*
> — see [`docs/paper.pdf`](docs/paper.pdf)

## 🗂️ Project Structure

```
gdi-cmos-dff-16nm/
├── design/
│   ├── cmos/
│   │   └── dff_cmos.jelib     # CMOS DFF — schematic + layout (Electric VLSI)
│   └── gdi/
│       └── dff_gdi.jelib      # GDI DFF — schematic + layout (Electric VLSI)
├── models/
│   └── ptm_16nm.txt           # PTM 16nm NMOS/PMOS SPICE models (Vdd = 0.7V)
└── docs/
    └── paper.pdf              # Full design paper with results & analysis
```

## 🔬 What Was Done

### Two flip-flop implementations, compared head-to-head:

**CMOS Design** — conventional master-slave DFF using complementary logic
- 24 transistors (22 functional + 2 for CLK generation)
- Full voltage swing, high noise margins
- Requires complementary clock (CLK and CLK̄)

**GDI Design** — Gate Diffusion Input based master-slave DFF
- 12 transistors: two GDI 2:1 MUXes + two CMOS inverters
- Single-clock operation (no CLK̄ needed)
- Two layout versions explored: naïve and diffusion-sharing optimized


## 📊 Key Results

| Metric | CMOS | GDI | Improvement |
|---|---|---|---|
| Transistor Count | 24 | 12 | **50% fewer** |
| Power (schematic) | 275 nW | 53.7 nW | **80.5% lower** |
| Propagation Delay | 395 ps | 131 ps | **66.8% faster** |
| Layout Area | 1440.4 fm² | 563.82 fm² | **60.9% smaller** |

> Post-layout results (after parasitic extraction): GDI — 65.5 nW, 211 ps delay.

### GDI Layout Optimization
The GDI layout was developed in two versions to validate the diffusion-sharing technique:
- **Naïve layout**: 1470.1 fm² — no diffusion sharing
- **Optimized layout**: 563.82 fm² — diffusion sharing between adjacent transistors, shared power rails, 6-metal-layer routing strategy (odd layers vertical, even horizontal)

## 🛠️ Tools & Technology

| Tool / Spec | Details |
|---|---|
| Design Tool | Electric VLSI Design System |
| Technology | 16nm PTM (Predictive Technology Model) |
| Supply Voltage | 0.7 V |
| SPICE Models | PTM High-K / Metal Gate / Strained-Si |


## 👥 Done by:

- Joud Thaher
- Layan Salem
- Labiba Sharia
