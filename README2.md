# Changes Made to Run `test_amrsim.py`

This document lists all the code and environment changes made to fix errors and successfully run `test_amrsim.py` in the AMRSim project.

---

## ✅ Summary of Python Code Fixes

---

### 1. Fix `cached_download` Import Error
**File:** `ExtendSentenceTransformer.py`  
**Original:**
```python
from huggingface_hub import HfApi, HfFolder, Repository, hf_hub_url, cached_download
```
**Fixed:**
```python
from huggingface_hub import HfApi, HfFolder, Repository, hf_hub_url, hf_hub_download
```
**Also:**
Replaced all `cached_download(...)` with `hf_hub_download(...)`.

---

### 2. Installed `scikit-learn`
To resolve:
```python
from sklearn.metrics.pairwise import ...
```
Ran:
```bash
pip install scikit-learn
```

---

### 3. Fix Missing `nn` in `bert_extend.py`
**File:** `bert_extend.py`  
**Added near the top:**
```python
import torch.nn as nn
```

---

### 4. Fix Missing `BertEncoder`
**File:** `bert_extend.py`  
**Added near the top:**
```python
from transformers.models.bert.modeling_bert import BertEncoder
```

---

### 5. Fix Missing `BertEmbeddings`
**File:** `bert_extend.py`  
**Explicitly added:**
```python
from transformers.models.bert.modeling_bert import BertEmbeddings
```

---

### 6. Fix Encoding Error When Reading File
**File:** `test_amrsim.py`  
**Changed from:**
```python
with open(path) as f:
```
**To:**
```python
with open(path, encoding='utf-8') as f:
```

---

### 7. Fix Missing `apply_chunking_to_forward`
**File:** `bert_extend.py`  
**Added near the top:**
```python
from transformers.modeling_utils import apply_chunking_to_forward
```

---

## 🧾 Tip
Consider saving this as `CHANGES.md` or committing these changes with meaningful Git messages like:
```bash
git commit -am "Fix: replace cached_download with hf_hub_download"
```