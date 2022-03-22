<h1 align="center">ANLP Final Project: SemEval 2022 Task G <br> - Multilingual News Pair Similarity Identifier - </h1>


<p align="center">by Chung-Fan Tsai (815202), Ruangrin Ldallitsakool (813990), Pier Giorgio Rayme Battisti (815979) <project-description></p>


## Links

- [SemEval 2022 Task G](https://competitions.codalab.org/competitions/33835#learn_the_details-overview)

- [Python Scraper](https://github.com/euagendas/semeval_8_2022_ia_downloader)

## Project Deployment

Other than the scraping part, the whole project can be executed by running the notebooks in the order that are numbered.
  
## Project Walkthrough

The task was provided with a python scraping tool and a csv files of news pair, their links (for scraping), their 1-4 human annotated similarity score (on average) as training and evaluation set. After scraping, the news are stored as html and json files, but since they are too big to upload, if you wish to scrape them, you can use the "Python Scraper" in the link section along with the csv files in the data/ folder to get the original files. 

Once we had the json and html files, we analyze first training files in the notebook starting with '01', explored the data provided and missing. Then in notebooks 02-03, we extracted the first two features in the news titles (title sentence cosine similarity, title named entity similarity). In notebook 04, we extracted the third feature: keyword similarity in the keyword (keyword tags in the meta-data we scrapped from the sites). In notebook 05, we used Google Translate API to translate news content, preprocessed the text in 06, then extracted news content named entity simlarity as the fourth feature in 07, and news content tfidf cosine similarity as the fifth feature in 08. Then we combined the features together in 09.

Once training set is done, we moved on to evaluation set to repeat the same process to extract the features we selected. From data exploration in notebook 10, notebook 11-12 working on title features, 13 on keyword features, 14 on translating, and we reuse notebook 06 for preprocessing, 15-16 on news content features, and notebook 17 on combining feature score and categories to feed into the model.
  
Last, we tried out logistic regression, SVM, and a sequential neural network for tuning and predicting the multiclasses in notebook 18, and due to some findings in 18, we further conducted a binary classification in 19. 

  
## Project Structure 

The folder <code>data/</code> stores the csv files provided by the task, which contains training and evaluation news pairs with links and annotated scores.

<code>Notebooks numbered 01-09</code> contain our work on the training set, from analyzing data, preprocessing,to extracting features.
  
And folder <code>train/</code> contains all the intermediate csv files we produced with notebooks 01-09.
  
<code>Notebooks numbered 10-17</code> contains our work on the evaluation set, from analyzing data, preprocessing, to extracting features.
  
And folder <code>eval/</code> contains all the intermediate csv files we produced with notebook 10-17.
  
Lastly, <code>Notebooks numbered 18-19</code> contain our tuning code and results of our models. And the tuning combinations are stored under the <code>model/</code> folder.
  
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

