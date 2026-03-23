# Ripuranjan Baruah
**Developer | Researcher | [Gambits.in](https://gambits.in) (Stealth)**

I develop systems for graphics, physics, and security. My work focuses on deterministic logic and architectures that prioritize algorithmic efficiency over brute-force compute.

I operate under the **Ryzen Standard**: a philosophy of achieving research-grade results on consumer-grade hardware (Ryzen 5 5500U, 8GB RAM).

---

### 🚀 Flagship Research: RTC-Core (Project Oort)
**Project Lead.** Bimodal Resilient Telemetry Codec for high-BER satellite downlinks. *Targeting ADASS Systems Track.*
*   **Metric:** 2.08–2.53x bandwidth reduction (vs 16-bit FITS) by trading Shannon coding efficiency (0.80x) for strict transmission resilience.
*   **Architecture:** Bimodal adaptive routing (RAW_RICE vs LOCO-I/RLGR) switching based on physics-derived instrument noise thresholds (Poisson sky component).
*   **Resilience:** Per-tile state isolation and 1-byte kP side-channels to isolate bit-flip corruption in degraded space-to-ground RF links.
*   **Integrity:** Big-Endian bit-packing and CRC32 coverage across tile headers for FITS-compatible scientific telemetry.

### 🛠️ Core Systems

**[SENTRY](https://github.com/r-baruah/SENTRY)** `Foundry` `Solidity` `TypeScript`
**Project Lead.** Deterministic verification engine for smart contract exploits.
*   **Verification:** Programmatically constructs executable **Solidity Test Harnesses** to verify AI-generated hypotheses, moving beyond stochastic auditing.
*   **Infrastructure:** Developed an ephemeral **300ms Sandboxing Layer** using custom Foundry cheatcodes to resolve complex on-chain dependencies without state pollution.
*   *Winner: Hack Space 2025 (Blockchain Track).*

**[Exo-Checkmate](https://github.com/r-baruah/Exo-Checkmate)** `Python` `PyTorch` `SciPy`
**Systems Lead (Team N-Body).** Physics-informed exoplanet discovery engine.
*   **Pipeline:** Implemented **Hill Stability Criteria (Gladman, 1993)** and **Box Least Squares (BLS)** using optimized **NumPy vectorization** to prune candidates, ensuring predicted orbits are stable before classification.
*   **Scientific Validity:** Integrated Quadratic Limb Darkening (ExoCTK physics) into the ML decision latent space.

**[Pyre Engine](https://github.com/Open-Source-Chandigarh/pyre)** `C++17` `OpenGL 4.5`
**Open Source Contributor.** High-performance rendering engine.
*   **Tooling & Hardening:** Integrated a real-time UI layer for scene manipulation and hardened the rendering pipeline against shadow indexing bugs and asset-loading failures.
*   **Optimization:** Focused on **Zero-allocation render loops** and cache-friendly entity storage to maintain high frame-time stability on integrated graphics. (WoC 5.0).

---

### 🔭 Active Research & Strategy
*   **Gambits.in (Stealth):** Developing independent infrastructure for regional chess excellence and strategic cognitive training.
*   **TTV Dynamics:** Utilizing **Genetic Symbolic Regression (PySR/Julia)** to derive analytical laws for planetary perturbations from TESS data.
*   **Chess:** 1800+ ELO (Blitz). Pattern recognition and positional strategy.

---

### 📬 Connect
[Email](mailto:ripuranjanbaruah@zohomail.in) • [Codeforces](https://codeforces.com/profile/R_Baruah) • [LinkedIn (Inactive)]
