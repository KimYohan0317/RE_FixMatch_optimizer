## [Re] Reimplementation of FixMatch and Investigation on Optimizer

### Introduction
This repository contains our reimplementation of FixMatch, a semi-supervised learning (SSL) method that leverages both strong and weak labels to improve classification performance.

We used the code from https://github.com/Celiali/FixMatch with some modifications. We reproduced the paper "FixMatch: Simplifying Semi-Supervised Learning with Consistency and Confidence". The code we used for the experiments can be found in the RE_FixMatch_optimizer/run_ours/ folder.

### RE_FixMatch/run_ours/ file description

- `Fixmatch.py`: base execution file for Fixmatch.
- `Fixmatch_adamw.py`: the experimental execution file where the optimizer is changed to AdamW.
- `Fixmatch_adamw_lr_006.py`: experimental execution file where the optimizer is changed to AdamW and the learning rate is changed.
- `Fixmatch_mu_10.py`: experimental execution file where mu is changed to 10.
- `Fixmatch_mu_13.py`: experimental execution file where mu is changed to 13.
- `Fixmatch_mu_16.py`: experimental execution file where mu is changed to 16.
- `Fixmatch_t_91.py`: experimental execution file where the threshold is changed to 0.91.
- `Fixmatch_t_93.py`: experimental execution file where the threshold is changed to 0.93.
- `Fixmatch_t_97.py`: experimental execution file where the threshold is changed to 0.97.
- `Fixmatch_t_95_m_70.py`: experimental execution file where the momentum is changed to 0.7.
- `Fixmatch_t_95_m_80.py`: experimental execution file where the momentum is changed to 0.8.
- `Fixmatch_t_95_m_95.py`: experimental execution file where the momentum is changed to 0.95.

  ## Experiment result
  #### official FixMatch, Ours
  
| CIFAR10 | Accuracy |
|-------|-----------|
|   Official Fixmatch(RA)   |    94.93 ± 0.65 |
|   Ours(RA)   |    92.55  |

---

#### threshold experiment
|   | Top1_acc | Top5_acc |
|-------|-----------|-----------|
|   Fixmatch_t_95(official)   |    92.55  |    99.69  |
|   Fixmatch_t_91   |    92.35  |    99.74  |
|   Fixmatch_t_93   |    92.5  |    99.8  |
|   Fixmatch_t_97   |    92.65  |    99.65  |

---

#### Ratio of unlabeled data(mu) experiment
| unlabeld(mu)  | 	7(official) | 10  | 13 | 16 |
|-------|-----------|-----------|-----------|-----------|
|   acc   |    91.18 |    91.7  |  91.68  |   91.28  |
|   error rate   |    8.82  |    8.30  |  8.32  |  8.72  |

---

#### momentum experiment
| momentum(β)  | 	0.90(official) | 0.70  | 0.80 | 0.95 |
|-------|-----------|-----------|-----------|-----------|
|   acc   |    91.18 |    91.66  |  92.08  |   91.18  |
|   error rate   |    8.82  |   8.34  |  7.92  | 8.82  |

---

#### Optimizer AdamW

The plot for SGD with Momentum and AdamW can be found in the following folder:

- [SGD with Momentum and AdamW](https://github.com/KimYohan0317/RE_FixMatch_optimizer/blob/main/plot/baseSGD_adaW_200epoch.png)

Please navigate to this folder to view the image: `baseSGD_adaW_200epoch.png`.

### All other plots are located in this folder

- **[RE_FixMatch_optimizer/plot](https://github.com/KimYohan0317/RE_FixMatch_optimizer/tree/main/plot)**

This folder contains all the additional plots generated during the project. Each plot is saved as an image file and is named according to the experiment it represents. You can explore the folder to find visualizations that provide insights into the results of various analyses performed in this project.

---
### Conclusion

In this work, we study and reimplement FixMatch from scratch.We reproduced essential experiments, including model performance on CIFAR-10 and ablation studies.

---
