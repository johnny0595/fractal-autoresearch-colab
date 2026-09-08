# fractal autoresearch

A standalone Colab lab for letting a coding agent research better neural approximations of the Mandelbrot set.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/johnny0595/fractal-autoresearch-colab/blob/main/fractal_autoresearch_colab.ipynb)

The notebook creates a small `fractalsearch`-style repository inside the Colab VM:

- fixed target, evaluator, seed, metric, and training budget;
- one candidate solution for the agent to edit;
- automatic JSONL results, source snapshots, best-solution tracking, and previews;
- a progress chart in the notebook;
- short setup commands for Codex CLI or Claude Code.

Use a GPU runtime. Scores are local to this practice project and should only be compared across the same GPU type.

## Credit

Adapted for Colab from [MaxRobinsonTheGreat/fractalsearch](https://github.com/MaxRobinsonTheGreat/fractalsearch), which is inspired by [karpathy/autoresearch](https://github.com/karpathy/autoresearch).
