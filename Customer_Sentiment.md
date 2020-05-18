# Customer Sentiment Analysis

## **1. Introduction**

- **Sentiment is the emotion behind customer engagement.** 

- When you monitor sentiment, you try to measure the **tone**, **context**, and **feeling** from customer actions.

- Whether a customer completes a purchase, leaves a review, or mentions your company socially, there is always an **emotional state** connected to their action.

- Customer sentiment can range anywhere from **pleased** or **loving** to **neutral** or **angry**, and no matter where your customers fall on the sentiment spectrum, it’s imperative you understand not only what their emotional state is, but what’s driving it. 


<center><img src="https://raw.githubusercontent.com/Karkerayashish/Machine-Learning/master/Projects/CustomerSentimentAnalysis/sentiment.jpg" width="600px"></center>

<a id = Section2></a>
## **2. Problem Statement**

- **Analyzing customer sentiment** helps give **insight** into how **customers feel** about your brand. 

- The more you listen to how your customers feel about recommending your company, giving you a rating, engaging with you on social channels, and giving you direct feedback, the more love everyone is sure to feel, and the deeper your relationships can be.


<center><img src="https://raw.githubusercontent.com/Karkerayashish/Machine-Learning/master/Projects/CustomerSentimentAnalysis/sentiment2.jpg" width="600px""></center>

**<h4>Business Scenario:</h4>**

- A large electronics company **Green Electric** has been falling behind the competition in terms of providing a good customer service to their customers.

- Their previous marketing campaigns have also been hit or a miss, and they don't know for certain what their customers want.

- They want to **gain deeper audience insight**, **improve** their **customer engagement**, **provide improved customer service** to their customers and also **improve** the **success rate** of their future **marketing campaigns**.

- To achieve this, the management proposed **analyzing** the **sentiment** of different customers for different products.

- But, analyzing customer sentiment can be a **hectic** process if done **manually**, due to the sheer volume of data. So the company wants to **automate** the process of **Sentiment Analysis**. 

- They have assigned their **Data Science team**, the task to automate the Sentiment Analysis of **future reviews**. 

## **3. Data Loading and Dataset Description**

- We are provided with a **customer review** data of different **Electronic products** sold on an E-commerce platform.

- This massive dataset of reviews will help us **build** a **Sentiment Analysis model** capable of classifying future reviews into their respective sentiment.

- The dataset contains information about the **marketplace**, **customers**, **products**, and also contains the review information including the entire **review text** written by the customer.

- Also provided in the dataset is the `star_rating`. It is the **1-5 star rating** of the review.

