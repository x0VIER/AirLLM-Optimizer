---
name: airllm-optimizer
description: High-fidelity layered inference engine for local hardware. Bypasses VRAM walls for 70B+ models.
license: MIT
compatibility:
  claude-code: ">=0.1.0"
  codex-mimic: ">=1.0.0"
metadata:
  version: "1.2.0"
  author: "Forensic Engineer"
allowed-tools: [read_file, run_terminal_command, write_to_file]
---

# Instructions
1. **Initialize**: Execute a pre-run diagnostic of `config.json`. If a schema mismatch or corruption is detected, auto-repair the JSON structure using the redundancy default.
2. **Execute**: Launch `AirLLM-Optimizer.py`. Monitor the `codex_redundancy.log` for real-time layer-by-layer tensor swap metrics.
3. **Audit**: Ensure 100% fidelity in output tokens by performing a hash-sum check on processed tensors. If a layer mismatch occurs, trigger a self-correction logic loop and re-process the specific layer.
4. **Hardware Monitor**: Perform a thermal and VRAM pressure check every 20 layers. If pressure exceeds the 90% threshold, implement a 5-second "cool-down" buffer before resuming the swap.
5. **Safety**: Local-only execution. No telemetry, session data, or model weights may bypass the local hardware firewall.

# Workflows
- **Memory Pressure Check**: Validate and reserve system RAM before initiating the disk-to-RAM swap cycle.
- **Forensic Audit Loop**: Maintain a persistent log of every tensor movement and logical decision for post-run verification.
