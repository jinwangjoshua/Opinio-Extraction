# Opinio-Extraction

This is the explanation for all the files in this repo.

- reviews folder: folder contains all original reviews data of nine products.
- results folder: folders contain all clustered data and visualization data for each model.
  - word2vec folder: visualizations and cluster opinions results using word2vec
  - glove folder: visualizations and cluster opinions results using glove
  - accuracies.csv: accuracy for each opinions results, how to get the accuracy numbers
- phrases.csv: the opinions after preprocessing and opinion extraction.
- work_proflio.ipynb: the work flow and explanation for all the work. I confirm this jupyter notebook is runable. The preprocessing part will cost **mins.** and the semantic clustering partr will cost around 30 hours.(Intel i7, 16GB memory, Ubuntu 16.04). For the semantic distance calculating part, the total running time for all the products for all the models are over 30 hours. So in this profolio, we make a presentation of one product.
- wordcloud.png: sample wordcloud visualization for the product in the proflio(product_5 and bword2vec)

## 1. Introduction of this Opinion Extraction Work


## 2. Codes and paper Citations 
Codes/paper citations, and detailed codes explanation are in the work_proflio.ipynb jupyter notebook.

## 3. Results Evaluation and Conclusion supported by data
After performing evaluations on the KMeans clustering model on both word2vec and glove embeddings, the table shows the semantic accuracies reviews opinions clusters from nine products. And we can find finally the model got an averaged accuracies are % for word2vec and % for glove embedding. Now we  need to check if the two models have some difference. 

Total there will be nine pairs of data point, after power analysis, when the effect size is 1.4, and significance level of 0.05, we can be 80% claim our experiments are reliable. 

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

## 4. Visualization
![](https://github.com/jinwangjoshua/Opinio-Extraction/blob/master/results/word2vec/product_5_wordcloud.png)

## 5. Time Allocation and why this is a semester's work
