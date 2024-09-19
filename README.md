# _autrainer_ Seminar Follow-Up

This repository is a follow-up to the [_autrainer_](https://github.com/autrainer/autrainer) seminar,
slightly modified with an extended training time of 20 epochs (instead of 5).
It includes the implementation from our hands-on coding session.

## Custom Dataset

The [ESC-50](https://github.com/karolpiczak/ESC-50) dataset for Environmental Sound Classification is implemented in `esc50.py`.

Configurations for both log-Mel spectrograms (`conf/dataset/ESC50-32k.yaml`)
and MFCCs (`conf/dataset/ESC50-MFCC-32k.yaml`) are provided (32 kHz sampling rate).

## Custom Model

The simple CRNN model implemented in `crnn.py` is implemented in `crnn.py`.
A configuration for the model is provided in `conf/model/crnn.yaml`.

## Custom Transform

A [MFCC](https://pytorch.org/audio/2.4.0/generated/torchaudio.transforms.MFCC.html#torchaudio.transforms.MFCC)
feature extraction transform is implemented in `mfcc.py`.
A preprocessing pipeline configuration for MFCCs is provided in `conf/preprocessing/mfcc_32k.yaml`.

## Results

The model was trained for 20 epochs (with early stopping),
using a batch size of 32, the Adam optimizer, and a learning rate of 0.001.
The table below shows the results for both log-Mel and MFCC features:

| Model | Features | Val. Accuracy | Test Accuracy | Test Loss |
| ----- | -------- | ------------- | ------------- | --------- |
| CRNN  | Log-Mel  | 51.00%        | **49.75%**    | 1.7792    |
| CRNN  | MFCC     | 50.00%        | 45.00%        | 2.2056    |

## Reproduction

To reproduce these results, follow the steps below after installing autrainer.
Detailed installation instructions are available [here](https://autrainer.github.io/autrainer/).

1. Fetch (download) the ESC-50 dataset:

```bash
autrainer fetch
```

2. Preprocess the log-Mel spectrograms and MFCCs:

```bash
autrainer preprocess
```

3. Train the CRNN model on both log-Mel spectrograms and MFCCs:

```bash
autrainer train
```

4. Summarize the results:

```bash
autrainer postprocess results default
```
