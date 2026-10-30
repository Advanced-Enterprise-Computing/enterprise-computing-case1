# Case 1 – Machine Learning Applications

IT Management, TU Dortmund, Winter Term 2026/27. See `assignment.pdf` for the task and `PROJECT.md` for roles and conventions.

## Setup
```bash
git clone https://github.com/AhmedWilly/enterprise-computing-case1.git
cd enterprise-computing-case1
python -m venv .venv
# Windows: .venv\Scripts\activate    macOS/Linux: source .venv/bin/activate
pip install torch torchvision --index-url https://download.pytorch.org/whl/cu126   # NVIDIA GPU; CPU only: pip install torch torchvision
pip install -r requirements.txt
```
Then put the dataset at `data/1_Case_AEC/Cat` and `data/1_Case_AEC/Dog` (not in Git).

## Layout
| Path | Content |
|---|---|
| `notebooks/1_Case_AEC.ipynb` | Cat vs Dog classifier (Part 2) |
| `src/metrics_utils.py` | Metrics, table and plots |
| `results/` | One JSON per experiment |
| `report/` | Report sections + screenshots |
| `slides/` | Discussion slides |
| `progress/` | Per-person handoff notes |
