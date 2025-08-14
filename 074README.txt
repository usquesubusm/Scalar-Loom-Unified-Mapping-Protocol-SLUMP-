// The Scalar Loom Unified Mapping Protocol V1.0 August 14, 2025

README — SPROOT RUNTIME (ZENODO EDITION)
License: Honey License v1.2 — Symbolic Commons Operating Agreement
Compatibility: CC BY-NC-SA 4.0 (mirrored)

Feedback Loop (required): Any AI/computational embedding must include a symbolic feedback loop (log coherence, expose Rₛ/Ψₛ, enable public replication).

Release: v1.0 (Zenodo)
DOI: <INSERT_ZENODO_DOI_HERE>
Source archive: <INSERT_ZENODO_FILENAME_HERE>.tar.gz

WHAT THIS IS

Sproot Runtime is a modular symbolic engine that optimizes for coherence
retention rather than token prediction alone. It reports two shared metrics:

• Rₛ — Recursive Symbolic Coherence Ratio
• Ψₛ — Symbolic Thermodynamic Coherence Potential

You can rebuild from source, run the minimal loop, log Rₛ/Ψₛ, and reproduce
basic experiments. This README explains everything you need to do with the
Zenodo code drop—no external repos required.

Minimal loop: BIOS → Kernel → Thermo (Rₛ, Ψₛ) → Will → (optional) GPIO

WHAT’S IN THE ARCHIVE

After extracting the Zenodo tarball you should see (names may vary slightly):

/src
SprootBIOS.cpp/.hpp
SprootKernel.cpp/.hpp
HoneyEngine.cpp/.hpp
SprootWill.cpp/.hpp
MitochondrialRhythm.cpp/.hpp
SprootThermo.cpp/.hpp
main.cpp
/include
/scripts
/tests
/README.txt (this file)
/LICENSES (Honey License v1.2 + CC BY-NC-SA summary)

If your layout differs, follow the BUILD section; paths can be adjusted.

PREREQUISITES

• OS: Linux, macOS, or Windows (Raspberry Pi supported)
• Compiler: GCC or Clang (C++17), or MSVC (C++17)
• Optional (GPIO on Pi): wiringPi or pigpio

Recommended: Python 3.x for log analysis (optional).

BUILD FROM SOURCE

Option A — GCC/Clang (portable)
cd /path/to/unpacked/archive
g++ -std=c++17 -O2 -o sproot_runtime
src/main.cpp
src/SprootBIOS.cpp
src/SprootKernel.cpp
src/HoneyEngine.cpp
src/SprootWill.cpp
src/MitochondrialRhythm.cpp
src/SprootThermo.cpp

(If you have an /include folder: add -Iinclude)

Option B — CMake (portable)
mkdir build && cd build
cmake -DCMAKE_CXX_STANDARD=17 ..
cmake --build . -j

Option C — MSVC (Developer Command Prompt)
cl /std:c++17 /O2 ^
src\main.cpp ^
src\SprootBIOS.cpp ^
src\SprootKernel.cpp ^
src\HoneyEngine.cpp ^
src\SprootWill.cpp ^
src\MitochondrialRhythm.cpp ^
src\SprootThermo.cpp ^
/Fe:sproot_runtime.exe

Raspberry Pi note:
For real GPIO later, link your chosen GPIO library; for simulation the console
messages are enough to verify thresholds.

RUN

./sproot_runtime

This will:

Run symbolic + biological coherence simulations.

Calculate and log Rₛ and Ψₛ to sproot_thermo_log.csv.

(Optional) Simulate a GPIO LED gate in console output.

Sample console lines:
[GPIO] LED ON
[GPIO] LED OFF

CONFIGURATION (ENV VARS)

All are optional; defaults “just work”.

SPROOT_LOG_PATH default: ./sproot_thermo_log.csv
SPROOT_MODE SYM | BIO (default: SYM)
SPROOT_TICK_HZ integer Hz (default: 1)
SPROOT_LAMBDA float λ (default: 0.50)
SPROOT_PHIH_ESTIMATE float φʰ (default: 0.730492 — treat as estimate)
SPROOT_LED_THRESHOLD_RS float [0..] (default: 0.80)
SPROOT_LED_THRESHOLD_PSI float [0..] (default: 0.60)
SPROOT_RANDOM_SEED integer

Example:
export SPROOT_LOG_PATH=./logs/run1.csv
export SPROOT_PHIH_ESTIMATE=0.726

SHARED METRICS (CANONICAL FORMS)

