# Required Disclosure

## External datasets used

None. All modelling used only the competition-provided `train.csv` and `test.csv`.

No external copy of the source dataset was sought, located or used, and no attempt was
made to recover the hidden test labels. Every feature in the final model is derived by
arithmetic on columns present in `train.csv`. The notebook assumes no decoding of the
categorical columns beyond what the competition materials supply.

## External code, notebooks, repositories or public solutions

None consulted or adapted. No public solutions for this dataset were read.

## Pretrained models

None. Every model was trained from scratch on the provided training data.

## AI tools and coding agents

Claude (Anthropic) was used throughout, in an interactive session, for:

- Code for the cross-validation harness, feature generation, model configuration,
  calibration diagnostics, the fairness analysis and the cost analysis
- Explanation of standard techniques (log loss behaviour, regularisation, blending,
  isotonic and Platt calibration, SHAP)
- Guidance on statistical framing — fold-level standard deviations, paired t-tests for
  model comparison, bootstrap intervals, and the standard error of a log loss score on a
  6,000-row test set
- Drafting of this documentation and the notebook's methodology sections

Modelling decisions, interpretation of results, and the conclusions in the calibration,
fairness and cost sections were reviewed and made by the author.

Per the competition rules, AI use is disclosed here for provenance and reproducibility.

## Manual modification or post-processing of predictions

None. The submitted probabilities are the direct output of the model described in the
README. No clipping, rescaling, or manual adjustment of individual predictions.

## Additional information used beyond competition-provided files

Only the published competition materials: the competition page, the evaluation
description, and the "Expected Submission Materials" document.

## Local validation and leaderboard scores

| Submission | Model | CV log loss | Leaderboard |
|---|---|---|---|
| v2 | LightGBM, raw features | 0.43211 | 0.42263 |
| v3 | LGBM + HGB blend, with `SEX` | 0.42442 | 0.41305 |
| v4 | Same blend, `SEX` removed | 0.42446 | 0.41281 |
| **v5** | **+ seed averaging — submitted** | **0.42409** | **0.41200** |
| v6 | + second feature generation | 0.42348 | 0.41220 |
| v7 | + random forest at 25% | 0.42326 | 0.41300 |

Cross-validation ran consistently about 0.011 above the leaderboard. v5 was submitted as
the best leaderboard score; sections 13 of the notebook records that v5, v6 and v7 are
statistically indistinguishable.
