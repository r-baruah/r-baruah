<div align="center">

  <img src="github-header-banner.png" alt="Ripuranjan Baruah" width="100%">

  <br>

  <b>Developer · Researcher · <a href="https://gambits.in">Gambits.in</a></b>

  <br><br>

  <i>I build systems where the output has to be provable — not probable.</i>
  <br>
  <i>Different domains, same constraint: if it can't survive on 8GB of RAM and a deterministic guarantee, it doesn't ship.</i>

  <br><br>

</div>

> **The Ryzen Standard** — Research-grade results on consumer-grade hardware (Ryzen 5 5500U, 8GB RAM).
> Not because I have to. Because systems built under constraint are systems that actually work.

---

## Flagship Research

*Satellite telemetry compression under extreme hardware and transmission constraints.*

### RTC-Core — Project Oort

**Project Lead** · Bimodal Resilient Telemetry Codec for high-BER satellite downlinks · *In preparation for ADASS Systems Track*

2.08–2.53x bandwidth reduction over 16-bit FITS, achieved by deliberately trading Shannon coding efficiency (0.80x) for strict transmission resilience — because a corrupted frame wastes more bandwidth than an inefficient one.

<details>
<summary><b>Architecture</b></summary>
<br>

**Bimodal Decision Logic:** Each tile's pixel residuals are evaluated against a physics-derived noise floor (Poisson sky component). Tiles where instrument/sky noise dominates route through RAW_RICE — resilient, tolerant of high bit-error rates. Tiles with structure-dominated signal use LOCO-I spatial prediction + RLGR entropy coding for higher compression.

**Why Per-Tile Isolation:** A single bit-flip in an entropy-coded stream cascades into full-frame corruption. Tile-level state boundaries with 1-byte kP side-channels ensure corruption is contained to a single tile — the rest of the frame remains scientifically valid. This is a deliberate architectural choice: sacrifice global coding efficiency for failure isolation.

| Mode | Compression | BER Tolerance | When Used |
|---|---|---|---|
| RAW_RICE | Moderate (~1.5–2x) | High | Noisy tiles, degraded RF links |
| LOCO-I / RLGR | High (~2.5–3x) | Low | Clean tiles, stable conditions |
| **Bimodal (adaptive)** | **2.08–2.53x** | **High** | **Mixed — production target** |

</details>

---

## Core Systems

*Verification engines, physics pipelines, and rendering infrastructure.*

<br>

**SENTRY** · `Foundry` `Solidity` `TypeScript` · [Repo](https://github.com/r-baruah/SENTRY) · [Demo](https://youtu.be/gyUxxnAI25I)
**Project Lead** — Deterministic verification engine for smart contract exploits.

Constructs executable Solidity Test Harnesses to verify AI-generated exploit hypotheses — moving verification from stochastic auditing to deterministic proof. Built on an ephemeral **300ms Sandboxing Layer** using custom Foundry cheatcodes to resolve on-chain dependencies without state pollution.

*Winner — Hack Space 2025, Blockchain Track.*

<br>

**Exo-Checkmate** · `Python` `PyTorch` `SciPy` · [Repo](https://github.com/r-baruah/Exo-Checkmate)
**Systems Lead (Team N-Body)** — Physics-informed exoplanet discovery engine.

Implemented **Hill Stability Criteria (Gladman, 1993)** and Box Least Squares via optimized NumPy vectorization to prune unstable orbital candidates before classification. Integrated Quadratic Limb Darkening (ExoCTK physics) into the ML decision latent space for scientific validity.

<br>

**Pyre Engine** · `C++17` `OpenGL 4.5` · [Repo](https://github.com/Open-Source-Chandigarh/pyre)
**Open Source Contributor (WoC 5.0)** — High-performance rendering engine.

Hardened the rendering pipeline against shadow indexing failures and integrated a real-time UI layer for scene manipulation. Focused on **zero-allocation render loops** and cache-friendly entity storage for frame-time stability on integrated graphics.

---

## Active

**Gambits.in** — Infrastructure for competitive chess development, born from a regional initiative that taught me more about systems design than any codebase.

**TTV Dynamics** — Genetic Symbolic Regression (PySR/Julia) to derive analytical perturbation laws from TESS transit timing data.

**Chess** — 1800+ Blitz. The only domain where I trust intuition over proof.

---

<div align="center">

[Email](mailto:ripuranjanbaruah@zohomail.in) · [Codeforces](https://codeforces.com/profile/R_Baruah)

</div>
