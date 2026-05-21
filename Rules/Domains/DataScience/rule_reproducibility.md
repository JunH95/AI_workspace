# Rule for Machine Learning Experiment Reproducibility

> Physical runtime guideline to ensure complete reproducibility of machine learning models and data processing across different executions.

---

## 1. Definition & Role
- **Goal:** Ensure that any machine learning training, validation split, and preprocessing produce identical results when run multiple times with the same inputs and configuration.
- **Scope:** Applied globally across all python-based data science pipelines, PyTorch training loops, and tabular models (e.g., LightGBM).

## 2. Execution Pipeline
Every machine learning training script MUST execute the seed-locking routine at the very beginning of its execution (before initializing datasets or models).

### 2.1 Seed Initialization Routine
```python
import random
import os
import numpy as np
import torch

def seed_everything(seed: int = 42):
    random.seed(seed)
    os.environ['PYTHONHASHSEED'] = str(seed)
    np.random.seed(seed)
    torch.manual_seed(seed)
    torch.cuda.manual_seed(seed)
    torch.cuda.manual_seed_all(seed) # if using multi-GPU
    
    # Guarantee deterministic algorithms in PyTorch
    torch.backends.cudnn.deterministic = True
    torch.backends.cudnn.benchmark = False
```

### 2.2 Framework-Specific Settings
- **LightGBM:** Always set the `random_state` parameter in the model initialization:
  ```python
  model = lgb.LGBMRegressor(random_state=42, ...)
  ```
- **Scikit-Learn:** Always set `random_state` in split functions (e.g., `KFold`) and estimators:
  ```python
  kf = KFold(n_splits=5, shuffle=True, random_state=42)
  ```

## 3. Constraints
- **Prohibited Actions:**
  - Never use raw `random.random()` or `np.random.rand()` without setting global seeds first.
  - Avoid using non-deterministic PyTorch operations where absolute reproducibility is required, or explicitly configure `torch.use_deterministic_algorithms(True)` if supported.
  - Do not dynamically change seed values mid-execution or between cross-validation folds.
- **Exceptions:**
  - Standard training speedups using `torch.backends.cudnn.benchmark = True` are allowed ONLY during rapid prototyping phases where exact numerical replication is not strictly required.
