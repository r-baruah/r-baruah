<div align="center">

  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/banner-dark-v2.svg">
    <source media="(prefers-color-scheme: light)" srcset="assets/banner-light.svg">
    <img alt="Ripuranjan Baruah — Founder, Researcher" src="assets/banner-dark-v2.svg" width="100%">
  </picture>

</div>

Following curiosity and figuring things out by building. Right now, that's split between space applications, bootstrapping a chess platform, and exploring hard, unconventional problems.

---

## Research

### FERRITE — Lossless Image Compression for Space Missions

> **Accepted for Oral Presentation at ADASS 2026 (Perth)**  
> *Astronomical Data Analysis Software and Systems XXXVI*

Space telescopes generate ~16.8 MB of 16-bit integer data per exposure, but downlink contact windows last only minutes. CFITSIO's fpack (the NASA community standard) streams data as a single continuous bitstream, where a single bit-flip desynchronizes the Rice decoder and destroys the remainder of the frame.

FERRITE partitions frames into autonomous 64×64 pixel tiles, each protected by its own CRC-16 integrity tag. A bit error isolates strictly to that tile while the rest of the frame decodes cleanly. The entire pipeline uses integer-only arithmetic (Newton-Raphson integer square root, binary de Bruijn log₂) with zero floating-point operations, built specifically for radiation-hardened flight processors without FPUs like the RAD750 and LEON3.

Tested against real Hubble Space Telescope (HST WFC3/UVIS) science frames, FERRITE compresses tighter than NASA's fpack (2.425× vs 2.410×) while surviving channel noise that destroys continuous streams.

<details>
<summary><b>Benchmark Results (HST WFC3/UVIS calibrated science vs NASA fpack)</b></summary>
<br>

| Metric | FERRITE v2.0 | NASA fpack (lossless) | Margin / Result |
|---|---|---|---|
| **Mean compression ratio (HST WFC3)** | **2.425×** | 2.410× | **FERRITE +0.015×** |
| **Science data survival @ BER 10⁻⁶** | **98.44%** | 0.00% (Total desync) | **+98.44%** |
| **Science data survival @ BER 10⁻⁵** | **70.31%** | 0.00% (Total desync) | **+70.31%** |
| **Lost-to-framing errors** | **0 across all regimes** | Complete frame loss | Single-tile blast radius ($\le 1$) |
| **Encode / decode throughput** | **156.9 / 291.7 MB/s** | Single-threaded | Multi-core OpenMP engine |
| **Photometric completeness** | **99.95%** | 100% (when uncorrupted) | 0.0000 ADU residual bias |

*fpack survival is zero by construction in noisy channels: it compresses the frame as one continuous bitstream without per-tile resynchronization, so a single bit-flip permanently desynchronizes the Rice decoder.*

</details>

*Paper accepted for oral presentation at ADASS 2026 (Perth). Code and benchmark harness will release under GPL alongside the conference proceedings.*

---

## Ventures

### [Gambits.in](https://gambits.in) — Chess Training Platform

*Turns recurring match blunders into a 15-minute daily training routine (1000–2200 Elo).*

Most online chess players hit a multi-year rating plateau from unstructured blitz games and random puzzle grinding. Gambits connects to Lichess and Chess.com match histories, isolates recurring tactical blind spots, and generates a structured daily training regimen using spaced repetition and sparring drills.

Bootstrapped, small team. Beta launching soon.

---

## Explorations & Systems

### [HeapGlass](https://github.com/r-baruah/HeapGlass) — Live Memory Diagnostics

*Watch a running program's heap, catch a leak or a double-free as it happens.*

HeapGlass attaches to a C or C++ program with an `LD_PRELOAD` interceptor, tracks every allocation and free, and renders them live to a 256×256 grid (65,536 cells). Leaks show up as regions that deepen toward red as blocks age, and a double-free flashes on the grid instead of crashing the target.

<details>
<summary><b>Measured numbers</b></summary>
<br>

*"Ghost window" = the trailing span of wall-clock time a freed block stays visible before aging off the grid.*

| Measurement | Value |
|---|---|
| Interceptor overhead (1 Hz live ticker, demo workload) | 1.23% |
| `demo_leaky` @ 30 MB/s, killed at 4 s | 42,817 allocs · 212.6 MB live · Ghost window 4.2 s |
| `demo_leaky` @ 25 MB/s, killed at 3 s | 26,834 allocs · 133.1 MB live · Ghost window 3.1 s |
| `demo_fixed`, clean 45 s run | 326,292 allocs · 7.2 MB plateau (1,200 blocks) · Ghost window 45.1 s |
| Relay self-test (`--smoke`) | exit 0, grid locked, 6 offenders caught |
| Grid geometry | 256×256 cells, 16 MiB min span, 8 GiB default ceiling |

</details>

---

### [Kepler-64](https://github.com/r-baruah/kepler-64) `[the absurd one]` — Differentiable Astrophysical Chess Engine

*What happens when chess positions are evaluated by continuous gravitational physics instead of heuristics? · [Live Observatory](https://r-baruah.github.io/kepler-64/)*

Kepler-64 replaces conventional piece-square evaluation tables with continuous gravitational physics. The board is a 2D discrete spacetime lattice where pieces act as point masses. Position evaluation computes Plummer gravitational potential fields, King tidal Hessian stress tensors, and astronomical Roche disruption limits. Physical constants (G, softening length, speed of light, Roche threshold) are differentiable leaves in JAX, trained against Grandmaster games via gradient descent. Captured pieces transfer 80% of their mass to their captor, creating localized supermassive pieces that warp board gravity. The whole thing ships with a custom 60 FPS Canvas observatory rendering real-time potential streamlines, force vectors, and move rankings.

It plays weak chess. That was never the point.

---

### Other Explorations

- **[Exo-Checkmate](https://github.com/N-Body-Labs/Exo-Checkmate)** (`Python`, `PyTorch`) — Screening exoplanet candidates using orbital stability physics and telescope transit light curves. Hosted under [N-Body Labs](https://github.com/N-Body-Labs).
- **[SENTRY](https://github.com/r-baruah/SENTRY)** (`Solidity`, `TypeScript`) — Adversarial exploit verification sandbox for smart contracts (Hack Space 2025 winner).
- **[Pyre Engine](https://github.com/Open-Source-Chandigarh/pyre)** (`C++17`, `OpenGL 4.5`) — Real-time graphics rendering architecture and viewport pipeline.

---

## Publications & Recognition

- **ADASS 2026** (Perth, Australia) — *Accepted for Oral Presentation:* **"FERRITE: A Fault-Error Resilient Rice Integer Tile Encoder for Orbital Science Imaging"** (To appear in *ASP Conference Series*).
- **Hack Space 2025** — Winner, Blockchain Track ([SENTRY](https://github.com/r-baruah/SENTRY)).

---

## Interests

- **Chess** — [1800+ Blitz on Lichess](https://lichess.org/@/Ripu01). The only domain where I trust intuition over computation.
- **Guitar** — Committed enough to own one, not enough to fix the missing E string.

---

<div align="center">

Open to research collaborations and hard problems.

[Email](mailto:ripuranjanbaruah@zohomail.in) · [Gambits.in](https://gambits.in) · [Lichess](https://lichess.org/@/Ripu01) · [Codeforces](https://codeforces.com/profile/R_Baruah) · [N-Body Labs](https://github.com/N-Body-Labs)

</div>
