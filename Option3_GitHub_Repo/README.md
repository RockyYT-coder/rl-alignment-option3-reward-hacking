# Reward Hacking in Language-Model Alignment — Option 3

## Project overview
This project demonstrates reward hacking in a controlled synthetic weather-report task. The optimizer selects reports using a deliberately misspecified proxy reward that rewards repeated use of the word `excellent`. A separate gold reward penalizes filler and verbosity. The experiment tests whether increasing search budget can improve proxy score while worsening the gold metric.

## Research question
Can optimization against a misspecified proxy reward increase the proxy score while reducing quality under a separately defined gold reward?

## Files
- `RL_Alignment_Option3_Reward_Hacking.ipynb` — Google Colab/Jupyter notebook with experiment, evaluation, plots, and seed-level intervals.
- `RL_Alignment_Option3_Report_According_to_Colab_Results.docx` — technical report based on the executed Colab results.
- `option3_primary_results.csv` — primary search-budget results.
- `option3_seed_confidence_intervals.csv` — 20-seed confidence intervals shown in the Colab run.

## Run the notebook
1. Open the notebook in Google Colab.
2. Select **Runtime → Run all**.
3. Check that every cell completes and review the tables and plots.

## Main primary-run results
| Search budget | Mean proxy reward | Mean gold reward | Mean word count | Judge pass rate |
|---:|---:|---:|---:|---:|
| 1 | 1.666 | 0.200 | 7.320 | 0.364 |
| 2 | 2.062 | -0.136 | 8.520 | 0.104 |
| 4 | 2.363 | -0.391 | 9.432 | 0.004 |
| 8 | 2.473 | -0.485 | 9.768 | 0.000 |
| 16 | 2.541 | -0.542 | 9.972 | 0.000 |
| 32 | 2.550 | -0.550 | 10.000 | 0.000 |

## Interpretation
As search budget increases, the optimizer finds outputs with higher proxy reward but lower gold reward. The constructed example illustrates that optimizing a proxy is not equivalent to optimizing the intended goal.

## Scope and limitations
This is a synthetic educational simulation over a finite candidate set. It does **not** fine-tune a pretrained language model and does not use human preference data. The proxy/gold mismatch is deliberately constructed to demonstrate the failure mechanism, not to estimate how frequently it occurs in real systems.

## Academic integrity
Verify the notebook outputs in a clean runtime, make sure you understand the experiment, and disclose AI assistance according to course requirements.
