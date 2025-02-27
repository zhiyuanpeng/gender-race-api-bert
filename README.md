# RaceBERT -- A transformer based model to predict race and ethnicty from names

# Installation

```
pip install racebert
```
Using a virtual environment is highly recommended!
You may need to install pytorch as instructed here: https://pytorch.org/get-started/locally/

# Paper
See Here: https://arxiv.org/abs/2112.03807

# Usage
raceBERT predicts race (U.S census race) and ethnicity from names. 

```python
from racebert import RaceBERT

model = RaceBERT()

# To predict race
model.predict_race("Barack Obama")
```

```
>>> {"label": "nh_black", "score": 0.5196923613548279}
```

The race categories are:
| Race                             | Label    |
|----------------------------------|----------|
| Non-hispanic White               | nh_white |
| Hispanic                         | hispanic |
| Non-hispanic Black               | nh_black |
| Asian & Pacific Islander         | api      |
| American Indian & Alaskan Native | aian     |


```python
# Predict ethnicity
model.predict_ethnicty("Arjun Gupta")
```
```
>>> {"label": "Asian,IndianSubContinent", "score": 0.9612812399864197}
```
The ethnicity categories are:

| Ethnicity                             |
|---------------------------------------|
| GreaterEuropean,British               |
| GreaterEuropean,WestEuropean,French   |
| GreaterEuropean,WestEuropean,Italian  |
| GreaterEuropean,WestEuropean,Hispanic |
| GreaterEuropean,Jewish                |
| GreaterEuropean,EastEuropean          |
| Asian,IndianSubContinent              |
| Asian,GreaterEastAsian,Japanese       |
| GreaterAfrican,Muslim                 |
| Asian,GreaterEastAsian,EastAsian      |
| GreaterEuropean,WestEuropean,Nordic   |
| GreaterEuropean,WestEuropean,Germanic |
| GreaterAfrican,Africans               |

## GPU

If you have a GPU, you can speed up the computation by specifying the CUDA device when you instantiate the model. 

```python
from racebert import RaceBERT

model = RaceBERT(device=0)

# predict race in batch
model.predict_race(["Barack Obama", "George Bush"])
```
```
>>>
[
        {"label": "nh_black", "score": 0.5196923613548279},
        {"label": "nh_white", "score": 0.8365859389305115}
]
```

```python
# predict ethnicity in batch
model.predict_ethnicity(["Barack Obama", "George Bush"])
```
# HuggingFace 

Alternatively, you can work with the transformers models hosted on the huggingface hub directly.

- Race Model: https://huggingface.co/pparasurama/raceBERT
- Ethnicity Model: https://huggingface.co/pparasurama/raceBERT-ethnicity

Please refer to the [transformers](https://huggingface.co/transformers/) documentation.