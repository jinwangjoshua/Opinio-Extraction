# Opinio-Extraction

## 0.Explanation for all the files in this repo.

- reviews folder: folder contains all original reviews data of nine products.
- results folder: folders contain all clustered data and visualization data for each model.
  - word2vec folder: visualizations and cluster opinions results using word2vec
  - glove folder: visualizations and cluster opinions results using glove
  - accuracies.csv: accuracy for each opinions results, how to get the accuracy numbers
- phrases.csv: the opinions after preprocessing and opinion extraction.
- work_proflio.ipynb: the work flow and explanation for all the work. I confirm this jupyter notebook is runable. The preprocessing part will cost **mins.** and the semantic clustering partr will cost around 30 hours.(Intel i7, 16GB memory, Ubuntu 16.04). For the semantic distance calculating part, the total running time for all the products for all the models are over 30 hours. So in this profolio, we make a presentation of one product.
- wordcloud.png: sample wordcloud visualization for the product in the proflio(product_5 and bword2vec)

## 1. Introduction of this Opinion Extraction Work
It is important for e-commerce shoppers to know the opinions and feedbacks from the customers. In this paper, we developed a product reviews opinion extraction system, which extracts, cluster and visualize opinions from the reviews text.  In the opinion extraction part, regular expression based on POS rules are utilized. Two word embedding, a new semantic similarity distance, and a clustering algorithm are utilized in the second part, semantic grouping part. After carefully test,  accuracies of semantic relevance were obtained for word2vec and glove models. 

## 2. Codes and paper Citations 
Codes/paper citations, and detailed codes explanation are in the work_proflio.ipynb jupyter notebook.
### 2.1 Data Cleaning
### 2.2 Opinion Extraction
This step is very important for the whole work. The purpose of this work is to obtain a text mining model which can automatically get opinions from reviews and group them, so that manual work can be reduced when investigating reviews’ opinions. In this paper, we used the method introducing in [1,2,3], that is setting rules of combinations of POS(part of speech) for the tokenizations to extract opinions.  For example, after the POS combinations extraction, we can grab opinions like this:(ADJ NOUN CCONJ NOUN --- great packing and speed, ADV ADV NOUN --- very hot temperature, NOUN VERB ADJ--- color is terrible). 

After improving the method in [3, 4], also because the reviews’ grammar and syntax are very informal in this problem, we made 45 rules to extract the opinions, and a sample of them are list below in Table 1. 
Table 1: Example of POS combinations

| Rules of POS Combinations | Examples |
|---|---|
| NOUN VERB ADJ | tank look large |
| ADJ NOUN | cheap material |
| ADJ CCONJ ADJ NOUN | quick and easy brew |
| VERB ADJ | work great |
| VERB ADJ NOUN | make fancy coffee |
| VERN ADJ ADJ | is cheap plastic |
| VERB ADV ADJ NOUN | generate so much trash |
| ... | ... |

## 3. Modeling and Experiment Structure
### 3.1Experiment Structure
The next step for this project is to group the extracted phrases(opinions) by semantic distance. 
The first is to apply word embedding to generator word vectors and calculate the semantic distance Word Mover's Distance based on the word embeddings. Then clustering models based on the semantic distance matrix will be used to group the phrases and finally, the result will be evaluated. The environment used here is Ubuntu 16.04.5, Python 3.6.6, Spacy 2.0.16[5], Gensim 3.5.0[6] and Sklearn0.20.0[7].
### 3.2 Word Embedding, Semantic Similarity and Clustering Model
As mentioned above, we will try both word2vec and glove pre-trained embedding here, versions are respectively GoogleNews-vectors-negative300[8] and glove.840B.300d[9]. For the semantic distance, as mentioned in Chapter 2, we will use Word Mover’s Distance to evaluate the semantic similarities between phrases, which better describe semantic similarity.

Based on the semantic similarity matrix, which is composed of similarities between every pair of phrases. We will introduce K-means clustering algorithms clustering[10].
### 3.3 Evaluation Sturcture
In the evaluation part, we will test accuracy of clustered results. There are totally nine group of products, for each group of dataset, there will be 100 clustered totally and the accuracy is how many are semantically relevant with the product. Both glove and word2vec embeddings will be test and hypothesis test will be implemented to check if there is any difference between two models. 


