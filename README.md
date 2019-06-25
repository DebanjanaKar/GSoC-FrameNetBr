# GSoC-FrameNetBr

This repository contains code for evaluating the semantic similarity between a sentence given in source (natural) language and another sentence given in target language using FrameNet open source technology. In this project, we experiment with three languages precisely : English, Deutsche and Portuguese.

#### Pre-requisites :
1. `Linux` system
2. `Anaconda, Python 3.x`

#### Instructions :
1. Create an environment in your local server using the given requirements-gsoc19.txt with the following command :
`conda create --name <env> --file requirements-gsoc19.txt`
2. Activate the environment using :
`conda activate <env>`
3. In that environment, open jupyter notebook to access the given `.ipynb` files in this repo
4. Run the **`xml_parsing.ipynb`** script first.

Since the size of the pretrained embeddings used in the next script **`create_feat_embeddings.ipynb`** are huge, storage of these resources in local machines and running this script can be a problem. Hence it is recommended to skip steps 5 & 6. The outputs of steps 5 & 6 which will be required in the execution of the last script is already provided in the `/resources` folder of this repo.

5. The next script **`create_feat_embeddings.ipynb`**, uses FastText pretrained embeddings to create dictionaries of embeddings for the different features used to evaluate the semantic similarity. For the pretrained embeddings, download the `.bin` files for the required languages from https://fasttext.cc/docs/en/crawl-vectors.html .

6. The above script outputs `.txt` files which stores the out-of-vocabulary(oov) words for each respective language. To compute the embeddings for the oov words in each language,
* Install FastText in your environment folder using : 
```
$ wget https://github.com/facebookresearch/fastText/archive/v0.2.0.zip
$ unzip v0.2.0.zip
$ cd fastText-0.2.0
$ make
```
- For installing and running FastText properly, ensure you have a (g++-4.7.2 or newer)
* Then run the following command using the pretrained embedding you had previously downloaded.
```
$ cat oov_words_en.txt | ./fasttext print-word-vectors cc.en.300.bin >> en_oov.bin
```
This will give a `.bin` file of the oov words.

7. The last script **`similarity.ipynb`** evaluates the semantic similarity on the basis of different features like FrameNet v.1.7 frames, etc. This script is the last script you need to run to produce results and graphical visualisations. The already computed results and visualisations can be found inside the folder `\results`of this repo.




