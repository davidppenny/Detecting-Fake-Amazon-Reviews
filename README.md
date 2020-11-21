# Detecting Falsified Reviews

<b>Problem Statement:<b>
- Users turn to reviews to inform their purchase decisions. However, is each review authentic? If you have spent any time on the internet these days, you may know by now that not everything is true. In fact, according to [Greg Sterling in an article for Marketing Land](https://marketingland.com/study-finds-61-percent-of-electronics-reviews-on-amazon-are-fake-254055#:~:text=Study%20finds%2061%20percent%20of%20electronics%20reviews%20on%20Amazon%20are%20'fake',-The%20problem%20appears), <b>up to 61% of reviews on Amazon are fake!<b>
    
<b>Questions:<b>
- Are there inescapable trends (features) within how we write that betray our intentions?
- Can we (and with what accuracy) exploit these trends using various Machine Learning Techniques?
    
<b>Project Goal<b>

- Goal 1: Using various machine learning and NLP techniques I will attempt to determine to what extent which of the features below could assist with determining if a review is falsified.
- Goal 2: Determine the combination of features below that results in the highest level of accuracy of detecting falsified reviews.
    
<b>Feature Engineering:<b>

   Feature    | Description   | Sample Data
------------- | ------------- | -------------
rating | The star rating the customer rated the product from 1-5 | 3
verified_purchase | Returns whether or not the customer purchased the product. | 1
sentiment | Returns the overall sentiment of the review. | 0
num_words_in_text | Returns the total number of words in the text | 23
num_stopwords| Returns the total number of stop words. | 12
num_words_in_text_no_stop | Returns the total number of words in the text not counting stop words. | 9
num_unique_words | Returns the number of unique words in the text. | 17
mean_word_len| Returns the average word length in the text. | 4
num_chars| Returns the total number of characters. | 251
num_punctuations| Returns the total number of punctuations. | 4
num_scentences_in_text | Returns the total number of sentences in the text using TextStat library. | 5
flesch_ease| Returns the Flesch Reading Ease Score. | 98.11
flesch_kincaid_grade | Returns the Flesch-Kincaid Grade of the given text. This is a grading formula in that a score of 9.3 means that a ninth-grader would be able to read the document. | 9.3
automated_readability_index | Returns the ARI (Automated Readability Index) which outputs a number that approximates the grade level needed to comprehend the text. | 6.5
overall_readability_index| Based upon all the above tests, returns the estimated school grade level required to understand the text. | 8.0
total_sentiment | Returns the overall sentiment of a multi-sentence review. | 13
    
## Results:
    
![Feature Importance Image](/data/feature_importance.png?raw=true)
    
From the image above we can determine that reviews having a 'Verified Purchase' label are much less likely to be falsified. This should be unsurprising. However, it doesn't tell us if perhaps the reviewer was paid/compensated to purchase the product and requested to leave a falsified or 'unauthentic' review.

|    Model     |    Accuracy   |   Precision   |     Recall    |    F1-score   | 
|------------- | ------------- | ------------- | ------------- | ------------- |
|<mark><b>Logistic Regression<b><mark>| 82.21% | 82.58%  |    82.53%   |   82.19% |
|KNN | 76.13%   |   76.58%   |   76.29% | 76.09%|
|SVM | 81.92%   |   82.31%    |  81.92% | 81.89% |
|Random Forest Classifier | 81.59%    |  82.60%  |    81.95% | 81.90%
    
Finally, after testing various models, the table above shows that Logistic Regression was returned the best accuracy at predicting falsified reviews.
    
## Next Steps
- Further work is needed to determine if higher or lower values within the engineered features results in higher or lower feature importance. For instance, setting a cut-off point for mean_word_len and classifying everything above it as "larger_mean_word_len" would create a new feature that could be used to detect falsified reviews. It would be interesting to see how this affects feature importance. 

## Additional Information
    
<b>Additional Packages, programs and libraries Required<b>
- [Java's JDK](https://www.oracle.com/java/technologies/javase-downloads.html)
- [Stanford CoreNLP](https://stanfordnlp.github.io/CoreNLP/index.html)
- [TextStat](https://pypi.org/project/textstat/)
    
<b>Notebooks:<b>
| Item |Notebook|  Environment  |    
|------|--------|---------------|
| 1    |01 Amazon Reviews Analysis - Cleanup EDA Modeling | Base Python |
| 2    |02 Amazon Reviews Analysis - NN in TensorFlow | Base Python + Tensorflow |
    
See the following [link](https://docs.anaconda.com/anaconda/user-guide/tasks/tensorflow/) for information on how to install TensorFlow within an environment.
    
<b>Ackowledgements<b>
- Dataset sourced from github repository: [Deception-Detection-on-Amazon-reviews-dataset](https://github.com/aayush210789/Deception-Detection-on-Amazon-reviews-dataset)
- Yao, Yao; Angelov, Ivelin; Rasmus-Vorrath, Jack; Lee, Mooyoung; and Engels, Daniel W. (2018) "Yelp’s Review Filtering Algorithm,"
SMU Data Science Review: Vol. 1 : No. 3 , Article 3.
Available at: https://scholar.smu.edu/datasciencereview/vol1/iss3/3
- Hossain, Md Forhad, "Fake Review Detection using Data Mining" (2019). MSU Graduate Theses. 3423.
Available at: https://bearworks.missouristate.edu/theses/3423

