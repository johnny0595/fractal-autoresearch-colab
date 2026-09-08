# 🌀 fractalsearch 🌀

[Open the thin Colab runner](https://colab.research.google.com/github/johnny0595/fractal-autoresearch-colab/blob/main/fractalsearch_colab.ipynb)

This fork keeps the project as normal, visible source files. The notebook only installs
the dependencies, shows the research instructions and baseline, runs an experiment,
opens the original dashboard, and explains how to hand the same directory to an agent.
Nothing is packed into a hidden setup cell.

Can AI Agents do AI research?


This project attempts to facilitate this strange loop on a toy ML problem:
How well can a function approximator fit the mandelbrot set? 
It is a low-dimensional curve-fitting problem, like fitting an image, but this image has infinite detail and complexity at every scale. 
This has been a [pet project of mine](https://github.com/MaxRobinsonTheGreat/mandelbrotnn) for a long time.


As the human overseer, you can edit the prompt file AGENT.MD to guide bot behavior, rather than writing any code directly. Spin up any AI agent, point it at AGENT.MD, talk with it for a bit, and let 'er rip. You can monitor performance through your webbrowser at `localhost:8000`.


This project is directly adapted form Karpathy's [autoresearch](https://github.com/karpathy/autoresearch). 
All code was AI generated with claude (this is human written btw). 

> [!WARNING]  
> I will not be managing this repo or accepting PRs.
