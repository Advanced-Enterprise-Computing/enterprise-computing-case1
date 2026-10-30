# Case 1 – Machine Learning Applications (IT Management, TU Dortmund, WS 2026/27)

Team of 3. This file is the shared project context.

## Start / end of every session
- Start: `git pull`, then read this file and every file in `progress/`.
- End: update your own file in `progress/` (ahmed.md, gomaa.md, abdelrazek.md) (done / decisions / next steps / blockers), then commit + push.

## Deliverables
- **One PDF** to Moodle by **Mon 02.11.2026 23:59**. Front page: all 3 names + matriculation numbers.
- **~5 slides PDF** for the discussion on **Tue 03.11.2026** (based on the guiding questions / tasks).
- Assignment text: `assignment.pdf`.

## Part 1 – TensorFlow Playground (playground.tensorflow.org, no code)
Base setup: Classification, Circle dataset, Show test data ON, features x1 + x2 only, 0 hidden layers, LR 0.03, no regularization.
- **A1**: describe the (linear) boundary and why it can't separate the ring.
- **A2**: 1 hidden layer, 6 neurons, Tanh, 100–200 steps; then 4 and 2 neurons. Smallest neuron count that still works, what it says about capacity. Screenshot of best boundary + which visual aspects show its quality.
- **B1**: LR 0.003 vs 1.0 – speed, stability, final boundary quality.
- **B2**: LR 0.03, L2 rate 0.03, noise 0% → 30%. Is L2 smoother? Test performance? Which (L2 on/off) is more robust at 30% noise and why? Screenshot.
Output: `report/part1_playground.md` + screenshots in `report/img/`.

## Part 2 – Cat vs Dog classifier (`notebooks/cats_vs_dogs_classifier.ipynb`)
Transfer learning: pretrained ResNet-18, frozen backbone, only the final `fc` layer is trained.
Required (and explain WHY results differ):
1. ≥2 train/test split sizes  2. ≥2 optimizers  3. ≥2 metrics  4. one table + ≥2 graphs.
Dataset lives locally in `data/1_Case_AEC/{Cat,Dog}` (git-ignored, never commit it).

## Roles and file ownership (only the owner edits a file)
| Who | Role | Files |
|---|---|---|
| Ahmed – AhmedWilly (has RTX 2060 GPU) | Repo owner, notebook, runs all training | `notebooks/cats_vs_dogs_classifier.ipynb`, `results/*.json` |
| Mohamed Gomaa – issamfarouk | Metrics + visualizations, Part 2 write-up | `src/metrics_utils.py`, `report/part2_classifier.md` |
| Ahmed Abdelrazek – AhmedElngar | Part 1 Playground, final report PDF, slides | `report/part1_playground.md`, `report/img/`, `report/final/`, `slides/` |

Jupyter notebooks merge badly → only Ahmed (AhmedWilly) commits changes to the notebook. Others send code snippets
(or put reusable code in `src/`) and Ahmed adds the cells.

## Results JSON format (agreed between notebook and `src/metrics_utils.py`)
One file per experiment: `results/<run_name>.json`, e.g. `results/split80_adam.json`
```json
{
  "run_name": "split80_adam",
  "train_frac": 0.8,
  "optimizer": "Adam",
  "lr": 0.001,
  "epochs": 3,
  "batch_size": 32,
  "seed": 42,
  "n_train": 9998,
  "n_test": 2500,
  "train_time_sec": 123.4,
  "classes": ["Cat", "Dog"],
  "history": [
    {"epoch": 1, "train_loss": 0.15, "train_acc": 0.94, "test_loss": 0.06, "test_acc": 0.98}
  ],
  "test": {
    "y_true": [0, 1, 1, 0],
    "y_pred": [0, 1, 0, 0],
    "y_prob": [0.02, 0.97, 0.41, 0.10]
  }
}
```
`y_prob` = predicted probability of class 1 (Dog). Labels: 0 = Cat, 1 = Dog.

## Git workflow
- `git pull` before starting, push at least twice a day.
- Branch per feature (`<name>/<feature>`) + Pull Request, or commit directly to `main` touching only your own files.
- Never commit `data/`, model weights, or `.venv/`.

## Timeline
Fri 30.10 setup · Sat 31.10 core work · Sun 01.11 integrate + draft report · Mon 02.11 review & submit early · Tue 03.11 slides/discussion