## 4. Results Evaluation and Conclusion supported by data
After performing evaluations on the KMeans clustering model on both word2vec and glove embeddings, the table shows the semantic accuracies reviews opinions clusters from nine products. And we can find finally the model got an averaged accuracies are % for word2vec and % for glove embedding. Now we  need to check if the two models have some difference. 

Total there will be nine pairs of data point, after power analysis, when the effect size is 1.41, and significance level of 0.05, we can be 80% claim our experiments are reliable. 

The null hypothesis is that there is no difference between accuracies between the two methods, while the alternative hypothesis is there is some difference. Statics of paired sample t test will be utilized here. After assumption check and hypothesis test, we got the p-value of 0.936, which is much larger than 0.05, the significance level, so that we do not reject null hypothesis and conclude that there is no significant difference between the accuracies between clustering models based on word2vec and glove embeddings.

|  Product_id |  accuracy(word2vec) |  accuracy(glove) | difference  | 
|---|---|---|---|
| 0 | 0.92 | 0.91 | 0.01 |
| 1 | 0.91 | 0.91 | 0.01 |
| 2 | 0.87 | 0.90 | -0.04 |
| 3 | 0.85 | 0.87 | -0.02 |
| 4 | 0.90 | 0.88 | 0.02 |
| 5 | 0.89 | 0.91 | -0.02 |
| 6 | 0.80 | 0.87 | -0.07 |
| 7 | 0.91 | 0.86 | 0.05 |
| 8 | 0.91 | 0.86 | 0.05 |

## 5. Visualization
![](https://github.com/jinwangjoshua/Opinio-Extraction/blob/master/results/word2vec/product_5_wordcloud.png)

## 6. Time Allocation and why this is a semester's work(300 hours totally)
- Paper Reading and Research Plan Making: 100 Hour
- Data Scraping and Data Preprocessing:100 Hour
- Model Applying: 50 Hour
- Results Analysis and Paper Writing: 50 Hour


## Citations:
[1]Hu, M. and Liu, B., 2004, August. Mining and summarizing customer reviews. In Proceedings of the tenth ACM SIGKDD international conference on Knowledge discovery and data mining (pp. 168-177). ACM.
[2]Samha, A.K., Li, Y. and Zhang, J., 2014. Aspect-based opinion extraction from customer reviews. arXiv preprint arXiv:1404.1982.
[3]Hu, M. and Liu, B., 2004, July. Mining opinion features in customer reviews. In AAAI (Vol. 4, No. 4, pp. 755-760).
[4]Lei Zhang, Riddhiman Ghosh, Mohamed Dekhil, Meichun Hsu, Bing Liu. "Combining Lexicon-based and Learning-based Methods for Twitter Sentiment Analysis".  Technical Report, HP Labs.
[5]https://spacy.io/
[6]Radim Reh˚u ˇ ˇrek and Petr Sojka. Software Framework for Topic Modelling with Large Corpora. In
Proceedings of the LREC 2010 Workshop on New Challenges for NLP Frameworks, pages 45–50, Valletta, Malta, May 2010. ELRA. http://is.muni.cz/publication/884893/en.
[7]Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., Blondel, M., Prettenhofer, P., Weiss, R., Dubourg, V. and Vanderplas, J., 2011. Scikit-learn: Machine learning in Python. Journal of machine learning research, 12(Oct), pp.2825-2830.
[8]The word2vec data used were from GoogleNews-vectors-negative300.bin.gz which can be downloaded from https://code.google.com/archive/p/word2vec/
[9]Sutskever, I., Vinyals, O. and Le, Q.V., 2014. Sequence to sequence learning with neural networks. In Advances in neural information processing systems (pp. 3104-3112).
[10]MacQueen, J., 1967, June. Some methods for classification and analysis of multivariate observations. In Proceedings of the fifth Berkeley symposium on mathematical statistics and probability (Vol. 1, No. 14, pp. 281-297).

## Environment:
 - Linux 16.04
- Python 3.6
- Jupyter Notebook


