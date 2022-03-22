<h1 align="center">ANLP Final Project: SemEval 2022 Task G <br> - Multilingual News Pair Similarity Identifier - </h1>


<p align="center">by Chung-Fan Tsai (815202), Ruangrin Ldallitsakool (813990), Pier Giorgio Rayme Battisti (815979) <project-description></p>


## Links

- [SemEval 2022 Task G](https://competitions.codalab.org/competitions/33835#learn_the_details-overview)

- [Python Scraper](https://github.com/euagendas/semeval_8_2022_ia_downloader)

## Project Walkthrough

The task was provided with a python scraping tool and a csv files of news pair, their links (for scraping), their 1-4 human annotated similarity score (on average) as training and evaluation set. After scraping, the news are stored as html and json files, but since they are too big to upload, if you wish to scrape them, you can use the "Python Scraper" in the link section along with the csv files in the data/ folder to get the original files. 

Once we had the json and html files, we analyze first training files in the notebook starting with '01', explored the data provided and missing. Then in notebooks 02-03, we extracted the first two features in the news titles (title sentence cosine similarity, title named entity similarity). In notebook 04, we extracted the third feature: keyword similarity in the keyword (keyword tags in the meta-data we scrapped from the sites). In notebook 05, we used Google Translate API to translate news content, preprocessed the text in 06, then extracted news content named entity simlarity as the fourth feature in 07, and news content tfidf cosine similarity as the fifth feature in 08.  Then we combined the features together in 09 and 10, and because the averagge 1-4 news pair simlarity score provided by the human annotators are not perfect 1,2,3,4 scores but instead floating numbers that are the average score of multiple annotators, we made the decsion to round the score into 4 categories (1,2,3,4, 4 categories with 1.6 rounded to 2, 3.3 rounded to 3) in 09 and 7 categories in 10 (1,1.5,2,2.5,3,3.5,4, 7 categories with 1.6 rounded to 1.5, 3.2 rounded to 3) in case we want to see how the number of categories affect our model.

Once training set is done, we moved on to evaluation set to repeat the same process to extract the features we selected. From data exploration in notebook 11, 12-13 working on title features, 14 on keyword features, 15-16 on translating on preprocessing, 17-18 on news content features, and 19-20 on combining feature score and categories to feed into the model.
  
Last, we tried out logistic regression, SVM, and a sequential neural network for tuning and predicting.

  
## Project Structure (Screenshots)

data/ stores the csv files provided by the task, which contains training and evaluation news pairs with links and annotated scores:
![data](/screenshots/provided_csv.png)

Notebook 01-10 contains our work on the training set, from analyzing data, preprocessing, to extracting features:
![train_code](/screenshots/train_code.png)
  
And folder train/ contains all the intermediate csv files we produced with 01-10 notebooks:
![train_csv](/screenshots/train_csv.png)
  
Notebook 11-20 contains our work on the evaluation set, from analyzing data, preprocessing, to extracting features:
![eval_code](/screenshots/eval_code.png)
  
And folder eval/ contains all the intermediate csv files we produced with 01-10 notebooks:
![eval_csv](/screenshots/eval_csv.png)
  
The rest of the notebooks contain our tuning code and model results:
![model_code](/screenshots/model_code.png)
  
The model/ folder contains tuning result and predictions:
![model_csv](/screenshots/model_csv.png)
  
## Project format

Due to the fact that this is a collaborated project that's being run on different OS, some minor formatting may be specific to a member's OS, but overall, at least for the directory format (eg. '/data/....csv'), it mainly complies to Mac OS. 


## Packages and Versions

nltk 3.5
  
googletrans 4.0.0-rc1
  
spacy 2.3.2
  
bs4 4.9.3 (BeautifulSoup)
  
pandas 1.1.5
  
json 2.0.9
  
sklearn 0.24.1
  
sentence_transformers 0.4.1
  
stanza 1.3.0
  
numpy 1.21.4
  
matplotlib 3.3.3
  
tensorflow 2.8.0
  
keras 2.4.3
  
scikeras 0.6.1

