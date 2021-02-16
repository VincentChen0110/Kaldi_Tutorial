# Kaldi Tutorial 

###### tags: `kaldi`

This notebook is to record the basic procedures of being a kaldi user. 
Thchs30 is a small database suitable for chinese recognition tutorial.
RM and WSJ is suitable for english recognition tutorial.

## :memo: Kaldi Outline
To run the recipes provided.
### Clone the kaldi repository from github
```linux
git clone https://github.com/kaldi-asr/kaldi.git
```

### Select speech corpus and recipe to train

In this notebook, I will be using aishell corpus and recipe to train on. <br />
**Edit run.sh in s5 to change datapath and check running stages**
```linux
##change data path for the corpus to be downloaded to.
data = /kaldi/egs/aishell/s5
##data url for the corpus to be downloaded
data_url = www.openslr.org/resources/33
```
The **download_and_untar.sh** will download and unzip the corpus and the data is ready for preprocessing.

### Observe the execution program
The main execution shell script file in the recipe is **run.sh** <br />
There may be quite a lot of bugs while executing the program. Hence, I recommend to split the program into different stages.
* Download and Preprocess Stage
* MFCC and Build Dictionary Stage
* Neural Network Training(TDNN) Stage

> In `cmd.sh` change **queue** command to **run**

Still, there might be a few bugs, but most of them should be about data path being incorrect. 

## :memo: Speech Recognition Outline

### Speech Corpus Composition
Speech Corpus contains four essential files as follows:
* **wave.scp** : The recording ID and its corresponding data path.
* **text** : The recording ID and its corresponding speech text 
* **utt2pk** : The recording ID and its corresponding speaker ID
* **spk2utt** : The speaker ID and all of its corresponding recording IDs

### Kaldi Language Preparation
The Kaldi recipe will preprocess the corpus into the data types that we need, which is stored in ```data/dict``` . For example, the wsj recipe is at ```local/wsj_prepare_dict.sh```.
The needed dictionaries are as follows:
* **lexicon.txt** : word and its phone composition
* **lexiconp.txt** : word pronounciation probability and its phone.
* **silence_phones.txt**
* **nonsilence_phones.txt**
* **optional_silence.txt**
* **extra_questions.txt**

Then,the recipe to continue preprocessing is located at ```utils/prepare_lang.sh```. The processed data are stored in ```data/lang```. The data in lang are processed so that they are able to be handled by FST, should be as follows:
* **phones.txt**: Converting phones to numerical values
* **words.txt**: Converting vocabulary to numerical values
* **oov.txt**: Out of vocabulary
* **topo, L.fst, phones/**
### Feature Extraction
Kaldi will perform feature extraction using MFCC and Fbank, it will extract 39 or 40 dimensions of features according to the recipe. Then, normalized using CMVN. MFCC is suitable to train with Gaussian Mixture Modesl, while FBANK acquire more advantages in Deep Neural Network. 

The two features are extracted using command:```compute-mfcc-feats```,```compute-fbank-feats ```.The features are stored in ```data/mfcc/train``` and ```data/fbank/train```. The file types are archives and scripts.
 
The Kaldi recipe procedure is as follows:
* **Pre-emphasis**: 
To expose the information from the high frequency domain, the following equation is performed on the time domain.
$$
x'[t] = x[t]-ax[t-1]
$$
* **Windowing**: To extract features, we take out 10ms of speech, and then add move 10ms to the take frame (Rectangular Window). This may cause Spectral Leakage. Hence, there are other windows like _Hamming Window_ or _Hanning Window_. The equation as follows is implied.
$$
x'[n] = w[n]x[n]
$$
* **Discrete Fourier Transform**:
* **FBANK**:
* **MFCC**:
