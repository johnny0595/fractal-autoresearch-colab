# 🌀 fractalsearch in Colab 🌀

Can a coding agent do AI research?

The task is to find a better universal function approximator for the Mandelbrot target:
`(real, imaginary) → value`. Every experiment gets the same training budget and is scored
on a fixed dense evaluation grid. Lower MSE is better.

This repository packages Max Robinson's
[fractalsearch](https://github.com/MaxRobinsonTheGreat/fractalsearch) as a thin Colab
workflow. The harness, target, solutions, results format, and original live dashboard are
ordinary source files—not generated or hidden inside the notebook. The project was
inspired by Andrej Karpathy's [autoresearch](https://github.com/karpathy/autoresearch).

## Start here

[Open `fractalsearch_colab.ipynb` in Colab](https://colab.research.google.com/github/johnny0595/fractal-autoresearch-colab/blob/main/fractalsearch_colab.ipynb)

In Colab:

1. Connect a GPU runtime. A Tesla T4 is fine.
2. Run the notebook from top to bottom.
3. Read `AGENT.md` and the baseline solution shown in the notebook.
4. Run the short manual baseline once.
5. Leave the original dashboard open.
6. Open **Tools → Terminal** and start either Codex CLI or Claude Code using the final
   notebook instructions.

The notebook and terminal share `/content/fractal-autoresearch-colab`, including the GPU,
solution files, `runs.jsonl`, and run artifacts. The dashboard updates when an evaluation
finishes.

## What the agent changes

- `solutions/*.py` — model architectures and training ideas
- `solutions/notebook.md` — hypotheses, results, and follow-up ideas
- `runs.jsonl` — the experiment leaderboard
- `runs/<run-id>/` — prediction, error, source snapshot, and result artifacts

The agent must not modify `harness/` or `dashboard/`. The detailed rules and research loop
live in `AGENT.md`.

## Git stays local

The setup cell configures a throwaway Git identity and removes the GitHub remote after
cloning. The agent can branch and commit normally, but it has nowhere to push. Those
commits exist only in the current Colab runtime and disappear when that runtime is deleted.

If you want to keep an experiment, download its solution file, notebook, or run artifacts
before ending the session. Do not add the original GitHub remote back during an autonomous
run.

## Manual commands

From the repository root:

```bash
python -m harness.evaluate solutions/baseline_mlp.py --budget 30
python -m uvicorn dashboard.app:app --port 8000
```

The notebook uses 30 seconds only for its quick manual check. The autonomous protocol in
`AGENT.md` retains fractalsearch's original five-minute experiment budget.

## Colab and Codex permissions

Codex's ordinary workspace sandbox can see `nvidia-smi` while still blocking PyTorch from
opening the CUDA driver, and it protects `.git` from writes. The notebook starts Codex with
automatic review so CUDA and local Git commands can be elevated individually while other
commands remain workspace-sandboxed. Keep authentication tokens out of the repository and
do not mount Google Drive during an unattended research loop.
