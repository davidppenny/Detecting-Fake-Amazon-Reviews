# 00_Amazon_Reviews_Analysis

<b>Problem Statement:<b>
- With amazon nearing ½ billion products, users turn to reviews to inform their purchase decisions. The question is how helpful is each review?

<b>Understanding the Problem<b>
- Yelp has an algorithm that classifies reviews as “recommended” or “not-recommended” and is very effective at maintaining an honest review of each establishment.
- Amazon removes reviews it deems unauthentic or that violate its Terms of Use. However many “unhelpful” reviews seem to remain. Sellers can also be maliciously attacked when competitors order blatently obvious reviews for another seller, forcing Amazon to automatically shut the seller down.

<b>What is an Unhelpful Review?<b>

Unhelpful reviews can be any combination of the following:
- Too Short.
- Too Long.
- Too complicated to read.
- Too simplistic.
- Overly negative
- Overly positive
- Containing toxic or otherwise strong negative sentiment.
- Falsified or dishonest.
- Incentivised
    
<b>Levels of Analysis<b>
    
While there are many avenues to tackle this problem and different levels of analysis possible. This project will only focus on the first level and if more time exists, pursue the second level.
    
Level 1: Feature Engineering
- Engineer features seen in Table 1 below. Train and test a variety of models to attempt to reach the highest accuracy.
    
Level 2: User Behavior & Product Trust
- www.ReviewMeta.com does this exceptionally well. They scrape each product, its reviews and the metadata from each of the users profile pages, and then determine the following:
    
    - Check for deleted reviews  (Has the product lost reviews over time?)
    - Reviewer ease (Does the reviewer always give '5-star' reviews?)
    - Rating trend (How has the review rating changed over time?)
    - Unverified purchases (Is the customer verified for purchasing the product?)
    - Word count comparison (How do the word counts compare review to review?)
    - Phrase repetition (Are the reviews similar in any way?)
    - Suspicious reviewers (one-hit wonders, never-verified reviewers, single-day reviewers)
    - Overlapping review history (Has the same customer reviewed the same product?)
    - Brand repeats (Do the same customers review all the same products?)
    
This creates a exceptionally powerful understanding of not just the trustworthiness of the review, but the trustworthiness of the reviewer.
    
<b>Goal<b>

- Engineer the correct features in the correct combination to attain the highest possible accuracy at labeling reviews as 'falsified'.
    
<b>Feature Engineering:<b>

Features to Add | Description | Example
------------- | ------------- | -------------
falsified | The label indicating if the review was falsified or not | 1
rating | The star rating the customer rated the product from 1-5 | 3
verified_purchase | Returns wether or not the customer purchased the product. | 1
sentiment | Returns the overall sentiment of the review. | 0
num_words_in_text | Returns the total number of words in the text | 23
num_stopwords| Returns the total number of stop words. | 12
num_words_in_text_no_stop | Returns the total number of words in the text not counting stop words. | 9
num_unique_words | Returns the number of unique words in the text. | 17
mean_word_len| Returns the average word length in the text. | 4
num_chars| Returns the total number of characters. | 251
num_punctuations| Returns the total number of punctuations. | 4
num_scentences_in_text | Returns the total number of scenctences in the text using textstat library. | 5
flesch_ease| Returns the Flesch Reading Ease Score. | 98.11
flesch_kincaid_grade | Returns the Flesch-Kincaid Grade of the given text. This is a grade formula in that a score of 9.3 means that a ninth grader would be able to read the document. | 9.3
automated_readability_index | Returns the ARI (Automated Readability Index) which outputs a number that approximates the grade level needed to comprehend the text. | 6.5
overall_readability_index| Based upon all the above tests, returns the estimated school grade level required to understand the text. | 8.0
total_sentiment | TBD | TBD
toxic_comment_count | TBD | TBD

<b><center>Table 1: Enginered Features from review_text Column</center><b>

#### Personal Notes

Boost Accuracy By:
- Creating feature total_sentiment_analysis by analyzing the sentiment contained in each scentence - NLP on each scentence and using recurrent neural tensor networks (RNTNs) to determine each scentence sentiment.
- Creating feature toxic_comments_count (toxic+severe_toxic+obscene+threat+insult+identity_hate) - Kaggle Challenge
- <mark>Word embeddings <mark>

Consider:
- Scaling data
- KNN, Decision Trees, Support Vector Machines
- PCA
- Model Evaluation
- HyperParameter Optimization for each
- K-Means, GMM, t-SNE clustering
- Neural Networks - recurrent neural tensor networks (RNTNs)
   
    
<b>Packages, programs and libraries Required<b>
- Sklearn
- textstat
- [Stanford CoreNLP](https://stanfordnlp.github.io/CoreNLP/index.html)
- Java's JDK
    
<b>Ackowledgements<b>
- Dataset sourced from github repository: [Deception-Detection-on-Amazon-reviews-dataset](https://github.com/aayush210789/Deception-Detection-on-Amazon-reviews-dataset)
- Yao, Yao; Angelov, Ivelin; Rasmus-Vorrath, Jack; Lee, Mooyoung; and Engels, Daniel W. (2018) "Yelp’s Review Filtering Algorithm,"
SMU Data Science Review: Vol. 1 : No. 3 , Article 3.
Available at: https://scholar.smu.edu/datasciencereview/vol1/iss3/3
- Hossain, Md Forhad, "Fake Review Detection using Data Mining" (2019). MSU Graduate Theses. 3423.
https://bearworks.missouristate.edu/theses/3423