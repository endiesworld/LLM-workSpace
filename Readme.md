# 🧠 Using a Local Python Environment with Jupyter Notebook

This guide walks you through making Jupyter Notebook use a local Python environment (e.g., created using `python -m venv` or `virtualenv`).

---

## ✅ Step-by-Step Instructions

### 1. Activate Your Environment

If you haven’t already activated your virtual environment, run:

```bash
source path/to/venv/bin/activate
pip install ipykernel
python -m ipykernel install --user --name=myenv --display-name "Python (myenv)"
jupyter notebook
```

### Choose the Correct Kernel
In the Jupyter Notebook interface:

Click Kernel → Change kernel → Select "Python (myenv)"