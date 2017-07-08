# JWE
Joint Embeddings of Chinese Words, Characters, and Fine-grained Subcharacter Components

## Preparation
You need to prepare a training corpus and Chinese subcharacter radicals or components. 
* Training corpus. Download [Chinese Wikipedia Dump] (http://download.wikipedia.com/zhwiki).
Following the instractions on the [blog](https://flystarhe.github.io/2016/08/31/wiki-corpus-zh/), you can extract the content and do some preprocessing.
* Subcharacter radicals and components.  Deploy the scipy codes in ChineseCharCrawler on [Scrapy Cloud](https://scrapinghub.com), you can crawl the resource from [HTTPCN](http://tool.httpcn.com/zi/).

## Model Training
- 'cd JWE/src', compile the code by 'make all'. 
- run './run.sh', you may modify the parameters in file 'run.sh'
- run './jwe' for parameters details
- Input files format:
Corpus 'wiki.txt' contains segmented Chinese words, use UTF-8  encoding
Subcharacters 'comp.txt' contains a list of components which are seperated by blank space, 'char2comp.txt', each line is a Chinese character and its components, e.g.:
'''
侩 亻 人 云
侨 亻 乔
侧 亻 贝 刂
侦 亻 卜 贝
'''

## Model Evaluation

Two Chinese word similarity datasets '240.txt' and '297.txt' and one Chinese analogy dataset 'analogy.txt' in evaluation folder are provided by [Chen et al., IJCAI, 2015](https://github.com/Leonard-Xu/CWE/tree/master/data).
cd 'JWE/src'
- run 'python word_sim.py -a <similarity_file> -e <embed_file>' for word similarity evaluation, where 'similarity_file' is the word similarity file, e.g., '240.txt or 297.txt', 'embed_file' is the trained word embedding file.
- run 'python word_analogy.py -a <analogy_file> -e <embed_file>' or './word_analogy <embed_file> <analogy_file>' for word analogy evaluation.
