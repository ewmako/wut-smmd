# Warsaw University of Technology - Social Media Monitoring Dataset

This repository contains a dataset called **Warsaw University of Technology - Social Media Monitoring Dataset (WUT-SMMD)**. The goal of this dataset is to simulate a real-life scenario of brand monitoring task in the wild. Each data sample is a short text statement from Twitter along with manually labeled relevance label (WUT-SMMD-A) and sentiment label (WUT-SMMD-B).

I have picked 3 telco companies, which will serve as a study for brand monitoring. The idea was to enable building end-to-end brand monitoring system.

Even though this document is in English, the dataset is in Polish.

### WUT-SMMD-A

This part of the dataset consists of 49785 tweets with ground truth relevance label. Relevance will be 1 if data sample is relevant for corresponing company from the perspective of brand monitoring and 0 otherwise. There are 49785 tweets in total here, which I split 80/20 for training and testing.

### WUT-SMMD-B

This part of the dataset consists of a subset of tweets of WUT-SMMD-A dataset, which are relevant from brand monitoring perspective (relevance=1). There are 21979 tweets here with ground truth sentiment label (negative=-1, neutral=0, and positive=1), and again they are split in 80/20 for training and testing.

### How to read the dataset in python

```python
import json
with open("wut-smmd-a/netia/train.json", "rt") as f:
    netia_train = json.loads(f.read())

print(data.keys(), len(data['tweets']), len(data['labels']))
print(data['tweets'][200], data['labels'][200])
```

Which will produce:
```
dict_keys(['tweets', 'labels']) 12000 12000
Z doświadczenia powiem ci że Netia Spot to szmelc. To jest sprzęt budżetowy więc masówka. Ja zainwestowałem w Linksysa Cisco X3000 i teraz jedyny problem jaki mam to jakość połączenia internetowego firmy Netia  Także polecam ci zakup własnego routera. 1.0
```

### The results

The dataset was created and experimented with as a part of my master thesis. I was able to achive `F1=0,7576` on `WUT-SMMD-A` and `F1=0,6887` on `WUT-SMMD-B` using smart preprocessing, FastText embeddings and SVM.
