# Label-aware Contrastive Loss

This repo contains the pytorch implementation of Label-aware Contrastive Loss (LCL).

## Dataset preprocess

Download datasets from the given data source
links, [Empathetic Dialogue](https://github.com/facebookresearch/EmpatheticDialogues.git)
, [GoEmotions](https://github.com/google-research/google-research/tree/master/goemotions)
, [ISEAR](https://www.unige.ch/cisa/research/materials-and-online-research/research-material/)
, [EmoInt](https://saifmohammad.com/WebPages/EmotionIntensity-SharedTask.html) [SST-2,SST-5](https://nlp.stanford.edu/sentiment/index.html)

For Empathetic Dialogue dataset, an additional extraction of the raw data was done to
get the csv files using ed_data_extract.py which is required for the below
pre-processing

```
python data_preprocess.py -d <dataset name> --aug ## for emotion datasets
python sst_data_preprocess.py -d <dataset name> --aug ## for sentiment datasets
```

## Training the model

Set the parameters in config.py

```
python train.py
```

### Train with label subsets

Change the `label_list` to your designed labels (e.g., ["Anticipating", "Excited",
"Hopeful", "Guilty"].)

For example, to train a subset of label of EmpatheticDialogues, after setting
`label_list`, run

```
python train.py --dataset ed 
```

## Data Subset

Labels for each subset. Use them in `config.py -> label_list` to trian only on a
subset of classes.

_Hint_: the following code snippets are copy-paste ready.

### EmpatheticDialogues

32-classes: `None` (full dataset)

16-classes: `["Afraid", "Angry", "Annoyed", "Anxious", "Confident","Disappointed", "Disgusted", "Excited", "Grateful", "Hopeful", "Impressed", "Lonely", "Proud", "Sad", "Surprised", "Terrified"]`

8-classes: `["Angry", "Afraid", "Ashamed", "Disgusted", "Guilty", "Proud", "Sad", "Surprised"]`

4-easy: `["Angry", "Afraid", "Joyful", "Sad"]`

4-hard-a: `["Anxious", "Apprehensive", "Afraid", "Terrified"]`

4-hard-b: `["Devastated", "Nostalgic", "Sad", "Sentimental"]`

4-hard-c: `["Angry", "Ashamed", "Furious", "Guilty"]`

4-hard-d: `["Anticipating", "Excited", "Hopeful", "Guilty"]`

## Credits

We took help from the following open source projects and we acknowledge their
contributions.

1. Supervised Contrastive Loss <https://github.com/HobbitLong/SupContrast>
2.

SST-tree2tabular <https://github.com/prrao87/fine-grained-sentiment/blob/master/data/sst/tree2tabular.py>

3. Tweet preprocess <https://github.com/cbaziotis/ntua-slp-semeval2018.git>
4. Tweet preprocess <https://github.com/abdulfatir/twitter-sentiment-analysis.git>

**Note:** There is minor typo in Eq 3 in the paper relating to the placement of
weight wi yi (i.e the positive weights which are constant for a given sample). It is
meant to be outside the log and is correctly implemented in the code. The results in
the paper follow the current implementation.