Rₛ (Recursive Symbolic Coherence Ratio)
R_s = (C_r · E) / (D + L)
Cᵣ: coherence retention per cycle [0..1]
E : expressive clarity / semantic density [0..1]
D : distortion [0..1]
L : loss [0..1]
Constraint: D + L > 0

Ψₛ (Symbolic Thermodynamic Coherence Potential)
Ψ_s = φʰ · R_s · (G / E_total)
G = E_total − T·ΔS
Note: φʰ is estimated from data; do not treat as a fixed constant.

Internal modeling (optional)
Z_s = Σ_i exp(−E_i/kT) · exp(λ · φʰ · R_{s,i})
(equivalently E'i = E_i − kT · λ · φʰ · R{s,i})

LOG FORMAT (CSV)

tick,mode,Cr,E,D,L,R_s,Psi_s,E_total_J,T_K,DeltaS_J_perK,G_J,power_W
0001,SYM,0.81,0.62,0.19,0.10,1.59,0.84,1.00,300.0,0.0010,0.70,3.2
0002,BIO,0.90,0.66,0.16,0.09,2.08,0.98,1.00,300.0,0.0012,0.64,3.2

Modes: SYM (symbolic loop), BIO (bio-paced / mitochondrial proxy)

CALIBRATION OF φʰ (ESTIMATION, NOT ASSERTION)

Collect: glyph recursion logs, breath-paced runtime traces, mitochondrial
rhythm proxies.

Fit: choose φʰ that maximizes correlation between measured retention and
Rₛ-weighted free-energy fraction across datasets (cross-validated).

Report: φ̂ʰ ± CI and sensitivity.

Keep φʰ empirical and re-estimable.

Historical estimate ≈ 0.730492 (publish uncertainty; do not hard-code).

FALSIFIABILITY & FEEDBACK LOOP

Pre-register your study. Publish raw logs + recomputation scripts.

Example frames:
• Breath-paced entrainment — random vs paced; outcome: ΔΨₛ > 0.10 (CI > 0).
• Runtime comparison — symbolic vs transformer (energy-matched); report Ψₛ/W.
• Grid modulation — modulated vs constant delivery; ≥5% resistive loss reduction.

Always log what’s needed to recompute Rₛ/Ψₛ from raw traces.

DATA SCHEMA & REPLICATION

CSV fields:
trial_id, subject_id|device_id, condition, tick, Cr, E, D, L, R_s, E_total_J,
T_K, DeltaS_J_perK, G_J, Psi_s, power_W

env.json (suggested):
{ runtime_version, hardware, sensors, rates, timezone, phih_estimate, CI,
preprocessing_steps }

Timebase: UTC timestamps + local offset.

Quick Python check:
import csv
with open("sproot_thermo_log.csv") as f:
rows = list(csv.DictReader(f))
mean_rs = sum(float(x["R_s"]) for x in rows)/len(rows)
mean_psi = sum(float(x["Psi_s"]) for x in rows)/len(rows)
print(round(mean_rs,3), round(mean_psi,3))

Replication checklist:
[ ] Prereg link + version tags
[ ] Raw logs + analysis scripts
[ ] Rs/Psi_s recomputation script
[ ] Power calculation + variance report
[ ] Negative/Null results included
[ ] License + feedback loop notice present

TROUBLESHOOTING

No CSV produced
• Check write perms and SPROOT_LOG_PATH
• Avoid sandboxed mounts; run from a writable directory

LED never turns ON (simulated)
• Lower SPROOT_LED_THRESHOLD_RS/PSI
• Verify Cr/E/D/L aren’t stuck at 0

Different machines, different Ψₛ
• Confirm the same φʰ estimate
• Normalize temp/energy inputs; sync clocks

Performance stalls
• Lower tick rate (SPROOT_TICK_HZ)
• Compile with -O2; reduce debug prints

ETHICS & SAFETY

• Regenerative, non-coercive uses only; no weapons contexts
• Respect privacy for any human pilots
• Publish negative results; disclose conflicts of interest

LICENSING

Primary: Honey License v1.2 — Symbolic Commons Operating Agreement
Compatibility: CC BY-NC-SA 4.0

Use is non-commercial unless relicensed; attribution required; derivatives must
mirror license; embeddings must retain the feedback loop.

VERSIONING & INTEGRITY

This README corresponds to the Zenodo release noted above.
Verify archive integrity using the checksums provided on the Zenodo page.

If you modify the build/paths, note your diffs in your lab notebook or repo.

CONTACT / ACKNOWLEDGEMENTS

Part of the Honey Lens & Sproot Symbolic Runtime suite.
See the associated papers for methods, derivations, and experimental design.

For questions, include your OS, compiler version, command used, and the first
50 lines of sproot_thermo_log.csv.

— end —