- Data can be loaded from [here!](https://storage.googleapis.com/retail-analytics-data/reviews_us_Electronics_v1_00.tsv) 

<br> 

| Records | Features |
| :--: | :--:
| 30,93,869 | 15 |

<br> 

| Column | Description |
| :--:| :--: | 
| **marketplace** | 2 letter country code of the marketplace where the review was written. |
| **customer_id** | Random identifier that can be used to aggregate reviews written by a single author. |
| **review_id** | The unique Product ID the review pertains to. |
| **product_id** | Sales for the given department in the given store. |
| **product_parent** | Random identifier that can be used to aggregate reviews for the same product. |
| **product_title** | Title of the product. |
| **product_category** | Broad product category that can be used to group reviews (also used to group the dataset into coherent parts). |
| **star_rating** | The 1-5 star rating of the review. |
| **helpful_votes** | Number of helpful votes. |
| **total_votes** | Number of total votes the review received. |
| **vine** | Review was written as part of the Vine program. |
| **verified_purchase** | The review is on a verified purchase. |
| **review_headline** | The title of the review. |
| **review_body** | The review text. |
| **review_date** | The date the review was written. |


## **4. Cleaning the Reviews**

- Here, we will **clean** the review data by:

  - **Changing** the **case** of each word to **lowercase**.

  - **Fixing** certain words like *i'm to i am*, *he's to he is*, *she's to she is*, etc.

  - **Removing** all the **punctuation marks** from each review.

  - **Removing** any additional white space from each review.

- Then, we will **create** a new column in the dataset `clean_reviews`, that will contain all the cleaned reviews.

## **5. Calculating Polarity and Subjectivity of Reviews**

- **Polarity** is a float value within the range **[-1.0 to 1.0]**.
  
  - Here, **0** indicates **neutral**,
  
  - **+1** indicates a **very positive** sentiment, and
  
  - **-1** represents a **very negative** sentiment.

- **Subjectivity** is a float value within the range **[0.0 to 1.0]**.

  - Here, **0.0** is **very objective**, and
  
  - **1.0** is **very subjective**. 
  
  - **Subjective** sentence **express** some *personal feelings, views, beliefs, opinions, allegations, desires, beliefs, suspicions, and speculations*.

  - **Objective** sentences are **factual**.

- We will use `textblob` library's **TextBlob** class to find the **polarity** and **subjectivity** values for each review.


## **6. Exploratory Data Analysis**

 <h4>We will try to answer the below questions using EDA.</h4>

 **Question 1:** *How are the Polarity values distributed for the Reviews?* 

 **Question 2:** *How are the Reviews distributed into Sentiments based on Polarity?*

 **Question 3:** *What is the Relationship between the Star Ratings and the Polarity of the Reviews?*

 **Question 4:** *Is there a Positive Correlation between the Star Ratings and the Polarity of Reviews?*

 **Question 5:** *Why the Boxplot was showing Positive Polarity for Low Star Rated Reviews?* 
 
 **Question 6:** *Why the Boxplot was showing Negative Polarity for High Star Rated Reviews?*

 **Question 7:** *How are the Subjectivity values distributed for the Reviews?*

 **Question 8:** *What should be the Threshold of Subjectivity for the Reviews?*
 
 **Question 9:** *What are the Most Common Words in Positive Reviews?*

 **Question 10:** *What are the Most Common Words in Neutral Reviews?*

 **Question 11:** *What are the Most Common Words in Negative Reviews?* 
 
 **Question 12:** *What are the Most Common Words used in the Most Reviewed Product?*

 **Question 12:** *What are the Most Common Words used by the Customer having Most Reviews?*

This **concludes** our Exploratory Data Analysis.

## **7. Post Data Processing & Analysis**

- After completing the analysis on the data, we can move on towards fitting our Machine Learning models with our data.

- But, our dataset still contains a lot of **redundant columns** in our data which won't help the model in making predictions.

- Also, we need to **remove samples** having **subjectivity lower than** the *subjectivity threshold* value of **0.3**

- And, we need to create a `sentiment` column containing the **labels** for our machine learning model.

- Our final dataset contains about **72.4% positive** reviews, **20.1% negative** reviews, and **7.6% neutral** reviews.

### **7.4 Data Splitting**

- Now, we will **split** the dataset into **Train** and **Test** subsets.

- We will use **80%** data for **training** and the remaining **20%** data for **testing** our models.

- First, we will **separate** the **reviews** and their respective sentiment **labels** from the data.

*Using scikit-learn's train_test_split function to split the dataset into train and test sets.*
*80% of the data will be in the train set and 20% in the test set, as specified by test_size=0.2*

## **8. Model Development & Evaluation**

- Building a `tokenizer` function that will **split** each review into a **list of tokens**.

- A **token** is a **single word** in this case, and the review will be splitted on a **single white space**.

def tokenizer(text):
    return text.split()

- Building a **TFIDF Vectorizer**.

- In this, first we create a **vocabulary** of **unique tokens** from the entire set of **documents** (i. e. **reviews**).

- Then we construct a **feature vector** from each document that contains the **term frequency** of how often each word occurs in a particular document.

- Term Frequency is the **number of times** a term, **t**, **occurs** in a document, **d**.

- TFIDF stands for **term frequency-inverse document frequency** (tf-idf).

  - It is used to **downweight** the **frequently occurring words** in the feature vectors that typically don't contain useful or discriminatory information.


 - *tf-idf(t, d) = tf(t, d) * idf(t, d)*
   - Here, *tf(t, d)* is the **term frequency**, and
    - *idf(t, d)* is the **inverse document frequency**
<br> 

  - *idf(t, d) = log(nd/ ( 1+ df(d, t))*
    - Here, *nd* is the **total number of documents**, and    
    - *df(d, t)* is the **number of documents**, d, that **contain** the **term t**.

- This will create a matrix of **15000** most common words, based on their term 

tfidf = TfidfVectorizer(max_features=15000, tokenizer=tokenizer)

- Creating a **Machine Learning Pipeline**.

- This will first, **vectorize** the data, creating a **TFIDF feature matrix** from the dataset, then will **pass** this **data** to our **classifier**.

- The classifier in this case is the **Multinomial Naive Bayes** classifier.

- This algorithm is **most suited** for **vectorized text** that contains a *large number of features*.

- Creating a pipeline allows us to **streamline** our Machine Learning workflow by performing **multiple steps** in a single pass.

*tfidf_mnb = Pipeline([('vect', tfidf), ('clf', MultinomialNB())])*

**Model Evaluation**

- Checking the model **accuracy** on both train and test sets.

- We are using the **classifier**'s `score` method, which calculates the **accuracy score** of the model on a given data.

*print('Model Accuracy for the Train set:', tfidf_mnb.score(X_train, y_train))*

*print('Model Accuracy for the Test set:', tfidf_mnb.score(X_test, y_test))*

**Observations:**

- We get an **accuracy** of about **92%** on both of our train set and test set.

- This implies that our model is **not overfitting**.

- It is **generalizing** well on unseen data, and giving good results.

- Creating **confusion matrix** and **classification report** of our predictions.

- Our model is giving **great** results for the **positive** sentiment.
  
  - This might be due to the **large proportion** of *positive reviews* in the dataset.

- The performace for **negative** reviews is also **good** with a **F1 score** of **85%**.

- But, our model **struggles** while predicting the *neutral sentiment*.

  - This is due to the fact the many neutral sentiment reviews contains **words** which can sometimes be **associated** with both *positive and negative reviews*.

  - Also, there are a lot **less** number of **neutral reviews** in the data.

  - And, hence leads to a lot of **false negatives** in the neutral sentiment.

### **8.2 Using Pre-Trained Model**

- We went to all the trouble of **calculating polarity**, **subjectivity** values for our reviews.

- Then we **divided** the **reviews** into **sentiments** based on some conditions.

- After that, we created a **TFIDF feature matrix** and **trained** a machine learning **model** to **predict** the **sentiment** of the reviews.

- It was a very **time consuming** process.

- But, what if we can **skip** all these steps and make **accurate predictions** without wasting any time.

**Enters Transfer Learning**

- **Transfer learning** is the process of **storing knowledge** gained while solving **one problem** and **applying** it to a **different** but **related problem**.

- For example, **knowledge gained** while learning to *recognize cars* could **apply** when trying to *recognize trucks*.

**NaiveBayesAnalyzer**

- `NaiveBayesAnalyzer` of **textblob** library is an **NLTK** classifier trained on a **movie reviews** corpus.

- We just need to **pass** the **review** and it will **predict** the **sentiment** present in it.

- It returns its result as a named tuple of the form: **Sentiment(classification, p_pos, p_neg)**.

*review = 'awesome fits really well & is very sturdy provides excellent protection at a great price'
review_blob = TextBlob(review, analyzer=NaiveBayesAnalyzer())
print(review)
print(review_blob.sentiment)*

- It predicts the **sentiment** of the review to be **positive**, which is correct.

- Creating a helper function which will allow us to make predictions on a large number of reviews.

- It will output **positive** if *p_pos is greater than 0.5*, **negative** if **p_pos is less than 0.5**, and **neutral** if *p_pos is equal to 0.5*

- **NaiveBayesAnalyzer** is **very slow** when compared to scikit-learn's machine learning models.

- Hence, it will take a **large amount of time** to make predictions on the entire dataset.

- So, we will **sample** a **500 reviews** from the evaluation_df, and make predictions on them.

**Model Evaluation**

- We get an **accuracy** of about **70%** on our **500** reviews.

- The pre-trained model is only good at making predictions about the positive sentiments.

- Also, it must have been trained on a data containing only positive and negative sentiments.
  
  - That's why it is unable to make predictions about the neutral sentiment.

**Observations:**

- Here we can compare the predictions made by both the models.

- Our TFIDF and Multinomial Naive Bayes model performs really well for this sentiment analysis task.

- It is **fast** and more **accurate** than the pre-trained model.

- The pre-trained model doesn't give very good results on this dataset.

- But, this shouldn't stop us from using **Transfer Learning** and Pre-trained models.

  - They are heavily used in Deep Learning for **Object Detection**, **Image Classification**, **Language Modelling**, etc.

- We should use our **TFIDF - Multinomial Naive Bayes** model as our final model, for making **future predictions**.

## **9. Conclusion**

- We cleaned the reviews by:
  - **Changing** the **case** of each word to **lowercase**,
  - **Fixing** certain words,
  - **Removing** all the **punctuation marks** from each review, and
  - **Removing** any additional white space from each review.

- Then, we calculate the **polarity** and **subjectivity** values for each review.

- This allowed us to **analyze** our data **in-depth** to find relationship between various features like star rating and polarity.

- We also calculated a **threshold** for the **subjectivity** value in our reviews.

- We then found out the **most common words** associated with different sentiments.

- After analyzing the data:
  - We **remove** all **redundant columns** from the data,

  - **Remove** all the **samples** having **subjectivity less than 0.3** i. e. the subjectivity threshold.

  - **Divide reviews into sentiments** based on star rating and polarity.

  - At last, we **split** the **data** into training and test sets.

- During model building, we first created a **TFIDF matrix** of our data and **trained** a **Multinomial Naive Bayes** model.

  - This model was then used to make **predictions** on the test set.

  - It achieved an **accuracy** of **92%** on both train and test sets.

  - This implied that model is not overfitting and is **generalizing** well on unseen data.

- At last, we used a **pre-trained** model to make sentiment predictions on a **small sample** of our data.
  
  - The pre-trained model was **slower** than the ML model we build, and gave **worse results**.

- So, we **discarded** this model, and used our **TFIDF - Multinomial NB** model as our **final model**.
