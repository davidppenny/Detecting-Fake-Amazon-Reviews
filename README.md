# Detecting Falsified Reviews

<b>Problem Statement:<b>
- Users turn to reviews to inform their purchase decisions. However, is each review authentic? If you have spent any time on the internet these days, you may know by now that not everything is true. In fact according to [Greg Sterling in an atricle for Marketing Land](https://marketingland.com/study-finds-61-percent-of-electronics-reviews-on-amazon-are-fake-254055#:~:text=Study%20finds%2061%20percent%20of%20electronics%20reviews%20on%20Amazon%20are%20'fake',-The%20problem%20appears), <b>up to 61% of reviews on Amazon are fake!<b> 
    
<b>Project Goal<b>

- Goal 1: Using various machine learning and NLP techniques I will attempt to determine to what extent which of the following features could assist with determining if a review is falsified.
- Goal 2: Determine the combination of the following features that results in the highest level of accuracy of detecting falsified reviews.
    
<b>Feature Engineering:<b>

   Feature    | Description   | Sample Data
------------- | ------------- | -------------
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
total_sentiment | Returns the overall sentiment of a review. | 13

    
<b>Additional Packages, programs and libraries Required<b>
- textstat
- [Stanford CoreNLP](https://stanfordnlp.github.io/CoreNLP/index.html)
- Java's JDK
    
<b>Notebooks:<b>
| Item |Notebook|  Environment  |    
|------|--------|---------------|
| 1    |01 Amazon Reviews Analysis - Cleanup EDA Modeling | Base |
| 2    |02 Amazon Reviews Analysis - NN in TensorfFlow | Base + Tensorflow |
    
    
<b>Ackowledgements<b>
- Dataset sourced from github repository: [Deception-Detection-on-Amazon-reviews-dataset](https://github.com/aayush210789/Deception-Detection-on-Amazon-reviews-dataset)
- Yao, Yao; Angelov, Ivelin; Rasmus-Vorrath, Jack; Lee, Mooyoung; and Engels, Daniel W. (2018) "Yelp’s Review Filtering Algorithm,"
SMU Data Science Review: Vol. 1 : No. 3 , Article 3.
Available at: https://scholar.smu.edu/datasciencereview/vol1/iss3/3
- Hossain, Md Forhad, "Fake Review Detection using Data Mining" (2019). MSU Graduate Theses. 3423.
https://bearworks.missouristate.edu/theses/3423