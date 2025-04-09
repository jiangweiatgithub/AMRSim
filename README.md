# AMRSim

This repository contains the code for our ACL-2023
paper: [Evaluate AMR Graph Similarity via Self-supervised Learning](https://aclanthology.org/2023.acl-long.892/).
AMRSim collects silver AMR graphs and utilizes self-supervised learning methods to evaluate the similarity of AMR
graphs. 
AMRSim calculates the cosine of contextualized token embeddings, making it alignment-free.

## Requirements

Run the following script to install the dependencies:

```
pip install -r requirements.txt
```
Install [amr-utils](https://github.com/ablodge/amr-utils):
```
git clone https://github.com//ablodge/amr-utils
pip install penman
pip install ./amr-utils
```

## Computing AMR Similarity

### Preprocess

Linearize AMR graphs and calculate the relative distance of nodes from the root:

```
cd preprocess
python amr2json.py -src <amr_file> -tgt <amr_file>
or
python amr2json.py
(for default values)
```

### Returning Similarity with pre-trained model

Download the model from [Google drive](https://drive.google.com/file/d/1klTrvv3hpIPxaCoMbRI7IJDme-Vq3UPS/view?usp=share_link) and
unzip the files and subfolders of the model into this directory (/sentence-transformers/output/ct-wiki-bert). It will look something like below screenshot on Windows:
![image](https://github.com/user-attachments/assets/8043d690-4315-415c-9b16-06d12c5d0a4d)

```
cd sentence-transformers
python test_amrsim.py
```

### Training a Similarity model from scratch
Following data preparation in AMR-DA (Shou et al., 2022), AMRSim utilized SPRING (Bevilacqua et al., 2021) to parse [one-million sentences](https://huggingface.co/datasets/princeton-nlp/datasets-for-simcse/tree/main) randomly sampled from English Wikipedia2 to AMR graphs. 

Generated Wiki AMR graphs were preprocessed and can be download from the [Google drive](https://drive.google.com/file/d/1VAuqLi0LsaCCbII_s2dPa9eDARicw18G/view?usp=sharing).
For training, run:
```
python train_stsb_ct_amr.py
```

## Citation

```
@inproceedings{shou-lin-2023-evaluate,
    title = "Evaluate {AMR} Graph Similarity via Self-supervised Learning",
    author = "Shou, Ziyi  and
      Lin, Fangzhen",
    booktitle = "Proceedings of the 61st Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)",
    month = jul,
    year = "2023",
    address = "Toronto, Canada",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2023.acl-long.892",
    pages = "16112--16123",
}
```


## Acknowledgments
This project uses code from the following open source projects:
- [AMR-DA](https://github.com/zzshou/amr-data-augmentation)
- [FactGraph](https://github.com/amazon-science/fact-graph)
- [Sentence-Transformers](https://www.sbert.net)

Thank you to the contributors of these projects for their valuable contributions to the open source community.

