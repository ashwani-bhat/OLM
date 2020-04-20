# OLM: Considering Likelihood in NLP Classification Explanations with Occlusion and Language Modeling [[Paper](https://arxiv.org/abs/)]

---

## 🔭&nbsp; Overview

| Path     	               | Description                         	|
|------------------------- |------------------------------	|
| [data/](dataset/)     |  |
| [experiments/](notebooks/) | |
| [notebooks/](notebooks/) | This directory contains the notebooks that we used to produce the results in the paper.|


## ✅&nbsp; Requirements

The code is tested with:

- Python 3.7


## 🚀&nbsp; Installation

### From source
```bash
git clone https://github.com/DFKI-NLP/olm
cd olm
pip install -r requirements.txt
```


## 🔬&nbsp; Experiments

### Datasets

The datasets are part of [GLUE](https://gluebenchmark.com/tasks) and can be downloaded by following the links below.
First, download the [datasets](datasets) and unpack into `data/glue_tasks/<TASK>/`.

| Dataset | Download |
| ------- | :--------: |
| SST-2| [[Link](https://firebasestorage.googleapis.com/v0/b/mtl-sentence-representations.appspot.com/o/data%2FSST-2.zip?alt=media&token=aabc5f6b-e466-44a2-b9b4-cf6337f84ac8)] |
| MNLI | [[Link](https://firebasestorage.googleapis.com/v0/b/mtl-sentence-representations.appspot.com/o/data%2FMNLI.zip?alt=media&token=50329ea1-e339-40e2-809c-10c40afff3ce)] |
| CoLA | [[Link]()] |

### Fine-tune Model

#### SST-2

```bash
cd olm_tasks
./finetune_sst2.sh
```

#### CoLA

```bash
cd olm_tasks
./finetune_cola.sh
```

### Compute Relevances

```bash
PYTHONPATH="./" python experiments/<TASK>.py \
    --data_dir ./data/glue_data/<TASK>/ \
    --model_name_or_path <MODEL NAME OR PATH> \
    --output_dir <OUTPUT DIR> \
    --strategy grad \ # either one of grad, gradxinput, saliency, integratedgrad, unk, resampling, resampling_std, delete
    --do_run \
    --do_relevances \
    --cuda_device 0
```

### Visualize Results


`notebooks/relevance-mnli.ipynb` contains the notebook to visualize occlusion results.

## 📚&nbsp; Citation

If you find the code or dataset patch helpful, please cite the following paper:
```
@inproceedings{harbecke-alt-2020-olm,
    title={Considering Likelihood in NLP Classification Explanations with Occlusion and Language Modeling},
    author={David Harbecke and Christoph Alt},
    year={2020},
    booktitle={Proceedings of ACL SRW},
    url={https://arxiv.org/abs/}
}
```

## 📘&nbsp; License
OLM is released under the under terms of the [MIT License](LICENSE).
