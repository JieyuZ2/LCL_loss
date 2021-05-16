# Label-aware Contrastive Loss

This repo contains the pytorch implementation of Label-aware Contrastive Loss (LCL). 
## Dataset preprocess

Download datasets from the given data source links, [Empathetic Dialogue](https://github.com/facebookresearch/EmpatheticDialogues.git), [GoEmotions](https://github.com/google-research/google-research/tree/master/goemotions), [ISEAR](https://www.unige.ch/cisa/research/materials-and-online-research/research-material/), [EmoInt](https://saifmohammad.com/WebPages/EmotionIntensity-SharedTask.html) [SST-2,SST-5](https://nlp.stanford.edu/sentiment/index.html)

```
python data_preprocess.py -d <dataset name> --aug ## for emotion datasets
python sst_data_preprocess.py -d <dataset name> --aug ## for sentiment datasets
```

## Training the model
Set the parameters in config.py
```
python train.py
```

## Credits

We took help from the following open source projects and we acknowledge their contributions.
1. Supervised Contrastive Loss <https://github.com/HobbitLong/SupContrast>
2. SST-tree2tabular <https://github.com/prrao87/fine-grained-sentiment/blob/master/data/sst/tree2tabular.py>
3. Tweet preprocess <https://github.com/cbaziotis/ntua-slp-semeval2018.git>
4. Tweet preprocess <https://github.com/abdulfatir/twitter-sentiment-analysis.git>