# DigitalPeter
Data and description for the Digital Peter dataset.

## Data
* Data [link](https://drive.google.com/file/d/1pl-NVBsjD7lgMYdTx6eFVU1s7rZfeeLY/view?usp=sharing). It consists of images and txt files for cutted text lines.

* Full documents [link](https://drive.google.com/file/d/1CcJpmE0yIJ2IY1PPKyil8ZrOuCfI1Jpv/view?usp=sharing). It consists of images of full documents. You can use it to train models that cut the text lines from initial image.

* Annotations [link](https://drive.google.com/file/d/1XxUMb4_NoNPPKioa4RqDLmSQ0Esu_Fbt/view?usp=sharing). It is annotation for the full documents dataset (previous link). Annotations include segmentation masks for text lines.

Data [link](https://drive.google.com/file/d/1pl-NVBsjD7lgMYdTx6eFVU1s7rZfeeLY/view?usp=sharing) has the following structure.

```
--- images/
--- mapper.csv/
--- words/
```
Images folder contains images of lines. Words folder contains txt files of text corresponding to images. You can map them by file name. For example image ```0_1_0.jpg``` has text translation in file ```0_1_0.txt```.

```mapper.csv``` has five columns - [new_name, old_name, train, public,private]. Data [link](https://drive.google.com/file/d/1pl-NVBsjD7lgMYdTx6eFVU1s7rZfeeLY/view?usp=sharing) has filenames from column "new_name". But for competition "DigitalPeter" (described below) we used different filenames. They are presented in column "old_name". So this file maps new_names to old_names from competition.

FINALLY, if you want to use our dataset for scientific researches, you can forget about "DigitalPeter" competition and don't look at column "old_name" in mapper.csv. Use only actual names from columns "new_name" and columns [train,public,private] for train/val/test splits.


## Description

The dataset consists of 9694 images and text files. There are 265788 symbols and approximately 50998 words.

<p align="center">
  <img src="pics/counts_hor.png" width="80%">
</p>

Each pair consists of one image file and one text file. File names have the format <img src="https://render.githubusercontent.com/render/math?math=x\_ y\_ z.jpg">. Where <img src="https://render.githubusercontent.com/render/math?math=x"> - is a document number, <img src="https://render.githubusercontent.com/render/math?math=y"> - is a page number in the document <img src="https://render.githubusercontent.com/render/math?math=x">, <img src="https://render.githubusercontent.com/render/math?math=z"> - is a line number in the page <img src="https://render.githubusercontent.com/render/math?math=y"> of document <img src="https://render.githubusercontent.com/render/math?math=x">. Such a naming system was created to help researchers who use our dataset to reconstruct original texts. One can train NLP models to help decrease the HTR model error.

Here is an example of one line of text.
<p align="center">
  <img src="pics/one_line.jpg" width="50%">
</p>


Here is an example of segmented document.
<p align="center">
  <img src="pics/line_label.png" width="50%">
</p>

## Train

Keras implementation of CNN-GRU-CTC model is presented in notebook [```baseline.ipynb```].

## Competition
We held a competition based on Digital Peter dataset.
Here is github [link](https://github.com/sberbank-ai/digital_peter_aij2020). Here is competition [page](https://ods.ai/tracks/aij2020) (need to register).

Here is the final leaderboard for this competition. Scores are presented for the private set. Baseline solution presented in this github has the following metric -  9,786	44,222	21,532 (CER,WER,ACC).
<p align="center">
  <img src="pics/leaderboard.png" width="70%">
</p>
