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

## Here is my Conda list result for my Anaconda env:
```
# packages in environment at D:\ProgramData\Anaconda3\envs\amrsim:
#
# Name                    Version                   Build  Channel
aiohappyeyeballs          2.6.1                    pypi_0    pypi
aiohttp                   3.11.16                  pypi_0    pypi
aiosignal                 1.3.2                    pypi_0    pypi
amr-utils                 1.0                      pypi_0    pypi
async-timeout             5.0.1                    pypi_0    pypi
attrs                     25.3.0                   pypi_0    pypi
bzip2                     1.0.8                h2466b09_7    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
ca-certificates           2025.1.31            h56e8100_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
certifi                   2022.12.7                pypi_0    pypi
charset-normalizer        2.1.1                    pypi_0    pypi
click                     8.1.8                    pypi_0    pypi
colorama                  0.4.6                    pypi_0    pypi
filelock                  3.13.1                   pypi_0    pypi
frozenlist                1.5.0                    pypi_0    pypi
fsspec                    2024.6.1                 pypi_0    pypi
huggingface-hub           0.30.2                   pypi_0    pypi
idna                      3.4                      pypi_0    pypi
jinja2                    3.1.4                    pypi_0    pypi
joblib                    1.4.2                    pypi_0    pypi
libexpat                  2.7.0                he0c23c2_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
libffi                    3.4.6                h537db12_1    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
liblzma                   5.8.1                h2466b09_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
libsqlite                 3.49.1               h67fdade_2    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
libzlib                   1.3.1                h2466b09_2    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
markupsafe                2.1.5                    pypi_0    pypi
mpmath                    1.3.0                    pypi_0    pypi
multidict                 6.3.2                    pypi_0    pypi
networkx                  3.2.1                    pypi_0    pypi
nltk                      3.9.1                    pypi_0    pypi
numpy                     2.0.2                    pypi_0    pypi
openssl                   3.4.1                ha4e3fda_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
packaging                 24.2                     pypi_0    pypi
penman                    1.3.1                    pypi_0    pypi
pillow                    11.0.0                   pypi_0    pypi
pip                       25.0.1             pyh8b19718_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
propcache                 0.3.1                    pypi_0    pypi
psutil                    7.0.0                    pypi_0    pypi
pyparsing                 3.2.3                    pypi_0    pypi
python                    3.9.21          h37870fc_1_cpython    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
pyyaml                    6.0.2                    pypi_0    pypi
regex                     2024.11.6                pypi_0    pypi
requests                  2.28.1                   pypi_0    pypi
safetensors               0.5.3                    pypi_0    pypi
scikit-learn              1.6.1                    pypi_0    pypi
scipy                     1.13.1                   pypi_0    pypi
setuptools                78.1.0             pyhff2d567_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
sympy                     1.13.1                   pypi_0    pypi
threadpoolctl             3.6.0                    pypi_0    pypi
tk                        8.6.13               h5226925_1    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
tokenizers                0.21.1                   pypi_0    pypi
torch                     2.6.0+cu126              pypi_0    pypi
torch-geometric           2.6.1                    pypi_0    pypi
torch-scatter             2.1.2                    pypi_0    pypi
torch-sparse              0.6.18                   pypi_0    pypi
torchaudio                2.6.0+cu126              pypi_0    pypi
torchvision               0.21.0+cu126             pypi_0    pypi
tqdm                      4.67.1                   pypi_0    pypi
transformers              4.51.1                   pypi_0    pypi
typing-extensions         4.12.2                   pypi_0    pypi
tzdata                    2025b                h78e105d_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
ucrt                      10.0.22621.0         h57928b3_1    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
unidecode                 1.3.8                    pypi_0    pypi
urllib3                   1.26.13                  pypi_0    pypi
vc                        14.3                h2b53caa_26    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
vc14_runtime              14.42.34438         hfd919c2_26    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
wheel                     0.45.1             pyhd8ed1ab_1    https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
yarl                      1.19.0                   pypi_0    pypi
```
