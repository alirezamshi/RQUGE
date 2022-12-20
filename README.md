RQUGE: Reference-Free Metric for Evaluating Question Generation by Answering the Question
=================

<p align="center">
  <img src="meta.jpeg" width="700"/>
</p>

We propose RQUGE, a **R**eference-free **QU**estion **G**eneration **E**valuation metric that can compute the quality of the candidate question without requiring the access to the reference question. Given the corresponding context and answer span, our metric calculates the acceptability score by applying a general question-answering module, followed by a span scorer. You can find more detail in [the paper](https://arxiv.org/abs/2211.01482)

Contents
---------------

- [Requirements](#requirements)
- [Calculation](#calculation)
- [Citation](#citation)

<a name="requirements"/>  

Requirements
--------------  

You should first install the following packages:
```
transformers
pytorch
sentencepiece
```

Additionally, you need to download the pre-trained model for the span scorer module:
```
wget https://storage.googleapis.com/sfr-qafacteval-research/quip-512-mocha.tar.gz
tar -xzvf quip-512-mocha.tar.gz
rm quip-512-mocha.tar.gz
```

<a name="calculation"/>  

RQUGE Calculation
-------------- 

Here is a sample score computation for the generated question, given the context and answer span:

```
from rquge_score import RQUGE

## qa_model_path can be changed with any pre-trained QA model 
rquge = RQUGE(sp_scorer_path='quip-512-mocha', qa_model_path='allenai/unifiedqa-v2-t5-large-1363200', device='cuda')

context = "The weather is sunny"
pred_question = "how is the weather?"
answer = "sunny"

print(rquge.scorer(context, pred_question, answer))
```

**Note:** the rquge score is between 1 to 5.

<a name="citation"/>  

Citation
-------------

<a name="citations"/>  

If you use this code for your research, please cite the following work:
```
@misc{mohammadshahi2022rquge,
    title={RQUGE: Reference-Free Metric for Evaluating Question Generation by Answering the Question},
    author={Alireza Mohammadshahi and Thomas Scialom and Majid Yazdani and Pouya Yanki and Angela Fan and James Henderson and Marzieh Saeidi},
    year={2022},
    eprint={2211.01482},
    archivePrefix={arXiv},
    primaryClass={cs.CL}
}
```
Have a question not listed here? Open [a GitHub Issue](https://github.com/alirezamshi/RQUGE/issues) or 
send us an [email](alireza.mohammadshahi@idiap.ch).
