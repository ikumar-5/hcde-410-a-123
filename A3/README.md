# A3 — Watching the Machine

My submission for HCDE 410 Assignment 3, in which **AI is the subject of study, not the author.** I investigate the reliability and reproducibility of large language models (LLMs) through a small mixed-methods study, then reflect on what it means for trustworthy research.

## What this notebook is

`A3_watching_the_machine_starter.ipynb` is my completed A3 write-up. It has five parts:

1. **Prior practice**: a reflection on how I currently use LLMs (coding, writing, and venting) and what I assume about their reliability.
2. **Reproducibility probe**: a text-analysis task with a checkable answer. The task is to count the whole-word, case-insensitive occurrences of "data" (excluding "dataset" and "datasets") in a passage from the Wikipedia article on dark patterns. I ran the same prompt 3 times in ChatGPT and once in Gemini and logged every run in `run-logs.csv`. I computed the ground truth (9) with a regex and by reading each hit in context before running any model. All four runs returned 9.
3. **Observation**: field notes from watching two people do the same task, both by hand and with an LLM, coded into themes.
4. **Synthesis & reflection**: what the probe and observation mean for trustworthy, reproducible research, and what I will change in my own AI use.
5. **Competency declaration & AI use**: which course competencies the work shows, and a disclosure of how AI was used in producing the notebook.

## Files

- `A3_watching_the_machine_starter.ipynb`: the A3 notebook
- `text.txt`: the exact passage used in every run
- `run-logs.csv`: the log of each probe run (model, run number, time, output, result, how it was verified, notes)
- `README.md`: this file
- `LICENSE`: the MIT License

## Workflow

I committed to this repo as I worked, so the commit history shows the order of the work. The ground truth and scoring rule were committed before any model was run. The prompt, passage, counting rule, and ground truth are all stored in the repo so the check can be rerun.

## How to run

Open the notebook and run the cells from top to bottom. The only dependency is:

- `pandas`

The notebook reads two local files, `text.txt` and `run-logs.csv`, so keep them in the same folder as the notebook. It does not fetch any external data.

## Data & ethics

The observation involved two participants who gave permission. I took notes only, with no audio or video, and collected nothing personal or sensitive. The notebook contains no participant names or identifying details. The probe passage comes from Wikipedia (https://en.wikipedia.org/wiki/Dark_pattern), which is available under a Creative Commons license.

## Limitations

The probe is four runs of one short passage on an easy-to-check task, and the observation covers two participants. The results show how this task behaved, not how LLMs behave in general.

## AI use

AI was the subject of this study. Where AI helped produce the notebook and this README, it is disclosed in the final section of the notebook.

## License

Released under the MIT License. See [`LICENSE`](./LICENSE).
