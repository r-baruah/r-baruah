<div align="center">

  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/banner-dark-v2.svg">
    <source media="(prefers-color-scheme: light)" srcset="assets/banner-light.svg">
    <img alt="Ripuranjan Baruah — Founder, Researcher" src="assets/banner-dark-v2.svg" width="100%">
  </picture>

</div>

I build things that keep working after something breaks.

> Everything I ship is developed and benchmarked on a **Ryzen 5 5500U (6C/12T) with 8 GB RAM**. If it can't hold up under tight memory and real-world failure conditions, it isn't finished.

---

## Research

### FERRITE — Lossless Image Compression for Space Missions

<details open>
<summary><i>High-reliability data compression designed for orbital telescope downlinks.</i></summary>
<br>

Space telescopes generate ~16.8 MB of 16-bit integer data per exposure, but downlink contact windows last only minutes. Standard Rice compressors (such as CFITSIO's fpack) stream data as a single continuous bitstream, where a single bit-flip desynchronizes the decoder and destroys the remainder of the frame.

FERRITE partitions frames into autonomous 64×64 pixel tiles, each protected by its own CRC-16 integrity tag. A bit error isolates to that tile while the remaining frame decodes cleanly. The entire pipeline uses integer arithmetic (Newton-Raphson integer square root, binary de Bruijn log₂) with zero floating-point operations, built for radiation-hardened flight processors without FPUs like the RAD750 and LEON3.

<details>
<summary><b>Benchmark Results (HST WFC3/UVIS vs fpack)</b></summary>
<br>

| Metric | FERRITE | fpack (lossless) |
|---|---|---|
| Mean compression ratio | **2.40×** | 2.41× (within 0.4%) |
| Science data survival @ BER 10⁻⁶ | **98.4%** | ≈ 0% |
| Science data survival @ BER 10⁻⁵ | **70.3%** | ≈ 0% |
| Encode / decode throughput | **75 / 203 MB/s** (OpenMP, 50-trial mean) | — |

*fpack survival is effectively zero by construction: it compresses the frame as one continuous bitstream with no per-tile resync, so a single bit error desynchronizes the decoder and every subsequent pixel is lost.*

</details>

*Abstract submitted to [ADASS 2026](https://pretalx.adass.org/adass2026/talk/review/QMW3EATPQ77FNS7YX3C7ZV7S7AYJBHUJ) (Perth), in review. Code releases publicly under GPL upon paper acceptance.*

</details>

<br>

### [HeapGlass](https://github.com/r-baruah/HeapGlass) — Live Memory Diagnostics

<details open>
<summary><i>Watch a running program's heap, catch a leak or a double-free as it happens.</i></summary>
<br>

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

</details>

---

### [Kepler-64](https://github.com/r-baruah/kepler-64) — Differentiable Astrophysical Chess Engine

<details open>
<summary><i>The absurd one: what happens when chess positions are evaluated by gravitational physics instead of heuristics?</i> · <a href="https://r-baruah.github.io/kepler-64/">Live Observatory</a></summary>
<br>

Kepler-64 replaces conventional piece-square evaluation tables with continuous gravitational physics. The board is a 2D discrete spacetime lattice where pieces act as point masses. Position evaluation computes Plummer gravitational potential fields, King tidal Hessian stress tensors, and astronomical Roche disruption limits. Physical constants (G, softening length, speed of light, Roche threshold) are differentiable leaves in JAX, trained against Grandmaster games via gradient descent. Captured pieces transfer 80% of their mass to their captor, creating localized supermassive pieces that warp board gravity. The whole thing ships with a custom 60 FPS Canvas observatory rendering real-time potential streamlines, force vectors, and move rankings.

It plays weak chess. That was never the point.

</details>

---

## Ventures

### [Gambits.in](https://gambits.in) — Chess Training Platform

<details open>
<summary><i>Automated blunder diagnosis and deliberate practice for competitive players (1000–2200 Elo).</i></summary>
<br>

Most online chess players hit a multi-year rating plateau from unstructured blitz games and random puzzle grinding. Gambits connects to Lichess and Chess.com match histories, isolates recurring tactical blind spots, and generates a structured 15–30 minute daily training regimen using spaced repetition and sparring drills.

Bootstrapped, small team. MVP shipping soon.

</details>

---

## Selected Projects

- **[SENTRY](https://github.com/r-baruah/SENTRY)** (`Foundry`, `Solidity`, `TypeScript`) — Test harness verifying smart contract exploit hypotheses in an isolated sandbox. Winner of Hack Space 2025 (Blockchain Track).
- **[Exo-Checkmate](https://github.com/N-Body-Labs/Exo-Checkmate)** (`Python`, `PyTorch`, `SciPy`) — Physics-informed exoplanet candidate screening using Hill stability criteria and quadratic limb darkening. Hosted under [N-Body Labs](https://github.com/N-Body-Labs).
- **[Pyre Engine](https://github.com/Open-Source-Chandigarh/pyre)** (`C++17`, `OpenGL 4.5`) — Contributed to rendering pipeline hardening and viewport UI tools during WoC 5.0.

---

## Interests

- **Chess** — [1800+ Blitz on Lichess](https://lichess.org/@/Ripu01). The only domain where I trust intuition over computation.
- **Guitar** — Committed enough to own one, not enough to fix the missing E string.

---

<div align="center">

[Email](mailto:ripuranjanbaruah@zohomail.in) · [Gambits.in](https://gambits.in) · [Lichess](https://lichess.org/@/Ripu01) · [Codeforces](https://codeforces.com/profile/R_Baruah) · [N-Body Labs](https://github.com/N-Body-Labs)

</div>
