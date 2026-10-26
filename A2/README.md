# A2: Exploring Sources of Bias in the Wikipedia Talk Corpus

**Author:** Isha Kumar | **Course:** HCDE 410 AU26 | **Assignment:** A2

This repository holds a documented Jupyter notebook that audits the **Wikipedia Talk Corpus** (Wikipedia Detox), the labeled comment data behind Google Jigsaw's Perspective API toxic-speech classifier. The notebook looks for limitations in the crowdworker demographic data and the toxicity labels, and argues how each could skew a general-purpose hostile speech detector trained on this data.

## Contents

| File | What it is |
|---|---|
| `[notebook-name].ipynb` | The full analysis, with Markdown explanations next to the code |
| `a2_all_annotator_demographics.csv` | Cleaned, combined worker table produced by the notebook (5,781 rows) |
| `toxicity_labelled_comments_3k_sample.csv` | 3,000-judgment sample used for Part 3 (see Limitations) |
| `LICENSE` | License for my code and written analysis (not for the data) |

## How to reproduce

1. Download the three `*_worker_demographics.tsv` files from the [Wikipedia Talk Corpus on Figshare](https://figshare.com/articles/Wikipedia_Talk_Labels_Toxicity/4563973) (toxicity, attack, and aggression datasets) and place them in a folder named `wikipedia_datasets/` next to the notebook.
2. Put `toxicity_labelled_comments_3k_sample.csv` next to the notebook. If you have the full `toxicity_annotations.tsv`, place it in `wikipedia_datasets/`; the notebook uses it automatically and otherwise falls back to the sample.
3. Install the requirements and run the notebook top to bottom:

```bash
pip install pandas matplotlib scipy jupyter
jupyter notebook
```

Then choose **Kernel > Restart & Run All**. I ran it on JupyterHub with Python 3.13.

## Data

- **Source:** the Wikipedia Talk Corpus released by the Wikimedia Detox project (Wulczyn, Thain, and Dixon, 2017), hosted on Figshare. It contains worker demographics and labels for personal attacks, aggression, and toxicity on English Wikipedia talk page comments.
- **License:** the project states that its data is available under free licenses on Figshare. [Check the license shown on the Figshare page and name it here.]
- **Not included in this repo:** the large raw files (for example the full annotations file), which are excluded by `.gitignore`.

## What I found

- **Duplicated files.** The attack and aggression demographic files are identical (2,190 workers each), and the documentation does not say so. A naive merge of all three files gives 7,971 rows instead of 5,781.
- **`worker_id` is not unique across files.** 1,858 ids appear in both the toxicity and attack/aggression files, but their demographics match only about as often as chance predicts, so I treat them as different people and use a new `unique_id`.
- **Unrepresentative labelers.** Of 5,781 worker records, 63.6% are male and 81.5% say English is not their first language; 86.3% are aged 18-45 and 68.8% hold a bachelor's degree or higher. About 2.0% report being under 18.
- **Incomplete data, twice over.** 1.9% of rows have a blank age, and in the 3k sample 15.6% of the workers who labeled comments have no demographic record at all, which suggests workers who skipped the optional survey are missing entirely.
- **Duplicates distort counts more than percentages.** Rebuilding without removing duplicates inflated every count by about a third but moved percentages by under one point, because the duplicated pool looks demographically similar to the rest.
- **Group differences are suggestive, not established.** Women marked 16.7% of their labels toxic versus 14.5% for men, and native English speakers 18.0% versus 14.7% for non-native speakers, but neither gap is statistically significant (p = 0.14 and 0.08).
- **Documentation inconsistencies.** The toxicity dataset is described as 60k comments in our class data statement, "over 100k" on Figshare, and 160k on the Wikimedia documentation page.

The notebook turns each of these into an evidence, mechanism, and predicted-effect argument about what a general-purpose detector trained on this data could get wrong.

## Updates to our class data statement

Based on this analysis, I would add to the "Provenance" and "Other" sections: the attack and aggression demographic files are identical; `worker_id` values are reused across the toxicity and attack/aggression files; some workers report being under 18; workers without a demographic record appear in the labels; and the stated comment counts disagree across sources. The statement also does not say how comments were sampled from the 95 million available or how roughly ten labels were combined into one.

## Limitations

- **Part 3 uses a 3,000-row sample, not the full annotations file,** which was not in my course folder. The sample holds about one label per comment, so per-comment statistics were not possible, and percentages are estimates for the full dataset.
- Demographics are self-reported through an optional survey; "English as first language" is not a measure of fluency.
- The benchmark comparison in Q7 uses ITU global internet-use rates by gender and qualitative Pew findings by age and education; the 48% female share of internet users is my own estimate from ITU rates.
- I did not attempt the no-code questions (Q13-Q16).

## AI use

I used Claude (Anthropic) as a tutor and drafting assistant. It planned the workflow from our data statement, wrote the code for the duplicate checks, the demographic tables, the missing-data and no-deduplication analyses, and the Part 3 join and chi-square test, It also helped debug a missing-file error. I also used it to ensure that I have completed all parts of the assignment adequately.

I checked the outputs against the text, edited the wording, chose the code track, and did not attempt Q13-Q16. Claude made a few errors that I corrected, including attributing an under-18 worker to the wrong file, pointing to the wrong question for the under-18 counts, and an imprecise "under 45" figure.

## License

This repository is released under the [MIT License](LICENSE). The starter code in the notebook comes from the course materials by Jonathan Morgan and Brock Craft (2022), also under the MIT License; my additions are the analysis, the added code, and the written explanations. The Wikipedia Talk Corpus data is **not** covered by this license. It is hosted on Figshare and remains under its original terms; see the [dataset page](https://figshare.com/articles/Wikipedia_Talk_Labels_Toxicity/4563973).