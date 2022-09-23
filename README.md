# Sentiment-Analysis

This project is about gathetring and analyzing the public sentiment from twitter about a brand, product or a topic, then provides a genral report by classifying tweets as Positive, Negative or Neutral based on usage of keywords and hashtags.

Two methods are used for this analysis:

1. **RoBERTa model by "Meta"**: *"A robustly optimized method for pretraining natural language processing (NLP) systems that improves on Bidirectional Encoder Representations from Transformers, or BERT, the self-supervised method released by Google in 2018. BERT is a revolutionary technique that achieved state-of-the-art results on a range of NLP tasks while relying on unannotated text drawn from the web, as opposed to a language corpus that’s been labeled specifically for a given task. The technique has since become popular both as an NLP research baseline and as a final task architecture. BERT also highlights the collaborative nature of AI research — thanks to Google’s open release, we were able to conduct a replication study of BERT, revealing opportunities to improve its performance. Our optimized method, RoBERTa, produces state-of-the-art results on the widely used NLP benchmark, General Language Understanding Evaluation (GLUE)."*
(click [here](https://ai.facebook.com/blog/roberta-an-optimized-method-for-pretraining-self-supervised-nlp-systems/) to read more about RoBERTa)

2. **Textblob library**: *"TextBlob is a Python (2 and 3) library for processing textual data. It provides a simple API for diving into common natural language processing (NLP) tasks such as part-of-speech tagging, noun phrase extraction, sentiment analysis, classification, translation, and more."*
(click [here](https://textblob.readthedocs.io/en/dev/) to read more about Textblob)

# The pipeline goes like this

1. first it collects data(posts) using the API methods of tweepy
2. Collected data is cleaned by removing unnecessary taggings using Regular Expressions
* **RoBERTa Model:**
3. The pretrained RoBERTa model analyze the posts, and produce vectors as per their as per their sentiment.
4. The vector scores are polarity score. The sentiments of posts are polarized in three categories,
      * ***Positive***
      * ***Negative***
      * ***Neutral***

Weightage of sentiment in individual polarities are assigned and a general polarity score is produced ranging from -1 to +1.
   
**Eg** 
|  |Tweet 	|  Neg    |	Neu     |	Pos     |	Polarity | 	Opinion|
|--|--------|---------|---------|---------|----------|---------|
|0 | Tweet 1| 0.219717| 0.735197|	0.045086| -0.174631| Neutral |
|1 | Tweet 2| 0.209507| 0.749692| 0.040801|	-0.168707| Neutral |

5. Now a graph is plotted: ***Polarity*** vs ***Weightage of each of three poles of opinion***
6. Another bar graph is plotted where bars are the poles ***Positive***, ***Negative***, ***Neutral***. Their height indicates the average score of that pole.


* **Textblob Library**
3. The subjectivity and polarity of the tweets are measured by the *textblob.sentiment* module.
4. A scattered graph is plotted, ***subjectivity*** vs ***polarity***
